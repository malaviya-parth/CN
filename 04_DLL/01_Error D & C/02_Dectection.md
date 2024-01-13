# Error Detection

- It is based on the concept of block coding.
- In block coding we divide or chop our message into blocks of k bits called dataword.
- We then add 'r' redundant bits to each dataword to form a block of n bits called codeword.
  - n = k + r
- In place of sending dataword we send codeword.
- Let k =2, r =1. So, n = 3.
    - Table
    - |Dataword| Codeword|
      |---|---|
      |00|000|
      |01|011|
      |10|101|
      |11|110|
- The receiver checks the codeword for error detection.
  - Using codeword check in the table above, if the received codeword is 011, then the dataword is 01.
- We can have $2^n$ codewords but only $2^k$ datawords.
  - So, we can have $2^n - 2^k$ codewords which are not datawords. These are called illegal codewords.
  - These illegal codewords are used for error detection.
  - There are stil chances we can receive not expected codeword.
    - Like to send 00, we send 000, but we receive 011 then error will not be detected.