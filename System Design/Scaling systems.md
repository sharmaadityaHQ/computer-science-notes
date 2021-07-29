## Problem

How should we scale a pizza shop to process more orders?

## Solution

- Optimize processes and increase throughput using the same resource. (Vertical Scaling)
- Preparing pizzas beforehand during non-peak hours. (Preprocessing and CRON jobs)
- Keep backups and avoid single point of failure (backups)
- Hire more resources to get more work done (Horizontal Scaling)
- Create teams of chefs based on specializations like pizza, garlic bread etc. (Mircoservices architecture - Dividing responsibilities and scaling individual teams at different rates)
- Open a new pizza shop at another location in case there is power cut in the other one. (Distributed systems - Fault tolerant and quicker response times)
- Route cutomer requests to shops based on a parameter like delivery time (Load Balancer)
- Decouple the systems so that separate systems can be handled more efficiently
- Logging and metrics calculation to keep a tab of all events like faulty machines in 1 shop leading to higher delivery times.
- Extensible (designed to allow the addition of new functionality)

## High Level Design

- Order overload (Recruitment)
- Complexity (Separation of concerns)
- Mishaps (Fault Tolerance)