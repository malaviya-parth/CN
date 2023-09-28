# Subnettin in Classful Adddressing

## Introductiom
- If an Organization needs $2^{22}$ addresses which class address will you provide
  - Range of A is $2^{24}$ and range of class B is $2^{16}$
  - So we will provide class A address
- Now here we allocated $2^{24}$ addresses to an organization which needs only $2^{22}$ addresses
  - So we are wasting $2^{24} - 2^{22} = 4 \times 2^{22} - 2^{22}$ addresses = $ 3 \times 2^{22}$ addresses = $3 \times 2^{2} \times 2^{20}$ = 12 Million addresses
- So here the addresses gets wasted, else one thing can be done is the org can search 3 more org which require $2^{22}$ addresses and then we can allocate class A address to all of them.
- So they collectively purchase one block and then divide it among themselves.
- This division is done with the help of subnetting.

## Question
- Given an IP address = 200.40.50.0, share this address among 4 organizations. Find first and last address of each organization.

### Solution
- From address we can see that it is a class C address.
- There are total $2^{8} = 256$ blocks in class C.
- Equal share of each organization is $256/4 = 64 = 2^6$ IP addresses.
- Calculation of addresses:
- $1^{st}$ organization:
  - There are 6 bits in host part on which the share of organization will be allocated.
  - Keeping first two bits set to zero
  - For first org rest 6 bits are also set to zero
  - i.e. = 00 000000
  - First address = 200.40.50.0
  - For last address all 6 bit zeros are converted to 1s
  - i.e. 00 111111
  - Last address = 200.40.50.63
- $2^{nd}$ organization:
  - Add one to the last address of $1^{st}$ organization
  - i.e. 00111111 + 1 = 01 000000
  - First address = 200.40.50.64
  - Convert all 6 zeros to ones
  - i.e. 01 111111
  - Last address = 200.40.50.127
- $3^{rd}$ organization:
  - Add one to the last address of $2^{nd}$ organization
  - i.e. 01111111 + 1 = 10 000000
  - First address = 200.40.50.128
  - Convert all 6 zeros to ones
  - i.e. 10 111111
  - Last address = 200.40.50.191
- $4^{th}$ organization:
  - Add one to the last address of $3^{rd}$ organization
  - i.e. 10111111 + 1 = 11 000000
  - First address = 200.40.50.192
  - Convert all 6 zeros to ones
  - i.e. 11 111111
  - Last address = 200.40.50.255
- Here the first two bits of host octet are used to label orgnaizations and rest 6 bits are used to label hosts in each organization.

## Question
- Given an IP address 141.14.0.0, share this address among 4 organizations. Find first and last address of each organization.

### Solution
- Looking at the address we can see that it is a class B address.
- There are total of $2^{16} = 65536$ addresses in class B.
- Equal share of each organization is $65536/4 = 16384 = 2^{14}$ addresses.
- $1^{st}$ organization:
  - 00 000000 00000000
  - First address = 141.14.0.0
  - 00 111111 11111111
  - Last address = 141.14.63.255
- $2^{nd}$ organization:
  - 01 000000 00000000
  - First address = 141.14.64.0
  - 01 111111 11111111
  - Last address = 141.14.127.255
- $3^{rd}$ organization:
  - 10 000000 00000000
  - First address = 141.14.128.0
  - 10 111111 11111111
  - Last address = 141.14.191.255
- $4^{th}$ organization:
  - 11 000000 00000000
  - First address = 141.14.192.0
  - 11 111111 11111111
  - Last address = 141.14.255.255

## Question
- Given an IP address 80.0.0.0, share this address among 4 organizations. Find first and last address of each organization.

### Solution
- Looking at the address we can see that it is a class A address.
- There are total of $2^{24} = 16777216$ addresses in class A.
- Equal share of each organization is $16777216/4 = 4194304 = 2^{22}$ addresses.
- Here we take 2 bits to label organizations and 22 bits to label hosts in each organization.
- $1^{st}$ organization:
  - 00 000000 00000000 00000000
  - First address = 80.0.0.0
  - 00 111111 11111111 11111111
  - Last address = 80.63.255.255
- $2^{nd}$ organization:
  - 01 000000 00000000 00000000
  - First address = 80.64.0.0
  - 01 111111 11111111 11111111
  - Last address = 80.127.255.255
- $3^{rd}$ organization:
  - 10 000000 00000000 00000000
  - First address = 80.128.0.0
  - 10 111111 11111111 11111111
  - Last address = 80.191.255.255
- $4^{th}$ organization:
  - 11 000000 00000000 00000000
  - First address = 80.192.0.0
  - 11 111111 11111111 11111111
  - Last address = 80.255.255.255

## Question
- Given an IP address 80.0.0.0, share this address among 8 organizations. Find first and last address of each organization.

### Solution
- Looking at the address we can see that it is a class A address.
- There are total of $2^{24} = 16777216$ addresses in class A.
- Equal share of each organization is $16777216/8 = 2097152 = 2^{21}$ addresses.
- Here we take 3 bits to label organizations and 21 bits to label hosts in each organization.
- $1^{st}$ organization:
  - 000 00000 00000000 00000000
  - First address = 80.0.0.0
  - 000 11111 11111111 11111111
  - Last address = 80.31.255.255
