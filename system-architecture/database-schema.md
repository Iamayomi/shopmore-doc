# Database Schema

A database is a structured collection of data that is organized in a way that allows efficient storage, retrieval, and manipulation. It serves as a centralized repository for information, enabling applications to access and manage data effectively. **PostgreSQL** is a high-performance, open-source object-relational database system that is widely used for a variety of applications. It offers a robust feature set, excellent performance, and a strong community.

* Stores data for products, customers, orders, and other entities.
* Relationships between tables are defined using primary and foreign keys.
* Can be accessed using Node.js database drivers or ORMs like Sequelize.

```javascript
const sequelize = require("../config/db");

const User = require("./userModel")(sequelize);
const Store = require("./storeModel")(sequelize);
const Product = require("./productModel")(sequelize);
const Review = require("./reviewModel")(sequelize);
const Cart = require("./cartModel")(sequelize);
const CartItem = require("./cartItemModel")(sequelize);
// const Payment = require("./paymentModel")(sequelize);
const Order = require("./orderModel")(sequelize);
const Category = require("./categoryModel")(sequelize);
const subCategory = require("./subCategoryModel")(sequelize);

// Order.hasMany(Orderitem);
// Orderitem.belongsTo(Order);

// Product.hasOne(Orderitem);
// Orderitem.belongsTo(Payment);

Cart.hasOne(CartItem);
CartItem.belongsTo(Cart);

// CartItem.hasOne(User);
// User.belongsTo(CartItem);

Product.hasMany(CartItem);
CartItem.belongsTo(Product);

Product.hasMany(Review);
Review.belongsTo(Product);

User.hasMany(Review);
Review.belongsTo(Product);

User.hasOne(Cart, { foreignKey: "userId" });
Cart.belongsTo(User, { foreignKey: "userId" });

Store.hasMany(Order);
Order.belongsTo(Store);

User.hasMany(Order);
Order.belongsTo(User);

Category.hasMany(subCategory);
subCategory.belongsTo(Category);

subCategory.hasMany(Product);
Product.belongsTo(subCategory);

// Payment.hasOne(CardPayment);
// CardPayment.belongsTo(Payment);

sequelize
  .sync({ alter: true })
  .then(() => {
    console.log("Models synchronized with the database <<<<<<<<<<<<<>>>>>>>>>");
  })
  .catch((err) => {
    console.error("UNABLE to synchronize with the DATABASE", err);
  });

module.exports = {
  User,
  Cart,
  Review,
  Product,
  Category,
  subCategory,
  Store,
  CartItem,
  Order,
};

```
