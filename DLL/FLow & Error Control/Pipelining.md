# Concept of Pipelining

- We know that for first packet it takes tt + tp time, and rest arrives at +tt interval of time. This is all because of the pipelining concept.

## Example 

```mermaid
graph LR;
    A[Sender] --> B(X)
    B --> C(X)
    C --> D[Receiver]
```
- $Tt_s = 2ms, Tp_s = 5ms, Tt_{r1} = 5ms , Tp_{r1} = 10ms, Tt_{r2} = 4ms Tp_{r2} = 8ms$

### Solution
Time for first packet = 5 + 2 + 5 + 10 + 4 + 8 = 34ms  
Time for second packet = 34 + 2 = 36ms  
Time for third packet = 36 + 2 = 38ms  
So on...

## GATE 2012
S is connected to R with two Routers in between. Each device has 100 km distance with it's neighbour. Speed of signal $10^8$ m/s, B/W = 1Mbps, File Size = $10^6$ bits. Which is broken in 1000 packets each of size 1000 bits. Find total sum of Tt & Tp in transmitting the entire file from S to R.

### Solution
$Tt = \frac{10^3}{10^6} = 1 ms$, $Tp = \frac{10^5}{10^8} = 1ms$  
Time for the first packet to reach the destination = 1 + 1 + 1 + 1 + 1 + 1 = 6ms  
Time for second packet to reach the destination = 6 + 1 = 7ms  
Time for entire file to reach destination = 6 + 1*(999) = 1005ms