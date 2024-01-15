# Hamming Distance

- Hamming distance between 2 binary strings of same size is the number of differences between corresponding bits.
- It is denoted by d(x,y)
  - d(101,100) = 1
  - d(100,011) = 3
  - d(101101,110) = d(101101,000110) = 4
- Hamming distance can be found by applying X-OR operations on 2 words and count no of 1s in the result.
- If we have more than two words then hamming distance will be min HD b/w all the possible pairs
  - d(00000,01011,11110,10101)
    - = d(00000,01011) = 3
    - = d(00000,11110) = 4
    - = d(00000,10101) = 3
    - = d(01011,11110) = 3
    - = d(01011,10101) = 4
    - = d(11110,10101) = 3
  - Minimum Hamming Distance = 3
- Number of Possible pairs to check = $\binom{n}{2}$

## Minimum Hamming Distance to detect 't' bit errors

- We can detect 't' bit errors if minimum hamming distance is atleast t+1.