- $2^{nd}$ organization:
  - 001 00000 00000000 00000000
  - First address = 80.32.0.0
  - 001 11111 11111111 11111111
  - Last address = 80.63.255.255
- $3^{rd}$ organization:
  - 010 00000 00000000 00000000
  - First address = 80.64.0.0
  - 010 11111 11111111 11111111
  - Last address = 80.95.255.255
- $4^{th}$ organization:
  - 011 00000 00000000 00000000
  - First address = 80.96.0.0
  - 011 11111 11111111 11111111
  - Last address = 80.127.255.255
- So on...

## Question
- Given an IP address 80.0.0.0, share this address among 16 organizations. Find first and last address of 14th organization.

### Solution
- It is a class A address.
- As 16 parts are there so we need 4 bits to label organizations and 20 bits to label hosts in each organization.
- $14^{th}$ organization:
  - 1101 0000 00000000 00000000
  - First address = 80.208.0.0
  - 1101 1111 11111111 11111111
  - Last address = 80.223.255.255

## Question
- Given an IP address 80.0.0.0, share this address among 512 organizations. Find first and last address of 251th organization.

### Solution
- It is a class A address.
- As 512 parts are there so we need 9 bits to label organizations and 15 bits to label hosts in each organization.
- $251^{th}$ organization
  - 01111101 0 0000000 00000000
  - First address = 80.125.0.0
  - 01111101 0 1111111 11111111
  - Last address = 80.125.127.255

## Note:
> Above 80.255.255.255 is called Direct Broadcast Address. When a packet from internet is needed to send to all host of netwrok 80.0.0.0 this address is used.  
>
> If a host inside the LAN want to broadcast a packet to all hosts in the LAN then it uses 255.255.255.255 address which is called Limited Broadcast Address, used because when it is sent to the router connected to it, it simply drops restricitng the packet to go outside the LAN.

## Question
80.0.0.0, write DBA and subnet id for 3rd subnet, shared among 4 organizations.

### Solution
- $3^{rd}$ organization:
  - 10 111111 11111111 11111111
  - Last address = 80.191.255.255 = DBA
  - 10 000000 00000000 00000000
  - First address = 80.128.0.0 = Subnet ID
- From this we must recall that we used to subtract 2 from the total number of addresses to get the number of hosts in each subnet because first and last address are reserved for network address and broadcast address respectively.

## Question
- Given an IP address 80.0.0.0, 6 bit subnet number, Find number of subnets and number of hosts in each subnet.

### Solution
- Given IP is of class A.
- There are 6 bits in subnet number so there are $2^{6} = 64$ subnets.
- Number of Hosts in each subnet = $2^{24-6} - 2 = 2^{18} - 2 = 262142$

## Routing in Subnetting

- The router connected to Internet and LAN router has only the information of the network address of the LAN and not the subnet addresses.
- There is a site router which has the information of the subnet addresses.
  - This site router will have entries equal to the number of subnets in the LAN.
  - It will map each subnet ID with the port number in the table.
- From a given ID site router will find subnet ID and then it will forward the packet to the LAN router.
  - Internet router does AND with the class net mask, here site router will do AND with subnet mask.
  - The subnet mask will have first k bits as 1 which are used to number the subnets and rest bits as 0 which are used to number the hosts in each subnet.

## Summary
> Internet Router forwards the packet to the site router using Net Mask.  
> Site Router forwards the packet to the desired host using Subnet Mask.

## Question
Suppose there is a Class A address and is shared among 8 organization what will be it's subnet mask.

### Solution
- 3 bits will be used to label subnets
- Subnet Mask = 255.224.0.0

## Question
Class B IP address shared among 16 organizations, what will be it's subnet mask.

### Solution
- 16 subnets so 4 bits to label them
- Subnet Mask = 255.255.240.0

## Question
Class C IP address shared among 2 organizations, what will be it's subnet mask.

### Solution
- Subnet Mask = 255.255.255.128
- with one bit we can label subnets

## Question
Class A IP addresss with 1024 subnets, what will be it's subnet mask.

### Solution
- 9 bits to label subnets
- Subnet Mask = 255.255.192.0

## Question
Class C address with 32 subnets, what will be it's subnet mask.

### Solution
- 5 bits to label subnets
- Subnet Mask = 255.255.255.248

## Question
A subnet mask contains 15 1s, what are the number of subnets possible

### Solution
- 15 1s are there in the subnet mask so it will be : 255.254.0.0
- First octet is 255 and next is not 255 so it is a class A address.
- Second octet contains 7 1s so number of subnets = $2^{7} = 128$

## Question
A subnet mask contains 18 1s, what are the number of subnets possible

### Solution
- Subnet mask = 255.255.192.0
- Now this has first two octets as 255 so it is a class B address.
- Also there is a possibility of more than 8 bits can be used for subnetting if it belongs to class A.
- If belongs to class B then subnets = $2^{2} = 4$
- If belongs to class A then subnets = $2^{10} = 1024$