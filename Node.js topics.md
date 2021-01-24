Nodejs is not Javascript. Nodejs is a runtime environment for Javascript, an environment to run Javascript and not a programming language.

### Streams

- Streams are objects that let you read data from a source or write data to a destination in continuous fashion. Streams allow for time and memory-efficient data transferring.

- A buffer is a temporary memory that a stream takes to hold some data until it is consumed.

### Events and Event Emitters

- Nodejs has an asynchronous event driven architecture.
- Pretty much everything in Node emits events. Eg. Stream events like `error`, `end` and `data`.
- Learn to use events in your application by creating your own events and utilize the event emitter.

### File System

- To deal with files by reading them, writing to them or collecting information about them on the server side.
- When interacting with the file system you will automatically interact with streams and events as well.

### HTTP

- Learn how things get to the server (requests), connection (agent), in what format (header, body), what information they contain, how to respond (response) to them, what details you can include.

### Module and Architecture

- The idea that every file is a module (implements the module pattern) with its own scope and you can choose what to expose or not pretty much defines Nodejs applications.

### Global

- On the browser, you create a global variable(with var) which will be available everywhere (global scope). With NodeJs things are different, the top level is the module itself so, any `global` variable you create is local to the module and you choose what the module exports to the rest of the application which by importing you know exactly what each module needs and where they all come from.

### Cluster and Process

- 
