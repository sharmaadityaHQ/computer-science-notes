## Message Queues

- A message queue is a form of asynchronous service-to-service communication used in serverless and microservices architectures.

- Message queues allow different parts of a system to communicate and process operations asynchronously. It provides a lightweight buffer which temporarily stores messages, and endpoints that allow software components to connect to the queue in order to send and receive messages.

- The messages are usually small, and can be things like requests, replies, error messages, or just plain information. To send a message, a component called a producer adds a message to the queue. The message is stored on the queue until another component called a consumer retrieves the message and does something with it.

- Many producers and consumers can use the queue, but each message is processed only once, by a single consumer.

- This messaging pattern is often called one-to-one, or point-to-point communication. When a message needs to be processed by more than one consumer, message queues can be combined with Pub/Sub messaging.

- Asynchronous message processing allows the client to relieve itself from waiting for a task to complete. Client can process other tasks during that time. It also allows the server to process the tasks in the order or priority it wants.

- Messaging queues provide useful features like persistence, routing and task management. It combines the features of load balancing and a heart beat monitor which checks if a server is up and running.

- The techniques used in load balancing like consistent hashing also remove the possibility of assigning duplicate requests to multiple servers when a server goes down apart from uniformly distributing load among the servers.

Examples - Kafka, Rabbit MQ, Zero MQ, JMS, Amazon SQS