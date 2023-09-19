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
- It can detect all odd number of bit errors(Whether odd parity or even parity systum) but cannot detect even number of bit errors.

