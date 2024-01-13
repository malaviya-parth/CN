## Address Resolution Protocol

- It is used for mapping Logical address to Physical address.
- If a machine knows IP address of another Machine in it's own Network but doesn't know it's physical address then ARP is used.
- When internet was developed, static mapping was used i.e. a table was maintained which contains LA & PA of each and every machine in LAN.
  - This table was stored on each and every machine.
  - Mapping was needed because datagram is encapsulated in frame. Hence to send a packet we need LA and PA of receiver.

### Static Mapping is not efficient
- If NIC card of any Machine fails then we have to update the table and & this updation must be done in each & every Machine.
- In some LANs like LocalTalk the PA changes everytime the Machine is booted.

## Dynamic Mapping
- It is done with ARP.
- ARP request is broadcasted because sender doesn't know PA of receiver but ARP reply is unicasted.

## Proxy ARP:
- ARP can be used in subnetting also
- If A wants to send message to D which is in other subnet, ARP request is broacasted with PA(FF:FF:FF:FF:FF:FF), now this ARP packet when reaches subnet router it simply drops the packet as it has global broadcast address, but in reply sends it's own PA.
- So, now A sends the packet to router which will then send the packet to the machine D.