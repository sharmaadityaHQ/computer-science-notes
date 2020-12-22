Scalabiility is the ability of a machine to handle more requests.

## Horizontal Scaling

- Similar to buying more machines.
- Load Balancing is required in horizontal scaling.
- If one of the machine fails then the requests can be redirected to other machines. (Resilient)
- Involves network calls between services so slow (RPC)
- Data inconsistency between various machines
- Scales well as users increase

## Vertical Scaling

- Similar to buying a single but bigger machine.
- Single point of failure
- Involves inter process communication so fast
- Consistent as all data resides on one machine
- Hardware limitations while scaling

The real world hybrid solution combines properties to build systems which are resilient, consistent and have fast inter process communication.
