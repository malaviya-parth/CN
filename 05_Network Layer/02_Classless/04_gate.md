## GATE 2006
C1: 203.197.2.53, C2: 203.197.75.201, Net Mask by C1: 255.255.128.0, Net Mask by C2: 255.255.192.0  
1. C1 and C2 both assume they are on same N/W
2. C2 assume C1 is on same N/W but C1 assume C2 is on different network
3. C1 assume C2 is on same N/W but C2 assume C1 is on different network
4. C1 & C2 both assume they are on different network

### Solution
- Subnet Id C1: 203.197.0.0
- Subnet Id C2: 203.197.64.0
- Subnet of C2 by C1(C2 AND mask of C1): 203.197.0.0
- Subnet of C1 by C2(C1 AND mask of C2): 203.197.0.0
- Now, Subnet of C1 and C2 by C1 is same, so C1 will think C2 is in it's N/W.
- Subnet of C2 and C1 by C2 is different, so C2 will think C1 is in other N/W.
- Option C.

## GATE 2008
Subnet Mask of Class B N/W: 255.255.248.0, Maximum no. of Hosts per subnet.

### Solution
- 248 means 3rd octet has 5 leading 1s
- Number of Hosts = $2^{32-21}-2 = 2^{11}-2 = 2046$

## GATE 2012
ISP: 245.248.128.0/20 | Half chunk to A | one-forth chunk to B | Remaining chunk with itself | Valid allocations of addresses to A & B.
1. 245.248.136.0/21 & 245.248.128.0/22
2. 245.248.128.0/21 & 245.248.128.0/22
3. 245.248.132.0/22 & 245.248.132.0/21
4. 245.248.132.0/24 & 245.248.132.0/21

### Solution
- Half to A
  - Subnet ID: 245.248.128.0/21 OR
  - Subnet ID: 245.248.136.0/21
- One-forth to B
  - Subnet ID: 245.248.128.0/22 OR
  - Subnet ID: 245.248.132.0/22 OR
  - Subnet ID: 245.248.136.0/22 OR
  - Subnet ID: 245.248.140.0/22
- If upper part given to A, then possible for B is 3&4
- If lower part given to A, then possible for B is 1&2
- Option A