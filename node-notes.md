### Node Notes
#### Intro
* nodes.js is an open source (MIT), cross-platform runtime environment for server-side and networking applications
* developed by Ryan Dahl in 2009 aiming to create real-time websites with push capability
    * web applications with real-time, two-way communication WITHOUT applets/flash
    * flash/applets weren't really the open web stack - they were simply using the web as their delivery mechanism, running in sandboxed environments, requiring extra permissions, non-standard ports, etc.
* not a silver bullet new platform that will dominate the web development world -- it's a platform that fills a particular need
    * node is crummy for heavy computation, CPU-intensive operations -- using node for this will void most of its advantages
    * node is for building fast, scalable network applications, capable of handling a huge number of simultaneous connections -- means high scalability
* traditional web server - each request spawns a new thread -- this takes up RAM -- tons of requests means tons of RAM
* node web server - all requests handled by a single thread -- much higher scalability as you are no longer tied to thread overhead/RAM
    * 1M concurrent connections on 16GB server -- http://blog.caustik.com/2012/08/19/node-js-w1m-concurrent-connections/
* node web server - operates on a single thread
* applications are written in javascript
* event-drive architecture and non-blocking IO API - optimizes app throughput and scalability
* commonly used for real-time web applications
* node.js used Google V8 JavaScript engine to execute code
    * V8 is open source (BSD license)
    * V8 is fast
        * compiles js to native machine code prior to execution
        * compiled code is additionally re/optimized dynamically at runtime based on heuristics of the code's execution profile
    * V8 is focused on the web - proficient with internet fundamentals such as HTTP, DNS, TCP
    * JavaScript is a well-known language - accessible to many developers
* Node.js combined with a browser, a document DB (MongoDB, CouchDB) and JSON offers  a unified JavaScript development stack
#### Threading
    * operates on a single thread, using non-blocking IO calls
    * allows node.js to support tens of thousands of concurrent connections w/o incurring cost of thread context-switching
    * upside - highly concurrent applications
    * downside - node.js doesn't allow scaling with number of CPU cores w/o using additional modules such as cluster, StrongLoop Process Manager, pm2
#### Package Management
    * npm - pre-installed package manager for node.js server platform
        * used to install programs from npm registry
        * helps developers build faster by organizing installation and management (similar to maven/apt-get/etc.)
        * similar to ruby gems
    ### Popular Packages
        * underscore - provides utility functions - "JavaScript's functional programming helper library"
            * most depended upon package in Node.js JavaScript runtime
            * The most popular utility library in JavaScript, packaged to be used with Node.js, as well as its two counterparts, which promise better performance by taking a slightly different implementation approach.
        * express - "Fast, unopinionated, minimalist web framework"
            * Express.js, a Sinatra-inspired web development framework for Node.js, and the de-facto standard for the majority of Node.js applications out there today.
        * coffee-script - "Unfancy JavaScript"
            * CoffeeScript compiler that allows developers to write their Node.js programs using Coffee.
        * browserify - bundle your dependencies into a single js file that can be included with a <script> tag
        * connect - Connect is an extensible HTTP server framework for Node.js, providing a collection of high performance “plugins” known as middleware; serves as a base foundation for Express.
        * socket.io and sockjs - Server-side component of the two most common websockets components out there today.
        * Jade - One of the popular templating engines, inspired by HAML, a default in Express.js.
        * mongo and mongojs - MongoDB wrappers to provide the API for MongoDB object databases in Node.js.
        * redis - Redis client library.
        * forever - Probably the most common utility for ensuring that a given node script runs continuously. Keeps your Node.js process up in production in the face of any unexpected failures.
#### Good Node Use Cases
    * "...blocking operations are the root of all evil—99% of Node misuses come as a direct consequence."
        - Tomislav Capan, 2013
    * Chat
        * Messages relatively small
    * API on top of an Object DB (MongoDB)
        * no data conversion
            * Rails - convert from JSON to binary models, then expose back as JSON over HTTP when data consumed by Backbone.js, Angular.js, or even jQuery AJAX
    * Queued Inputs
        * lots of concurrent data? db can become bottleneck since it's a blocking operation
        * useful when the client doesn't need to confirm successful data write (eventual consistency)
        * data queued through some type of cache or message queueing (RabbitMQ, ZeroMQ)
        * same thing can be implemented in other languages, but with inferior throughput
    * Data Streaming
        * HTTP requests/responses are streams, not isolated events
        * Process files while they are still uploading
        * Real-time audio or video encoding
    * Application Monitoring Dashboard
        * Gather real-time stats from your user
        * Even reacting to user events realtime
        * Real World Examples (use node.js in their stacks):
            * Hummingbird - http://projects.nuttnet.net/hummingbird/ - "Hummingbird lets you see how visitors are interacting with your website in real time."
            * CANDDi - http://www.canddi.com/ - "CANDDi is an internet start-up that develops web-tracking software to customize interactions with their web visitors."
    * System Monitoring Dashboard
        * Check infrastructure services asynchronously and push data to web clients
#### Less Good Node Use Cases
    * Server-Side Web Application with Relational Database
        * Additional Components Need, Less Mature
            * Sequelize - http://docs.sequelizejs.com/en/latest/
            * 'Object Relational Mapping' (node-orm2) - http://dresende.github.io/node-orm2/
    * Heavy Server-Side Computation and/or Processing
        * CPU-intense operations annuls Node throughput benefits
        * But you could always throw heavy computations into a background process - RabbitMQ, ZeroMQ, etc. 



#### References
    * http://en.wikipedia.org/wiki/Node.js 
    * http://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js
    * http://code.tutsplus.com/tutorials/real-time-chat-with-nodejs-socket-io-and-expressjs--net-31708


