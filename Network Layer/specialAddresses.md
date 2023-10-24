## First
- 0.0.0.0/32
- If any machine don't know it's own IP addrress then it sends the data writing Source IP as 0.0.0.0/32.

## Second 
- 255.255.255.255/32
- It is also known as Limited broadcast address.
- When source want to broadcast packet within the network it sends packet with destination addresss as 255.255.255.255/32.

## Third
- First & Last IP address of the block
- First is used as Net ID and Last is used as Broadcast address
- One host use Broadcast IP of foreign network to direct a broadcast to every node of foreign network.

## Forth
- 127.0.0.0/8 this whole block of $2^{24}$ IPs is reserved.
- Loop-back addresses
- If Source and destination both are on the same machine, then we use loopback addresses.
- We can have both same just the processes are the same machine are different.
- Using this, the hacktic work of unveiling Data Link and Physical layers to transfer the network is skipped. Just the layers used are App, Transport and Network.
- Used for Debugging IP S/W purpose.
- Checking NIC card

## Fifth
- 224.0.0.0/4 (Multicasting)
- 256 Million IPs

## Private IPs
- 192.168.0.0/16
- 10.0.0.0/8
- 172.16.0.0/12
- 169.254.0.0/16
- There existence matter inside their own LAN only, so over Internet they can repeat but not inside their own LAN.
```
192.168.0.1(SIP) --...--

192.168.0.2(SIP) --SIP|251.61.71.81(DIP)-- NAT(250.40.50.60) -- 250.40.50.60|DIP-- Google(DIP)

192.168.0.3(SIP) --...--
```
- The host send des and src addresses, NAT replace privsate IP with Public IP and send to internet
- Internet respond with desIP as public IP of Network, Again NAT translates this Publice IP to private IP with help of table
- In table it stores the Src IP and Des IP written in the packet when packet was sent.
- It compares SRC IP of response packet with Des Ip written in the table when it was sent.
- Also port address is stored in the table so that if more than one source want to communicate with same des then it will be helpful to distinguish.

## Which of the following cannot be Source IP
1. 127.0.0.1 ✅
2. 127.0.0.5 ✅
3. 0.0.0.0 ❌
4. 255.255.255.255 ✅