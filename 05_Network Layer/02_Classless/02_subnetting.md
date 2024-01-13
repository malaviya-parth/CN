## Question
An organisation is granted with block 130.34.12.64/26 It needs 4 subnets with equal hosts
1. Total IP in block
2. Net Mask
3. Subnet mask
4. Total number of IP addresses in each subnet
5. Starting address & last address of each subnet

### Solution
- There are 6 bits left for the hosts purpose so total IPs: $2^{6}$
- Net Mask: 255.255.255.192
- Net ID: 130.34.12.64
- 4 subnets are required so 2 bits will be used for that purpose
- Subnet Mask: 255.255.255.240
- Total IPs in each Subnet: $2^{4}$
- **Addresses of Subnet**
- First Subnet:
  - 1st: 130.34.12.64/28
  - Last: 130.34.12.79/28
- Second Subnet:
  - 1st: 130.34.12.80/28
  - Last: 130.34.12.95/28
- Third Subnet:
  - 1st: 130.34.12.96/28
  - Last: 130.34.12.111/28
- Fourth Subnet:
  - 1st: 130.34.12.112/28
  - Last: 130.34.12.127/28

## Question
An organisation is granted with block 130.34.12.0/22 | It needs 8 subnets with equal hosts
1. Total IP
2. Net Mask
3. Subnet Mask
4. IPs in each subnet
5. 1st and last address of each subnet

### Solution
- Total IPs: $2^{10}$
- Net Mask: 255.255.252.0
- Subnet Mask: 255.255.255.128
- IPs in each: $2^{7}$
- **Addresses**
- First:
  - 1st: 130.34.12.0/25
  - Last: 130.34.12.127/25
- Second:
  - 1st: 130.24.12.128/25
  - Last:130.24.12.255/25
- Third:
  - 1st: 130.24.13.0/25
  - Last: 130.24.13.127/25
...

## Question
A block 36.46.56.0/24 is divided into 3 groups of 120,60,10. Design the subnets

### Solution
- One bit to break in halves for 128 addresses
- 36.46.56.0/25 - 36.46.56.127/25
- Other half break it into 2 for 64 hosts
- 36.46.56.128/26 - 36.46.56.191/26
- The other half break it into 4 and give one for 16 hosts
- 36.46.56.192/28 - 36.46.56.207/28

## Question
An ISP is granted with block 190.100.0.0/16. It wants to distribute these addresses into 3 group of customers.
1. 64 customers each need 256 IP addresses
2. 128 customers each need 128 IP addresses
3. 128 customers each need 64 IP addresses  

Asign the subnets

### Solution
- Total IP requirements:
  - First Group: $2^{14}$
  - Second Group: $2^{14}$
  - Third Group: $2^{13}$
- Available addresses: $2^{16}$
- Make 4 Parts of given address
  - First Group: 190.100.0.0/18 - 190.100.63.255/18
    - 1st: 190.100.0.0/24 - 190.100.0.255/24
    - 2nd: 190.100.1.0/24 - 190.100.1.255/24
    - 64th: 190.100.63.0/24 - 190.100.63.255/24
  - Second Group: 190.100.64.0/18 - 190.100.127.255/18
    - 1st: 190.100.64.0/25 - 190.100.64.127/25
    - 2nd: 190.100.64.128/25 - 190.100.64.255/25
    - 3rd: 190.100.65.0/25 - 190.100.65.127/25
    - 256th: 190.100.127.128/25 - 190.100.127.255/25
- For third group we need to divide the third subnet into half
- Third Group: 190.100.128.0/19 - 190.100.159.255/19
  - 1st: 190.100.128.0/26 - 190.100.128.63/26
  - 2nd: 190.100.128.64/26 - 190.100.128.127/26
- Wastage: 24K addresses