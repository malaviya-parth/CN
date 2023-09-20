# CheckSum

- This error detection scheme is also based on concept of Data redundancy i.e. adding some error bits in data.

**Basic Idea**
- We want to send 5, 4-bits data like 7,11,12,0,6.
- Along with these numbers we will send a checksum which is sum of all these numbers with negative sign.
- Receiver will add all these numbers and if sum is zero then no error else error.
- Example: 7,11,12,0,6 $\rightarrow$ 7+11+12+0+6 = 36 $\rightarrow$ -36
- Problem with this scheme is 36 require 6 bits to represent but we have only 4 bits.
  - So, we use folding method where we fold the bits and add them.
  - 36 = 0010 0100 $\rightarrow$ 0010 + 0100 = 0110 = 6
- To show negative sign we use 1's complement.
  - 6 = 0110 $\rightarrow$ 1001 = 9
  - So, 9 is the checksum.
- Receiver will receive 7,11,12,0,6,9 and add them.
  - 7+11+12+0+6+9 = 45 $\rightarrow$ 101101, apply folding $\rightarrow$ 1101 + 0010 = 1111 = 15, Now take 1's complement $\rightarrow$ 0000 = 0, hence no error.

**Disadvantage**
- If 2 numbers are interchanged then also checksum will be same.
- If we have 1 bit error in 2 different number at same position then also checksum will be same.
  - Example: 7,11,12,0,6
    - 11 = 1011 but sent 1111 and 12 = 1100 but sent 1000
    - Changes will +4 and -4 so checksum will be same.
    - No error will be detected.
- Calculation is very time consuming.