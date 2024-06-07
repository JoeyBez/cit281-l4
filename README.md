# Lab 4

Lab 4 was important, with it being the first time a fastify server was put to use. Having to make a simple server with request query to display a name.
```ruby
// Require the Fastify framework and instantiate it
const fastify = require("fastify")();
// Handle GET verb for / route using Fastify
// Note use of "chain" dot notation syntax
fastify.get("/", (request, reply) => {
    reply
        .code(200)
        .header("Content-Type", "text/html; charset=utf-8")
        .send("<h1>Hello from Lab 4!</h1>");
});
fastify.get("/name", (request, reply) => {
    const {first, last} = request.query;
    const name = first && last ? `${first} ${last}` : "Guest"; 
    reply
        .code(200)
        .header("Content-Type", "text/html; charset=utf-8")
        .send(`<h1>Hello, ${name}</h1>`);
});
// Start server and listen to requests using Fastify
const listenIP = "localhost";
const listenPort = 8080;
fastify.listen(listenPort, listenIP, (err, address) => {
  if (err) {
    console.log(err);
    process.exit(1);
  }
  console.log(`Server listening on ${address}`);
});
```
<a href="https://joeybez.github.io/joeybezner.github.io/">Back to Home</a>
