## GATE 2003
Subnet Mask of N/W: 255.255.31.0, Which of the following pairs of IP addresses belong to this N/W.
1. 172.57.88.62 & 172.56.87.23
2. 10.35.28.2 & 10.35.29.4
3. 191.203.31.87 & 191.234.31.88
4. 128.8.161.43 & 128.8.161.55

### Solution
- Option 1:
  - 88: 01011000 & 87: 01010111
  - AND with Mask
  - 88: 00011000 & 87: 00010111
  - ❌
- Option 2:
  - 28: 00011100 & 29: 00011101
  - AND with Mask
  - 28: 00011100 & 29: 00011101
  - ❌
- Option 3;
  - 203 and 234
  - Subnet ID will be different for both due to this
  - ❌
- Option 4:
  - 161: 10100001
  - Both will have subnet ID: 128.8.1.0
  - ✅

## GATE 2004
Subnet Mask: 255.255.255.192, Maximum no. of host??

### Solution
- Maximum number of Hosts:
  - 255.255.255.11000000
  - There are 6 0s, so Maximum number of Hosts = $2^{6}-2 \rightarrow 62$

## GATE 2005
Class B N/W has 64 subnets, Subnet Mask?

### Solution
- 255.255.11111100.0
- 255.255.252.0

## GATE 2005
Given class C N/W: 204.204.204.0, 3 Subnets having 100,50,50 hosts. Possible set of subnet address/subnet mask pairs
1. 204.204.204.128 / 255.255.255.128  
   204.204.204.0 / 255.255.255.128  
   204.204.204.64 / 255.255.255.192
2. 204.204.204.0 / 255.255.255.192  
   204.204.204.192 / 255.255.255.128  
   204.204.204.64 / 255.255.255.128
3. 204.204.204.128 / 255.255.255.128  
   204.204.204.192 / 255.255.255.192  
   204.204.204.224 / 255.255.255.192
4. 204.204.204.128 / 255.255.255.128  
   204.204.204.64 / 255.255.255.192  
   204.204.204.0 / 255.255.255.192

### Solution
- Here concept of VLSM will be used
- First divide block into 2 halves, for this we need 1 bit and block ID for 100 host can be either 204.204.204.0 OR 204.204.204.128 / Subnet Mask: 255.255.255.128
- Now, divide either block in again two halves, Subnet Mask for later two: 255.255.255.192
- According to option first address of 100 host block is 204.204.204.128 so it may go upto now 204.204.204.255
- But the other two blocks are given the addresses from the same half 192 and 224 hence partion in this way won't yeild desired output.
- Option satisfies all, so it is correct.

## GATE 2006
Subnetted class B N/W has following broadcast address 144.16.95.255. Subnet Mask?
1. Is necessarily 255.255.224.0
2. Is necessarily 255.255.240.0
3. Is necessarily 255.255.248.0
4. Could be any of above

### Solution
- Class B address, last octet is all 1 so no role in NET ID
- 95 = 01011111
- From this we can say that last 5 ones are necessarily used for Host and first 3 can be used for NET ID
- 128+64+32=224
- So, necessarily it will be 255.255.224.0
- It can also be 255.255.240.0 or 255.255.248.0 or so on..., but not necessarily
- But yes anyone from above can be subnet mask, so Option D.

## Question
Class B N/W split into subnets with 6 bit subnet No. Maximum No. of Subnets & Maximum No. of Hosts in each subnet.
| Subnets  | Hosts  |
| -------  | -----  |
|    62    | 262142 |
|    64    | 262142 |
|    62    |  1022  |
|    64    |  1024  |

### Solution
- 6 Bits are used in subnets so, 64 subnets are possible according to RFC 1812.
- Now, 10 left for host, No. of Hosts = 1022 as one of them will be used for subnet ID and one for broadcast address.
- No option like that, so we consider RFC 950 and answer now will be 62, 1022

## GATE 2010
Computer A: 10.105.1.113, Computer B: 10.105.1.91, Both uses same Netmask N. N value that could not be used if A & B belong to same N/W.
1. 255.255.255.0
2. 255.255.255.128
3. 255.255.255.192
4. 255.255.255.224

### Solution
- Using option 1 they both will get same Subnet ID
- Using option 2 they both will get same Subnet ID
- Using option 3 they both will get same Subnet ID
- Using option 4 they both will get diff Subent ID
  - Option 4: ID1: 10.105.1.96 & ID2: 10.105.1.64
- Answer: Option 4 should not be used

## GATE 2019
Consider 3 machines  
M: 100.10.5.2, N: 100.10.5.5, P: 100.10.5.6  
Subnet Mask: 255.255.255.252
1. M,N,P belong to same subnet
2. N,P belong to same subnet
3. M,N,P belong to diff subnet
4. M,N belong to same subnet

### Solution
- M: 100.10.5.0
- N: 100.10.5.4
- P: 100.10.5.4
- N,P belong to same subnet
- Option 2