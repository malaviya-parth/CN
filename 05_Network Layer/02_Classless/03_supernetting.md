## Conditions
1. No. of blocks must be power of 2
2. Equal Size block
3. contiguous blocks
4. 1st address must be divisible by total no. of IP addresses

## Question
4 Blocks are aggregated to make a single N/W. Find supernet mask & supernet ID of the aggregated N/W.  
IPs: 100.40.36.0/24, 100.40.37.0/24, 100.40.38.0/24, 100.40.39.0/24

### Solution
- Condition 1,2,3 are met
- Also, first block address, 100.40.00100100.0 10 zeros so divisible by $2^{10}$ number of addresses.(total number of IPs), Hence, supernetting is possible.
- SuperNet ID: 100.40.36.0/22
- SuperNet Mask: 255.255.252.0

## Question
16 Blocks are aggregated to make a single N/W. Find supernet mask & supernet ID of the aggregated N/W.  
IPs: 100.40.36.0/24, 100.40.37.0/24, 100.40.38.0/24, ..., 100.40.51.0/24

### Solution
- Condition 1,2,3 are met
- Block 1 is not divisible by total IPs, so not possible.  

## Question (⭐⭐⭐)
Given blocks: 100.40.32.0/24, 100.40.33.0/25. 100.40.33.128/25. Is aggregation possible in this?

### Solution
- Directly looking it might seem like aggregation is not possible.
- But we can aggregate this like below:
- First aggregate /25 blocks
  - Supernet ID: 100.40.33.0/24
  - Supernet Mask: 255.255.255.0
- Now, aggregate the new supernet with first block.
  - Supernet ID: 100.40.32.0/23
  - Supernet Mask: 255.255.254.0
- This is how suppernetting is done, similar to the concept of VLSM in subnetting.

## Question
Given blocks: 100.40.32.0/24, 100.40.33.0/24, 100.40.34.0/24, 100.40.35.0/25, 100.40.35.128/25,

### Solution
- SuperNet ID1: 100.40.35.0/24
- SuperNet ID2: 100.40.32.0/22

## Question
Given BLocks: 100.16.0.0/17, 100.16.128.0/18, 100.16.192.0/19, 100.16.224.0/20, 100.16.240.0/20

### Solution
- SuperNet ID1: 100.16.224.0/19
- SuperNet ID2: 100.16.192.0/18
- SuperNet ID3: 100.16.128.0/17
- SuperNet ID4: 100.16.0.0/16
- SuperNet Mask: 255.255.0.0