# Third-party Integration

Node.js, with its modular architecture and rich ecosystem, makes it easy to integrate with various third-party services and APIs. This enables us to extend our applications with additional functionalities and features.

* **Payment Gateways:** Using Stripe services handling payments within the application.

```javascript
const stripe = require("stripe")(process.env.STRIPE_API_KEY);
const { Product, Order, Cart, CartItem } = require("../models/index");
const AppError = require("../utils/appError");

exports.checkoutSession = async function (req, res, next) {
  try {
    const product = await Product.findByPk(req.params.productId);

    const productDetails = await stripe.products.create({
      name: product.name,
      description: `payment for ${product.name}`,
      image: product.image,
    });

    const productPrice = await stripe.prices.create({
      product: productDetails.id,
      unit_amount: product.price * 100,
      currency: "usd",
    });

    const checkoutProduct = await stripe.checkout.sessions.create({
      payment_method_types: ["card"],
      success_url: `${req.protocol}://${req.get("host")}/shopmore/success.html`,
      cancel_url: `${req.protocol}://${req.get(
        "host"
      )}/shopmore/user/cancel.html`,
      customer_email: req.user.email,
      client_reference_id: req.params.id,
      mode: "payment",
      currency: "usd",
      line_items: [{ price: productPrice.id, quantity: req.body.quantity * 1 }],
    });

    res.status(200).json({
      status: "Success",
      checkoutProduct,
    });
  } catch (err) {
    switch (err.type) {
      case "StripeCardError":
        next(new AppError(`${err.message}`, 400));
        break;

      case "StripeRateLimitError":
        next(new AppError(`${err.message}`, 429));
        break;

      case "StripeInvalidRequestError":
        next(new AppError(`${err.message}`, 400));
        break;

      case "StripeAPIError":
        next(new AppError(`${err.message}`, 400));
        break;

      case "StripeConnectionError":
        next(new AppError(`${err.message}`, 402));
        break;

      case "StripeAuthecationError":
        next(new AppError(`${err.message}`, 403));
        break;

      default:
        next(new AppError(`${err.message}`, 400));
        break;
    }
  }
};
```

* **Email Services:** Send emails using providers like Brevo.

```javascript
const nodemailer = require("nodemailer");

module.exports = class Email  {
	   constructor(user, html) {
		this.from = `Shopmore <${process.env.EMAIL_FROM}>`;
		this.to = user.email;
		this.username = user.username;
		this.otp = user.otp;
		this.html = html;
	};

	transporter(){
		return nodemailer.createTransport({
			host: process.env.BREVO_SMPT_HOST,
			port: 587,
			secure: false,
			// family: 6,
			 auth: {
				user: process.env.BREVO_SMPT_USERNAME,
				pass: process.env.BREVO_SMPT_PASSWORD 
			}
		})
	};

	async sendEmail(subject){

		const mailOption = {
			from: this.from,
			to: this.to,
			subject,
			html: this.html,
		};

		await this.transporter().sendMail(mailOption, (err, info) => {
			if(err){
				return console.log('Error', err);
			}
		 console.log('Email sent successfully: ', info.response);

		});
	};

	async welcomeMessage(){
		await this.sendEmail(`Welcome to shopmore ${this.username}`)
	};

	async verifyEmail(){
		await this.sendEmail(`Your security code is ${this.otp}`);
	};

	async sendPasswordReset(){
		await this.sendEmail(`Your security code ${this.otp} password reset`);
	};

	async detectIpAddress(){
		await this.sendEmail('Your account is login on difference device');
	};

};

```



* Location: using ipify to get IP address and Ipstack for getting location.

```javascript
   if (!(user.ipAddress === req.ip)) {
      const ipAddress = await axios.get(`https://api.ipify.org?format=json`);

      const { ip } = ipAddress.data;

      const getLocation = await axios.get(
        `http://api.ipstack.com/${ip}?access_key=${process.env.IPSTACK_API_KEY}`
      );

      const { country_name, region_name, longitude, latitude, city } =
        getLocation.data;

      html = `<h2>Your account was sign in on difference device </h2>
			<p>Account: ${user.email}</p>
			<p>Location: ${country_name}, ${region_name} ${city}</p>
			<p>Time: ${new Date()}</p>
			<p>Latitude: ${latitude}</p>
			<p>Longitude: ${longitude}</p>
			<p>Ip Address: ${ip}</p>
			<p>Best regards</p>
			<p>Shopmore support </p>`;  

      await new Email(user, html).detectIpAddress();
    }
```

