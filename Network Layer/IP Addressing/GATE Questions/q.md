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