## Need of CLassless Addressing
1. Wastage of address
2. Lot of wastage for single user

## Classless Addressing
- Here the block length is not of fixed size.
- Here the terminology used is prefix and suffix.
  - Prefix means Net ID and Suffix means Host ID
- Entire Internet is one block where Prefix = 0, then there are $2^{32}$ addresses in the block.
- If Prefix length = 32, then there are $2^{32}$ networks.
- If prefix length is 4, then number of addresses in each block = $2^{28}$
- **Representation: 10.20.30.40/24**
  - Here, 24 represents the prefix.
  - This notation is called CIDR notation.
  - Classless Inter Domain Routing

## Question
IP address in block: 10.20.30.40/24. Find Net Mask, 1st address, last address, No. of IP addresses, No. of Hosts.

### Solution
- Net Mask: 255.255.255.0
- First address: 10.20.30.0
- Last address: 10.20.30.255
- No. of IPs: $2^{8}$
- No. of Hosts: $2^{8}-2 = 254$

## Question
IP address in block: 10.20.30.40/23. Find Net Mask, 1st address, last address, No. of IP addresses, No. of Hosts.

### Solution
- Net Mask: 255.255.254.0
- First address: 10.20.30.0
- Last address: 10.20.31.255
- No. of IPs: $2^{9}$
- No. of Hosts: $2^{9}-2 = 510$

## Note:
> IANA (Internet Assigned Numbers Authority) is organisation responsible for block allocation.  
> IANA gives addresses to Bigger organisation or ISP.  
> Else for smaller ISP allocate them.  

## Restriction of Allocation
1. Addresses are given in Power of 2
2. Addresses must be contiguous
3. First address of the block must be divisible by total numbers of IP addresses in the block

## Question
Organisation need 1000 IP addresses, what can be starting address of the block.
1. 10.20.30.40
2. 10.20.30.0
3. 10.20.12.0
4. 10.20.10.0

### Solution
- We need to allocate block of 1024
- We need 10 bits to allocate this
- Last octet 8 zeros no need to check
- 3rd octet check number divisible by 4.
- 12 is divisible by 4, and last octet contains all 0s.
- Answer: Option C