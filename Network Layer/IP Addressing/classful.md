# Classful Addressing

- When Internet Developed total $2^{32}$ addresses were available
- This were broken into 5 classes
  - Class A
    - First bit of first octet is 0
    - Range: 0.0.0.0 to 127.255.255.255
    - Number of Addresses: $2^{7} * 2^{24} = 2^{31}$
    - 50% of total available
  - Class B
    - First two bits of first octet is 10
    - Range: 128.0.0.0 to 191.255.255.255
    - Number of Addresses: $2^{6} * 2^{24} = 2^{30}$
    - 25% of total available
  - Class C
    - First three bits of first octet is 110
    - Range: 192.0.0.0 to 223.255.255.255
    - Number of Addresses: $2^{5} * 2^{24} = 2^{29}$
    - 12.5% of total available
  - Class D
    - First four bits of first octet is 1110
    - Range: 224.0.0.0 to 239.255.255.255
    - Number of Addresses: $2^{4} * 2^{24} = 2^{28}$
    - 6.25% of total available
  - Class E
    - First four bits of first octet is 1111
    - Range: 240.0.0.0 to 255.255.255.255
    - Number of Addresses: $2^{4} * 2^{24} = 2^{28}$
    - 6.25% of total available

## Net id and Host id
- Host id is the IP address assigned to our computer or device.
- Id given to every network connected to internet is called Net id.
- Having this ids helps saving searching time in tables as well as reduces the storage space required to store the tables.
- Suppose some packet is coming from the internet to your device, now the router connected to the internet should only bother about the network in which you device is connected to. So it will only look for the net id of your device and then forward the packet to the router connected to your network. Now this router will look for the host id of your device and then forward the packet to your device.
- Net id is not assigned to any computer or Router in network.
- It is the 1st address of the block of addresses assigned to the network.
- Assignment in the classes
  - Class A: First octet signifies Net id, rest 3 octets are host id
  - Class B: First two octets signifies Net id, rest 2 octets are host id
  - Class C: First three octets signifies Net id, rest 1 octet is host id
  - Class D: Not assigned to any network, it is used for multicasting
  - Class E: Not assigned to any network, it is used for research purposes

## How many networks(organizations) can be created in each class?
- Class A: $2^{7} = 128-2 = 126$
- Class B: $2^{14} = 16384 - 2 = 16382$
- Class C: $2^{21} = 2097152 - 2 = 2097150$

## Class A network can have __ IP addresses and __ hosts
- Number of IP addresses: $2^{24} = 16777216$
- Number of hosts: $2^{24} - 2 = 16777214$ (First is for Net id and last is for broadcast id)

## Range of IP addresses in an organization using class A
- First Org: 1.0.0.0 to 1.255.255.255
  - 1.0.0.0 is the Net id
  - 1.255.255.255 is the broadcast id
- As first defines the Network of ORG so it will be fixed and rest can be used for hosts
- Other org: 2.0.0.0 to 2.255.255.255
  - 2.0.0.0 is the Net id
  - 2.255.255.255 is the broadcast id
- Last org: 126.0.0.0 to 126.255.255.255
- 0.0.0.0 to 0.255.255.225 and 127.0.0.0 to 127.255.255.255 are reserved for special purposes
- 89th Organization: 89.0.0.0 to 89.255.255.255
  - First Computer will get address as 89.0.0.1
  - Last Computer will get address as 89.255.255.254

## Class B network can have __ IP addresses and __ hosts
- Number of IP addresses: $2^{16}$
- Number of hosts: $2^{16} - 2$ (First is for Net id and last is for broadcast id)


## Range of IP addresses in an organization using class B
- First Org: 128.0.0.0 to 128.0.255.255
- Second Org: 128.1.0.0 to 128.1.255.255
- 200th Org: 128.199.0.0 to 128.199.255.255
- 257th Org: 129.0.0.0 to 129.255.255.255
- Last Org: 191.255.0.0 to 191.255.255.255

## Class C network can have __ IP addresses and __ hosts
- Number of IP addresses: $2^{8}$
- Number of hosts: $2^{8} - 2$ (First is for Net id and last is for broadcast id)

## Range of IP addresses in an organization using class B
- First Org: 192.0.0.0 to 192.0.0.255
- Second Org: 192.0.1.0 to 192.0.1.255
- 257th Org: 192.1.0.0 to 192.1.0.255
- Last Org: 223.255.255.0 to 223.255.255.

## Net Mask

## Question
Given an IP address, find which is the first address, last address and how many addresses in the block to which this IP address belongs ___. IP = 73.65.45.90

### Solution
- Given address belongs to class A
- First octet NETid and rest HOSTid
- First address = 73.0.0.0
- Last address = 73.255.255.255
- Number of addresses = $2^{24} = 16777216$

> This calculation are performed by routers to find the Net id and Host id of the given IP address with the help of subnet mask.  
> Afte finding the class of IP perform AND operation with subnet mask to find the first address. OR operation with NOT of subnet mask to find the last address.

- To find first address
  - Net Mask for Class A = 255.0.0.0  
  - Net Mask for Class B = 255.255.0.0  
  - Net Mask for Class C = 255.255.255.0
- To find last address
  - Net Mask for Class A = 0.255.255.255
  - Net Mask for Class B = 0.0.255.255
  - Net Mask for Class C = 0.0.0.255
- Net Mask is useful to find Net id which is used by router to find the router to which the packet should be forwarded to.