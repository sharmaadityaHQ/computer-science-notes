## Message Queues

- Message Queues are widely used in asynchronous systems.

- Asynchronous message processing allows the client to relieve itself from waiting for a task to complete. Client can process other tasks during that time. It also allows the server to process the tasks in the order or priority it wants.

- Messaging queues provide useful features like persistence, routing and task management. It combines the features of load balancing and a heart beat monitor which checks if a server is up and running.

- The techniques used in load balancing like consistent hashing also remove the possibility of assigning duplicate requests to multiple servers when a server goes down apart from uniformly distributing load among the servers.

Examples - Kafka, Rabbit MQ, Zero MQ, JMS