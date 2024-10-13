# Rate Limiting

Rate limiting is a technique used to control the number of requests a client can make within a specified time period. This helps prevent abuse, protect resources, and ensure fair usage.

```javascript
const express = require('express');
const rateLimit = require('express-rate-limit');

const app = express();

// Create rate limit middleware
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // Limit to 100 requests per windowMs
  message: "Many request from this Ip, please try after 15 minutes",
});

// Apply the rate limit middleware to all requests
app.use(limiter);

// Your application routes
app.get('/', (req, res) => {
  res.send('Hello, world!');
});

app.listen(3000, () => {
  console.log('Server listening on port 3000');
});
```



**Explanation:**

* `windowMs`: Specifies the time window in milliseconds. In this example, it's set to 15 minutes.
* `max`: Sets the maximum number of requests allowed within the window. Here, it's limited to 100 requests.
