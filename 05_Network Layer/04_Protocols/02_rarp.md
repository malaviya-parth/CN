## Reverse Address Resolution Protocol

- Physical address to Logical address Mapping
- Whenever diskless machine is booted then it moves it's PA(NIC Card) but doesn't move it's IP address. So, it was RARP to move it's IP address.
- RARP is based on client-server model(unlike ARP) because now station wants to move it's own LA when it move it's PA.
- Just like ARP, RARP request packet is broadcasted, but RARP is unicasted.

## Drawback
- RARP has a serious drawback that it can't be used in subnetting.
- So if Network administrator has made several subnets in a Network then in each subnet RARP server must be present.
- Hence it is not used nowadays.
- After RARP 2 more protocols were developed for PA to LA mapping i.e. BOOTP & DHCP

## BOOTP & DHCP
- Both are application layer protocols
- Both can work in subnetting i.e. client & server may be in different network.
- Since both these rptocols works at application layer, so every message is generated at application layer & it is encapsulated in user datagram UDP is used at transport layer [Port No. 67 for server & 68 for client]
  - We use UDP because DHCP and BOOTP requests are small in size and using UDP it will save the network bandwidth.
- This user datagram is encapsulated in datagram at N/W layer but problem is that what sender fill in SIP and DIP of IP Header.
  - SIP: 0.0.0.0 & DIP: 255.255.255.255
- Further this datagram is encapsulated in frame
  - SPA: own PA & DPA: FF:FF:FF:FF:FF:FF
- Problem is same i.e. request packet is broadcasted & hence it can't cross router so one of the host( or router can be configured to operate at application layer) can be used as relay agent & when it receives request packet then it encapsulates the message in unicast datagram & send it to BOOTP server.
- Simply we can say that now relay agent put in own IP in SIP and IP of BOOTP server in DIP & now this datagram can cross routers can reach BOOTP server & it will reply to relay agent and relay agent reply to station.
  - Station Broadcasts message
  - When message reaches Relay agent
    - Relay agent knows the IP of BOOTP server
  - SIP is now made of Relay agent and DIP of BOOTP server
  - Hence packet can reach upto BOOTP server now
  - Later BOOTP server reply to the packet and sends to relay agent
  - Relay agent then sends this reply to station and hence station get's to know the IP.
  - The station stores the PA in it's cache memory.

## BOOTP
- BOOTP server maintains a table of LA & PA, it can do only static mapping.
- No. of stations = No. of IP addresses
  - Suppose there are 100 pcs in office, 50 work in morning and 50 work in night.
  - But we have only static mapping so we need to give IP to each pc because if we buy only 50 IPs and change allocation in day & night BOOTP being a static won't be able to change the table.
- Hence , to prevent this wastage DHCP is used. 

## DHCP
- Everything is same as BOOTP but DHCP server has 2 databases one is used for static mapping whle other for dynamic mapping.
- Whenever query packet arrives at DHCP server then it first searches the database having static mapping if the entry is missing then it will allocate a random IP address from the pool of IP addresses to the client & male an entry in database containing dynamic mapping for some time [say 10 min.]
- After that renew request must come from client & another IP is given but if request doesn't come then connection is terminated automatically.
- Static IP addresses are still needed for servers like webserver, email server, file server etc. because they should go down even for a minute that's why.

### Dynamic Database Entry
MAC  IP LeaseTime  
 Ma  Ia    10

### Advantages
- Problem of subnetting solved
- Dynamic so stations >> IP addresses
- It is backward compatible with BOOTP & hence replace BOOTP server with DHCP server & no need to change software for clients i.e. they will send request like they send to BOOTP [ Port No. same 67-68.]