# Linear Block Codes

- If XOR of 2 valid codewords is a valid codeword then we can say that set of codewords are linear block codes.
- Today almost all error detecting codes are linear block codes $\because$ Non-linear block codes are difficult to implement.
- It has a special property that minimum hamming distance is the minimum number of 1s in a non-zero valid codeword.

## Examples

- Simple parity check code
- 2D parity check code
- Cyclic codes
- checksum

## Simple Parity Check Code

- One extra bit called parity bit is added to the data word to make total number of 1s in the codeowrd as even (Some implementations use odd parity).
- Minimum hamming distance is 2, so it can detect single bit error.
- It can detect all odd number of bit errors(Whether odd parity or even parity system) but cannot detect even number of bit errors.

## 2D Parity check Code

- Datawords are arranged in a matrix and parity bits are added to each row and column.
- Minimum hamming distance is 3, so it can detect single bit error and can correct single bit error.
- It can detect all odd number of bit errors but cannot detect even number of bit errors.
- It can detect upto 3 bit errors but cannot correct 3 bit errors.
- Suppose we want to send 4 datawords of 7 bits each, then we can arrange them in a matrix of 4 rows and 7 columns. 
```
1 0 1 1 0 1 0
1 1 1 1 1 0 1
1 0 1 0 0 0 1
1 0 1 1 0 1 1
```
code is used to represent this code.
- After adding parity bits to each row and column, the code becomes
```
1 0 1 1 0 1 0 0
1 1 1 1 1 0 1 0
1 0 1 0 0 0 1 1
1 0 1 1 0 1 1 1
0 1 0 1 1 0 1 0
```

**Disadvantage**
- If there is error in parity bits then it cannot be detected.

## GATE 2008
- Even paity scheme 4 datawords each of 7 bits d0 and r4 are parity column and row respectively. Minimum number of errors?
```math
|   |d7|d6|d5|d4|d3|d2|d1|d0|
|r0 |0 |1 |0 |1 |0 |0 |1 |1 |
|r1 |1 |1 |0 |0 |1 |1 |1 |0 |
|r2 |0 |0 |0 |1 |0 |1 |0 |0 |
|r3 |0 |1 |1 |0 |1 |0 |1 |0 |
|r4 |1 |1 |0 |0 |0 |1 |1 |0 |
```
- There is error in d5,d2,d0,r1.
- Taking intersection we get errors in 2 data bits and one parity bit[r1 d0].
- Think it of other way, like we can have error in 1 data bit[r1 d5] and 2 parity bits.
- Also one way is we can have error in 3 parity bits[d5r4, d2r4, d0r1].
- Anyhow minimum number of errors is 3.