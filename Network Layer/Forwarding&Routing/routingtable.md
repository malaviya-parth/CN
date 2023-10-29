## How to fill the routing table

- Suppose a router R1 is connected directly to 4 networks [ 180.70.65.128/26, 201.4.16.0/22, 180.70.65.192/27, 201.4.22.0/24 ] and one port connects to router which is connected to the rest of the internet[ 180.70.65.200 ].
- The table is feild according to the longest mask matxhing technique means network with longest net ID comes first.
- Table entries:

| Mask | Net ID | Next hop | Interface/Port |
| ---- | ------ | -------- | -------------- |
| /27  | 180.70.65.192 | - | m2 |
| /26  | 180.70.65.128 | - | m0 |
| /24  |  201.4.22.0   | - | m3 |
| /22  |  201.4.16.0   | - | m1 |
|  /0  |    0.0.0.0    | 180.70.65.200 | m2 |

- The last entry is for the remaining packets of the internet, look the main router is connected to some network and in that netwrok there is a router which is connected to the internet.
- Suppose want to send packet to 180.70.65.140
  - First mask with /27, Net ID: 180.70.65.128
    - Not the required one
  - Second mask with /26, Net ID: 180.70.65.128
    - Required one, packet forwarded to m0
- Packet with ID: 201.4.22.35
  - Firtst two tried, ofcourse no match
  - Third try with /24, Net ID: 201.4.22.0
    - Required one, packet forwarded through m3
- Packet with ID: 180.24.32.0
  - Tried first four no matching
  - Matched with fifth, sent through port m2
    - Also next hop is mentioned so it will go to the router connected to the internet.