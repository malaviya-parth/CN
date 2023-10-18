## Question
Subnet Mask $\rightarrow$ 255.224.0.0, Find number of subnets and number of hosts in each subnet

### Solution
- 255 is in the first octet and 224 is added up as 128+64+32 means three bits are used.
- Hence, number of subnets = $2^{3}$ = 8
- Number of hosts in each subnet = $2^{21} - 2$

## Question
Subnet Mask $\rightarrow$ 255.225.224.0, Find number of subnets and number of hosts in each subnet

### Solution
- There are 16 + 3 = 19 ones
- If address belongs to class A
  - Number of Subnets: $2^{11}$
  - Number of Hosts in each subnet: $2^{13}-2$
- If address belongs to class B
  - Number of subents: $2^{3} = 8$
  - Number of Hosts in each subnet: $2^{13}-2$

## Question
Subnet Mask $\rightarrow$ 255.225.225.192, Find number of subnets and number of hosts in each subnet

### Solution
- If belongs to class A
  - Number of Subnets: $2^{18}$
  - Number of hosts in each subnet: $2^{6} -2$
- If belongs to class B
  - Number of subnets: $2^{10}$
  - Number of hosts in each subnet: $2^{6} -2$
- If belongs to class C
  - Number of subnets: $2^{2}$
  - Number of hosts in each subnet: $2^{6} -2$

## Note:
> Number of Subnets are reduced by 2 if we use RFC 950  
> If we RFC 1812 then ther aren't reduced by two  
> Also, number of hosts are reduced by two in both the cases.

## Question
IP address of a block is 200.40.50.60, Subnet Mask of that block is 255.255.255.224, Find the Subnet no. and the subnet ID of the block.

### Solution
- Looking at the IP address we can say that it belongs to Class C IP address.
- Net Mask for class C is 255.255.255.0
- Given subnet Mask is 255.255.255.224
- So, the bits used for subnetting add upto 224 = 128+64+32 = 3 bits.
- 3 bits can make 8 subnets.
- Now, 200.40.50.60 AND 255.255.255.224 = 200.40.50.32
- Since 8 parts are made of 256 $\rightarrow \frac{256}{8} = 32$
- First subnet will be from 200.40.50.0 to 200.40.50.31
- Second will be from 200.40.50.32 to 200.40.50.63
- Hence, Subnet number = 2
- Subnet ID: 200.40.50.32
- Subnet No: 32 = 001 00000 = 1+1 = 2

## Question
IP address of a block is 200.40.50.153, Subnet Mask of that block is 255.255.255.224, Find the Subnet no. and the subnet ID of the block.

### Solution
- Looking at the IP address we can say that it belongs to Class C IP address.
- Net Mask for class C is 255.255.255.0
- Given subnet Mask is 255.255.255.224
- So, the bits used for subnetting add upto 224 = 128+64+32 = 3 bits.
- 3 bits can make 8 subnets.
- Subnet ID:
  - 200.40.50.153 AND 255.255.255.224 = 200.40.50.128
- Subnet no: $\frac{128}{32} + 1 = 5^{th}$
- Subnet No: 128 = 100 00000 = 4+1 = 5

## Question
IP address of a block is 200.40.50.153, Subnet Mask of that block is 255.255.255.240, Find the Subnet no. and the subnet ID of the block.

### Solution
- Looking at the IP address we can say that it belongs to Class C IP address.
- Net Mask for class C is 255.255.255.0
- Given subnet Mask is 255.255.255.240
- So, the bits used for subnetting add upto 240 = 128+64+32+16 = 4 bits.
- 4 bits can make 16 subnets.
- Subnet ID: 200.40.50.144
- Subnet No: $\frac{144}{16} + 1 = 10^{th}$
- OR Subnet number: 144 = 1001 0000, now first 4 bits are used for the subnetting and they add upto 9 hence, Subnet Number: $10^{th}$
- According to RFC 950 it would be $9^{th}$ because in old paper we used to remove first and last subnet group.

