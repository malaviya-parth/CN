# Hamming Code

- It is an error correcting code.
- It is a type of Linear Block Code.
- The main task in error correcting code is to find the position of error, then we just need to complement the bit at that position.
- This scheme is also based on the concept of redundancy.
- Itt can correct single bit error.

## How many Redundant bits in Hamming Code?
- $2^k \geq n + k + 1$
- k = number of redundant bits
- n = number of data bits
  - Example if n = 4, then k =3
  - If n = 6, then k = 4
- If D.W. = 4 bits then C.W. = 7 bits, 3 redundant bits.

## Where to add these redundant bits?
- Redundant bits are added at the positions which are powers of 2.
- If n = 4, D.W. = 1011, then
  - C.W. = 1 0 1 _ 1 _ _
  - Here, P1,P2,P3 are needed to be calculated
  - D7(7=4+2+1) = P4 + P2 + P1, D6(6=4+2) = P4 + P2, D5(5=4+1) = P4 + P1, D3 = P2 + P1
  - P1 = _ D7 D5 D3 $\rightarrow$ _ 1 1 1 $\rightarrow$ 1 1 1 1(Even parity) = 1
  - P2 = _ D7 D6 D3 $\rightarrow$ _ 1 0 1 $\rightarrow$ 0 1 0 1(Even parity) = 0
  - P4 = _ D7 D6 D5 $\rightarrow$ _ 1 0 1 $\rightarrow$ 0 1 0 1(Even parity) = 0
- C.W. = 1 0 1 0 1 0 1

## Question
- Given codeword = 1000101, find whether codeword is valid or not. If not then find the position of error and corresponding valid codeword.

### Solution
- C.W. = 1 0 0 0 1 0 1
- D7 = P4 + P2 + P1, D6 = P4 + P2, D5 = P4 + P1, D3 = P2 + P1
  - P1 = _ D7 D5 D3 $\rightarrow$ _ 1 0 1 $\rightarrow$ 0 1 0 1(Even parity) = 0
  - P2 = _ D7 D6 D3 $\rightarrow$ _ 1 0 1 $\rightarrow$ 0 1 0 1(Even parity) = 0
  - P4 = _ D7 D6 D5 $\rightarrow$ _ 1 0 0 $\rightarrow$ 1 1 0 0(Even parity) = 1
- Corresponding bits in C.W. are P1 = 1, P2 = 0, P4 = 1
  - Error codes C1 = 1 (P1), C2 = 0 (P2), C4 = 1 (P4)
  - Error position = C4C2C1 = 101 = 5
- Valid codeword = 1010101
- Dataword = 1011

## Question
- A 12 bit hamming code whose Hex value is 0xE4F arrives at receiver. What was the original value in hex? (Assume only one bit error & Numbering from left to right)

### Solution
- 0xE4F = 1110 0100 1111
- P8 = 0, P4 = 0, P2 = 0, P1 = 1
- Error Codes = 0011 $\orplus$ 0001 = 0010
- Error Position = 0010 = 2
- Valid Codeword = 1010 0100 1111 = 0xA4F

## Question
- A 8 bit dataword 00111001, check bits stored would be 0111. Suppose when the word is read from the memory the check bits are calculated to be 1101. What is the correct dataword read from the memory?

### Solution
- Look given is 8 bit dataword and 4 bit check bits.
- So, it is a question related to hamming codes.
- Error codes = 1101 $\orplus$ 0111 = 1010
- Error is in position 1010 = 10.
- Valid dataword = 00011001

## GATE 2021
- Assume that 12 bit hammimg code of 8 bit dataword. Databits = 110x0101, Checkbits = y010. Values of x and y = ?

### Solution
- Codeword = 110xy0100110
- P8 = y 1 1 0 x, P4 = 0 1 0 1 0, P2 = 1 1 0 0 1 1, P1 = 0 1 x 0 0 1
- Even parity, so from P8 x=y, from P1 x=0, $\therefore$ y=0