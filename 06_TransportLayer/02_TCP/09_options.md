## Options in TCP header
1. Time Stamp:
   - Used to extend sequence No. when (WaitAroundTime < LifeTime)
2. Window Size Extension:
   - Used to extend window size field.
   - WS has 16 bits so max window size can be 64KB
   - But if buffer larger than 64KB is available then we can use this option.
   - It's 14 bit field so maximumm window size advertized can be of 30 bits = 1GB.
   - This is also called as Scale Factor.
     - If 512KB window size, 19 bits used then scale factor is 3.
3. Parameter Negotiation:
   - Lots of parameter but one such parameter discussed is MSS.
   - Time of connection is discussed also
4. Padding:
   - 0s added to make options multiple of 4Bytes.