## Consistent Hashing and Load Balancing

- Hash function is any function that can be used to map data of arbitrary size to fixed-size values.

- Hashing is used to index and retrieve items in a database because it is faster to find the item using the shorter hashed key than to find it using the original value.

- Let a pie chart represent the load on each server based on the range of requests it handles. Load on each server is proportional to the thickness of pie slice.

- Assume that servers cache data relevant to their request ID (generally contains user info like user id) range to speed up processing.

- If no. of servers are increased or decreased then each node has to load or evict data.

- A node has to do more work if it has to load and evict more data and has a tendency to crash if the pressure increases.

- Request allocation (Assigning a request to a server)

- Consistent hashing assigns requests to the servers in a way such that the load is balanced. The request ID's are arranged in a ring of hash (0 - M-1). The requests hash can be at any point on the ring.

- Server's also have id's. Hash the server id's (0, 1, 2 ...) and take remainder with M (Eg. h(0)%M, h(1)%M ...). Now server is also placed on a point on the ring. The requests are assigned to the closest server in the clockwise direction in the ring. The change in server load on adding servers will be much less than before.

- If we use k hash functions (h1(0)%M, h2(0)%M) then each server will be placed at k points. This is a way to create virtual servers. This way the chance of 1 server getting a lot of load is reduced. If 1 server is removed, multiple points on the ring will be removed so load will be distributed uniformly. If 1 server is added then there will be minimum change as multiple points will be added on different parts of the ring.