## Question
IP address of a block is 100.40.50.153, Subnet Mask of that block is 255.255.255.240, Find the Subnet no. and the subnet ID of the block.

### Solution
- It is a class A address
- bits used for subnetting = 8 + 8 + 4 = 20
- Subnet Id = 100.40.50.144
- Subnet No: 11111111111111111001 + 1
- $4^{th}$ Subnet = 100.00000000.00000000.<u>0011</u> 0000 = 100.0.0.48
- $27^{th}$ Subnet = 100.00000000.0000000<u>1.1010</u> 0000 = 100.0.1.160

# Part 2

## Question
IP address in a block is 100.150.40.50, Subnet Mask = 255.252.0.0
1) 1st host in 2nd subnet
2) 3rd host in 4th subnet
3) 4th host in 3rd subnet

### Solution
- IP is of class A
- Looking subnet Mask we get that 6 bits are used for subnetting
- 2nd subnet = 100.4.0.0
  - 1st host in this subnet = 100.4.0.1
- 4th subnet = 100.12.0.0
  - 3rd host in this subnet = 100.12.0.3
- 3rd subnet = 100.8.0.0
  - 4th host in this subnet = 100.8.0.4

## Question
IP address in a block is 150.150.40.50, Subnet Mask = 255.255.224.0
1) 1st host in 2nd subnet
2) 3rd host in 4th subnet
3) 4th host in 3rd subnet

### Solution
- IP is of class B
- Bits used in subnetting = 3
- 2nd subnet = 150.150.32.0
  - 1st host in this subnet = 150.150.32.1
- 4th subnet = 150.150.96.0
  - 3rd host in this subnet = 150.150.96.3
- 3rd subnet = 150.150.64.0
  - 4th host in this subnet = 150.150.64.4

## Question
IP1 = 140.41.40.50 | IP2 = 140.41.50.40 | IP3 = 140.41.68.40 | Subnet Mask = 255.255.192.0  
Which of the following IP addresses belongs to the same subnet?

### Solution
- IP1 AND Mask = 140.41.0.0
- IP2 AND Mask = 140.41.0.0
- IP3 AND Mask = 140.41.64.0
- Hence, IP1 and IP2 belongs to the same class

## Question
IP1 = 140.41.40.50 | IP2 = 140.41.50.40 | IP3 = 140.41.68.40 | Subnet Mask = 255.255.240.0  
Give the subnet no for given IP

### Solution
- IP1 AND Mask = 140.41.32.0 $\rightarrow$ 0010 = 3rd Subnet
- IP2 AND Mask = 140.41.48.0 $\rightarrow$ 0011 = 4th Subnet
- IP3 AND Mask = 140.41.64.0 $\rightarrow$ 0100 = 5th Subnet

## Question
IP1 = 200.41.40.50 | IP2 = 200.41.40.60 | IP3 = 200.41.40.40 | Subnet Mask = 255.255.255.224
Which host of which subnet?

### Solution
- IP1 AND Mask = 200.41.40.32
  - 50 = 001 10010 $\rightarrow$ 2nd subnet and 18th host
- IP2 AND Mask = 200.41.40.32
  - 60 = 001 11100 $\rightarrow$ 2nd subnet and 28th host
- IP3 AND Mask = 200.41.40.32
  - 40 = 001 01000 $\rightarrow$ 2nd subnet and 8th host
- We have not done +1 in case of host because we have reserved first and last host ID for subnet ID and Broadcast that's why.

## Question
IP1 = 150.41.40.50 | IP2 = 150.41.60.60 | IP3 = 150.41.80.40 | Subnet Mask = 255.255.252.0
Which host of which subnet?

### Solution
- 252 $\rightarrow$ 6 bits in subnetting
- IP1 AND Mask = 150.41.<u>001010</u>00.00110010
  - 11th Subnet and 50th Host
- IP2 AND Mask = 150.41.<u>001111</u>00.60
  - 16th subnet and 60th host
- IP3 AND Mask = 150.41.<u>010100</u>00.40
  - 21st subnet and 40th Host