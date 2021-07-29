## Representational State Transfer (REST)


REST API's are best for domain modeling (resources or entities) and making CRUD available for our data.

- Client-Server relationship where server-side data are made available through simple formats like JSON.
- Stateless (not persisting sessions between requests)
- Focuses on uniformity
- Responses should declare cacheability (helps scale API's)

## Remote Procedure Call (RPC)

RPC based API's are best for actions (procedures or commands).

- Similar to calling a function with a name and arguments
- Mostly use GET for fetching information and POST for everything else. Eg. POST /doWhateverThingNow

## Conclusion

- If an API is mostly actions, maybe it should be RPC.
- If an API is mostly CRUD and is manipulating related data, maybe it should be REST.

## Use both REST and RPC

Example Problem

We have a REST API to manage a web hosting company. We can create new server instances and assign them to users, which works nicely, but how do we restart servers and run commands on batches of servers via the API in a RESTful way?

Possible Solution

Create a simple RPC-style service that has a POST /restartServer method and a POST /execServer method which could be executed on servers built and maintained via the REST server.
