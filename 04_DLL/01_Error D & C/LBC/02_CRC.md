# Cyclic Codes

- It is a type of Linear Block Code in which if a codeword is cyclically rotated left or right then we get a valid codeword only.

```math
D.W.   C.W.
 00    000
 01    001
 10    010
 11    100
```
- Most widely used cyclic code is CRC(Cyclic Redundancy Check).

## Cyclic Redundancy Check (CRC)

- Block Coding $\rightarrow$ Linear block code $\rightarrow$ Cyclic code $\rightarrow$ CRC.
- Given a dataword of $n$ bits, Divisor of $k$ bits
- Append $k-1$ zeros to dataword and divide it by divisor.
- Remainder is called CRC.
- Code word = Dataword appended by Remainder.
- C.W. = n + k - 1 bits.

## D.W. = 1001, Divisor = 1011 Find C.W.

- Append 3 zeros to D.W. $\rightarrow$ 1001000
- Divide 1001000 by 1011 $\rightarrow$ 1001000|1011
- While dividing simply do XOR operation.
- Remainder = 110
- C.W. = 1001110

## Divisor = 1011, D.W. = 10110101101101 Find C.W.

- Remainder = 1 $\rightarrow$ 001
- C.W. = 10110101101101001

---
- After receiver gets the C.W. it divides it by divisor and if remainder is 0 then no error else error.
- At receiver side remainder is called Syndrome.

## Is CRC scheme perfect?
- Look Received Codeword = Sent Codeword + error
- Notation format
  - $R(x)$ = $C(x)$ + $E(x)$
  - $\frac{R(x)}{G(x)}$ = $\frac{C(x)}{G(x)} + \frac{E(x)}{G(x)}$
- For message to be error free LHS must be zero which means both the term in RHS must be zero.
  - Now Dataword gives zero remainder when divided by G(x) $\rightarrow$ $C(x)$ = $D(x)G(x)$
  - $E(x)$ should also give zero remainder when divided by G(x), Ideally if no error then $E(x)$ = 0, but if $E(x) \neq$ 0 and is divisible by G(x) then also $\frac{E(x)}{G(x)}$ = 0. Hence, in such case error is not detected.
- $\therefore$ CRC is not perfect.

## Polynomial Notation

- 101101 $\rightarrow$ $x^5 + x^3 + x^2 + 1$
  - If Degree 5 then 6 bits.

## Question
- DW = $x^3 + 1$, Divisor = $x^3 + x + 1$, Find CW.
- New Word = $x^3 + 1$*$x^3$ = $x^6 + x^3$ (Multiplied with $x^3$ because degree of divisor is 3)
- Remainder = $x^6 + x^3$|($x^3 + x + 1$) = $x^2 + x$ (Keep on dividing until inner degree is more than divisor's degree)

## How to choose Divisor

- Except for last bit error, single bit error gives even number.
- Example for a number 101010101
  - last 3rd bit is wrong then error will be 100 = 4
  - last 5th bit is wrong then error will be 10 = 16
  - last bit is wrong then error will be 1 = 1

- As always coming an even number so we should select divisor an odd number[last bit should be 1] so that it can detect all single bit error.
- To detect odd number of errors (x+1) must be factor of divisor.
  - Like if error is at 3 places[odd] then error will contain three 1's. Hence it's polynomia; will have odd number of terms. So, x+1 will not be factor for it.
  - So if we design divisor in such a way that x+1 is factor of it then it will always detect error as odd error polynomial is not divisible by x+1.    

## Characteristics of Divisor
- It must have atleast 2 terms (Single term means divisor is an even no. & single bit error can't be detected)
- Co-efficient of $x^1$ must be 1 (So that divisor becomes an odd number & all single bit errors can be detected)
- Must be a multiple of $x + 1$. (So that odd number of errors can be detected)

## GATE 2005
- Message m = 1010001101, Divisor = $x^5 + x^4 + x^2 + 1$, Find C.W.

### Solution
- Append 5 zeros to message $\rightarrow$ 101000110100000
- Divisor = $x^5 + x^4 + x^2 + 1$ $\rightarrow$ 110101
- Remainder = 01110
- C.W. = 101000110101110

## GATE 2007
- Message m = 11001001, Polynomial = $x^3 + 1$, Find C.W.

### Solution
- Append 3 zeros to message $\rightarrow$ 11001001000
- Divisor = $x^3 + 1$ $\rightarrow$ 1001
- Remainder = 011
- C.W. = 11001001011