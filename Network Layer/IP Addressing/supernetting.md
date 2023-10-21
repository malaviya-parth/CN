## Background

- Suppose an organisation needs $2^{10}$ addresses the best block one can give is B block but still there will be wastage of $2^{6}\times2^{10}-2^{10}$ addresses = $63 \times 2^{10} \approx 63k$
- Now, to eliminate wastage we have to find 63 more organizations who require $2^{10}$ addresses, which is a hectic task.
- One thing we can do is instead of subnetting we can do is supernetting.

## Supernetting
- Multiple blocks are given to single organisation, instead of dividing single block into multiple organisations.
- Example:
  - If $2^{10}$ addresses are required then give 4 blocks of class C. $\Rightarrow 2^{2} \times 2^{8} \Rightarrow 2^{10}$
  - If $2^{25}$ is required then give 2 blocks of class A.

## Conditions of Supernetting
1. No. of blocks must be power of 2
2. Blocks must be of equal sizes
3. All blocks must be in contiguous fashion
4. $1^{st}$ address of block must be divisible by total number of IP addresses in the block.

## Note:
> If there 4 conditions are not met, then routing will not be possible.

## Question
Given four IP addresses | 200.40.50.0 | 200.40.51.0 | 200.40.52.0 | 200.40.53.0 | If 1000 IP addresses are demanded is it possible with this?

### Solution
- No. of blocks are power of 2 (4)
- All are of equal sizes ($2^{8}$)
- All blocks are continuous
- Condition 4:
  - Addresses: 200.40.00110010.00000000
  - Given address has only 9 zeros at last so it is max divisible by $2^{9}$, Hence condition 4 is no met.
- Supernetting is not possible

## Question
Given four IP addresses | 200.40.48.0 | 200.40.49.0 | 200.40.50.0 | 200.40.51.0 | If 1000 IP addresses are demanded is it possible with this?

### Solution
- No. of blocks are power of 2 (4)
- All are of equal sizes ($2^{8}$)
- All blocks are continuous
- Condition 4:
  - Addresses: 200.40.00110000.00000000
  - Given address has only 12 zeros at last so it is divisible by $2^{10}$.
- Supernetting is possible
- Easy way to check like 10 zeros needed, now in last octet we have 8 zeros. So 2 zeros left to check, if the number written in 3rd octet is divisible by 4 then it is divisible by 4 so at least there will be 2 zeros at back. Hence Given IP will be divisible by $2^{10}$

## Question
Given four IP addresses | 200.40.51.0 | 200.40.52.0 | If 500 IP addresses are demanded is it possible with this?

### Solution 
- Con 1,2,3: are met.
- For Con 4:
  - 51 is not divisible by 2, so 3rd octet don't even have single 0 at end.
- Supernetting is not possible.

## Question
Given 8 consecutive IP addresses blocks with first address being 200.40.56.0, If 2000 IP addresses are demanded is it possible with this?

### Solution
- Con 1,2,3: met
- Con 4:
  - 56 is divisible by 8, so 3rd octet will have atleast 3 zeros at end.
  - Supernetting is possible.

## Question
Given 8 consecutive IP addresses blocks with first address being 140.41.0.0, If $2^{19}$ IP addresses are demanded is it possible with this?

### Solution
- Con 1,2,3: are met
- Con 4:
  - 41 is not divisible by 8.
- No supernetting possible.

## Question
Given IP 200.40.128.0 - 200.40.255.0, is it possible for the organisation to have these blocks for $2^{15}$ addresses?

### Solution
- Con 1,2,3: are met
- Con 4:
  - 128 is having 7 zeros at end.
- So, supernetting is possible.

## Routing in Supernetting
- Here, we have supernet mask for the routing purpose.
- In case of supernetting we fill zeros in places which we occupied.
- Example:
  - Class C Net Mask: 255.255.255.0
  - If 8 blocks of Class C are used for supernetting
  - Supernet Mask: 255.255.248.0
- While subnet Mask was used by Site Routers, but supernet Mask are used by the internet routers.
- Example:
  - 200.40.36.0 - 200.40.39.255, 4 blocks
  - Supernet Mask: 255.255.252.0
  - Any address from range given to supernet mask will yeild 200.40.36.0
- This yeild of 36, or it can be any ither but it will be multiple of 4 and so we required first block to have address divisible by 4, as it work as NetID for the organisation.

## Question
Given Supernet mask is 255.255.240.0, find the number of IP addresses.

### Solution
- Super net mask and it can only be of class C
- Now it is converted from 255 to 240, we have 4 0s at the end.
- Number of IP addresses = $2^{8} \times 2^{4} \rightarrow 2^{12}$ addresses.
- We can also do with concept of **Subnet**
  - We have 16+4 = 20 1s
  - Left 12 0s
  - No. of Host = $2^{12}$