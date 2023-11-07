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