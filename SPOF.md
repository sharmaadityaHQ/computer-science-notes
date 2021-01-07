## SPOF basics

- A single point of failure (SPOF) is a critical point in the system whose failure can take down the entire system. A lot of resources and time is spent on removing single point of failures in an architecture/design.

- Use multiple instances of every component or more nodes in the service. This allows the system to resiliently switch to another service instead of failing requests.

- Have backups. Master-Slave architecture. Backups are useful in components dealing with data like databases.

- Set up the system in multiple regions.

- Multiple IP addresses in the DNS resolving for the same host thus connecting to different load balancers and servers.

- The CAP theorem does not allow removing SPOFs if perfect consistency is required.