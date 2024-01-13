## How to Fill Routing Table
- Basically there are two ways to fill routing table.
  - Network Administrator fills the table
  - Routers fill their table themselves using any Routing Algorithm

## Types of Routing Algorithm
- Adaptive
  - If one of the router fails or congestion occurs then Routing table of other routers is updated.
- Non-Adaptive
  - No updation
  - Table is filled automatically only once
  - Can't adapt with changes
- Broadcasting
  - Adaptive or Non Adaptive

## Types of Adaptive Routing
- Centralized
  - Path Vector Routing
- Isolated
  - Hot Potato
  - Backward Learning
- Distributive
  - Distance Vector Routing
  - Link State Routing
- Delta
  - Hybrid of Centralized and Isolated

## Centralized
- Here there is a centralized Machine/Router where all the information of routing is stored.
- Other routers connected to different networks when they get any packet to forward, they ask the centralized Machine/Router query of where to forward.
- The machine replies and the packet is forwarded.
- Meanwhile the reply comes the routers stores the packets in their RAM for that much amount of time.

### Advantage
- No. of entries is less

### Disadvantages
- If the central machines stops, everything stops.

## Isolated
- Table is updated to all movements of datagram in Network i.e. routers doesn't seek help from neighbour as a result packet may be sent through congested route.
### Hot Potato
- With each outgoing port of router a queue is maintained.
- Router will place the packet in smallest queue, so that packet can be forwarded as fast as possible.
- This type of routing is used in fully connected network, like mesh topology K5, K6, etc.
### Backward Learning
- Just like transparent bridges, here also learning is done by Source IP Addres.
- One way to implement backward learning is use Hop counter & it will be incremented on each hop.
- When a node receives a packet it note down the no. of hops it has taken to reach the node.
- Like if Source sent a packet to router R1 then it went to router router R2, the table of R2 will have entry of Source with value 2 as it took 2 hops to reach.
- If the previous value of hop count in table is more than packet hop entry then, table is updated else not.
- Problem is that when best route goes down then it can't recall 2nd best Route.
- Hence all nodes have to forget all info periodically & start proces again.

## Distributive
- Here learning is done from neighbours & not from datagram movements
- Nodes receive information from its neighbouring nodes & take action decision about which way is best to send packet.
- This technique is used in Distance vector routing & Link State Routing.

## Non-Adaptive
- Flooding
- Random Walk
  - Non-Adaptive version of Hot Potato
- Multipath
  - Non-Adaptive version of Delta routing

## Flooding
- As the name suggest every inconming packet is sent on every outgoing line except the line from which the packet came.
- Problem is that packet may go in a loop
  - Like A is connected to B and C, B is connected to C.
  - A gives to B and C
  - B gives to C, C gives to B
  - C gives to A (Due to B gave packet to C)
  - This process is now infinite loop of A-C.
- 3 Solutions to avoid loop:-
  - Sequence No.
  - Hop Count
  - Spanning Tree
- Application:
  - Where it is necessary that packet reaches earliest possible like military applications.

### Sequence Number:-
- Each datagram will have a unique seq no
- When node receives a datagram it will make entry in table & forward it from all the ports except incoming.
- when packet arrives, it first search the table & if entry is present then it drops the packet.
### Hop Count
- Similar to TTL field
- This value is decremented (or incremented) when ever router forward the packet.
- When this value become 0 or (maximum value) packet is dropped by router.
### Spanning Tree
- The packet is sent only on those limbs that leads to destination by contructing a spanning tree where root is the source.
- It is possible only when all the intermediate nodes have knowledge about Netwrok topology.

## Note:
- If we have a large network & many of the routers are not working & still we want to send packet then best algo will be flooding.
- It guarantees fastest delivery i.e. packet arrives at destination very early because all paths are tried and one of them will be the fastest.

## BroadCasting
- Adaptive
  - Flooding
- Can be Adaptive or Non-Adaptive
  - MultiDestination
    - Used in Multicasting
  - Spanning Tree
  - Reverse Path

## Type based on Domains
- Inter Domain
  - Path Vector Routing
- Intra Domain
  - Distance Vector Routing
  - Link State Routing
- Domain means an autonomous system
- An autonomous system is a large network owned by any company eg: BSNL, Airtel, etc.