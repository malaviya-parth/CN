## Link State Routing
- DVR was used in ARPANET until 1979, when it was replaced by link state routing.
- In DVR entire Network knowledge is shared between immediate neighbours.
- In LSR knowledge about immediate neighbours is broadcasted in Network.
- DVR only knew about the next hop that where to send this packet, but in lsr routers ought to know the entire map of the network.
- ```
    D --- C
    | \   |
    |   \ |
    A --- B
    ```
- Cost D-C:11, C-B:3, A-B:2, A-D:1, B-D:7
- Unlike DVR here A will receive packet from B,C & D.
- A already knew about immediate neighbours B & D
- After receiving packet from D it came to know about C & B are neighbour of D.
- After receiving packet from C, A came to know that B & C are neighbours.
- Hence, unlike dvr each router here has complete knowledge about topology of the network.
- Now A will apply Dijkstra's algorithm to calculate single source shortest path from A.
- Hence every station broadcast it's table by flooding to every other station.
- After receiving tables from every station each station apply Dijkstra's algorithm to calculate single source shortest path to every other station.
- Hence unlike dvr here table converges very fast i.e. in single step only.

### 5 Steps
1. Discover Neighbour [ Hello Packet ]
2. Compute cost of each neighbour [ Echo Packet ]
3. Make a packet containing all info learned [ Link State Packet ]
4. Send packet to all routers [ Flooding ]
5. Compute cost using Dijkstra's algorithm

## Link State Packets
- A's Link State Packet

| A ||
| - | - |
| Seq No. ||
| age ||
| B | 2 |
| D | 1 |
- B's Link State Packet

| B ||
| - | - |
| Seq No. ||
| Age ||
| A | 2 |
| C | 3 |
| D | 7 |

## Loop Problem
- Let there be a connection of 3 routers in triangle
- A send to B, B send to C, C send to A, and this process goes on infinite loop because routers flood the packets to everyone except incoming route.
- To avoid this loop problem we have the sequence number field, like if A's packet is reached to B it mentions A,0 in RAM; same C mentions A,0 in RAM; now again C sends to A the same packet entry will be there in A's RAM and hence it discards that packet and doesn't flood it forward.
- Sequence number also gives track that which packet is the latest.
- Router stores packet of source router sequence pair, with latest sequence number.
- The sequence number is of 32 bits.
- If router crash, it will lose track of Seq number. It it starts again at 0, the next packet will be rejected as higher sequence numbe rpacket from this router is already present.
- if a sequence number is ever corrupted and 65540 is received instead of 4, packets from 5 to 65540 will be rejected.
### Aging a solution to corrupted sequence numbers and crashes.
- Age states upto what time we have to keep the packet at the router.
  - Age is set to some value and after some interval it decreases by 1.
  - If new packet arrives and if that packet is accepted then age is reset to the value mentioned.
  - If Age becomes 0, then packet is discarded, hence this helps in sequence number corruption and router crashes.

## Difference Between DVR and LSR

| DVR | LSR |
| --- | --- |
| Info about all the routers | Info ablout immediate neighbours |
| is shared with immediate nei. | is shared with all routers |
| Bandwidth required is low | Bandwidth required is high[Flooding] |
| Bellman Ford Algorithm | Dijkstra's Algorithm |
| Low Traffic | High Traffic |
| Table Converges Slowly | Table converges fastly |
| Router have no knowledge of Netwrok | Router have knowledge of topology |
| Count to inf prob | No Count to inf prob |
| RIP protocol | OSPF Protocol |
| Less Calculations | More Calculations |

## GATE 2023 ⭐
Which of the following statements is/are INCORRECT about the OSPF (Open Shortest Path First) routing protocol used in the Internet?
1. OSPF implements Bellman-Ford algorithm to find shortest paths.
2. OSPF uses Dijkstra’s shortest path algorithm to implement least-cost path routing.
3. OSPF is used as an inter-domain routing protocol.
4. OSPF implements hierarchical routing.

### Solution
- 1,3