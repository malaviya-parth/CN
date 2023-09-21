# Sliding Window Protocol

## Numerical Example
Frame Size = 1000 bits, Tp = 10 ms, B/W = 1 Mbps. 
1. Find percentage of utilization of link using stop & wait protocol. 
2. Improvement in percentage utilization if 15 frames are sent before receiving ACK. 
3. How many frames must be sent by the sender so that it never remains ideal? 
4. How many bits are needed as overhead in header of each frame for sequence number
   1. If $\eta$ = 100%
   2. Maximally packed link

### Solution
1. TT = 1000/1000000 = 1 ms  
    - Efficiency = 1/(1 + 2*10) = 1/21 = 4.76%  
2. If 15 frames are sent before receiving ACK, then efficiency = 15/(15 + 2*10) = 15/35 = 42.85%  
   - Improvement = 42.85 - 4.76 = 38.09%
3. Sender never remains means efficiency = 100%  
    - 1 = x*1/(1 + 2*10)
    - x = 21
4. Bits are calculated on the basis of number of frames sent
   1. For 21 frames, 5 bits are needed
   2. Capacity = 1 Mbps * 10 ms = 10000 bits  
      - Number of frames = 10000/1000 = 10
      - Bits needed = 4 bits

## Sliding Window Protocol
- Sender will send window(buffer) of packets & waits for ACK from receiver
- Size of window can be from 1 to $min(1+2a,2^n)$ where n is the number of bits allowed in the trailer of the frame.
- If size of window is 1 we get stop & wait protocol.
- Concept of pipelining is used to improve efficiency i.e. in place of sending 1 frame sender will send multiple frames & then it waits for ACK.
- Window slides one position to the right as soon as ACK for the first frame is received.
![Alt text](./Assests/image2.png?raw=true "Title")

### Summary
To geet maximum efficiency window size should be 1 + 2a, where a = $\frac{T_p}{T_t}$  
For this we need to have 1 + 2a sequence numbers.  
Number of bits required for sequence number = $\lceil log_2(1 + 2a) \rceil$  

## Question
TT = 1 sec, TP = 5 sec
1. Window size for maximum efficiency
2. Sequence number bits required for maximum efficiency
3. If 3 bits are used for sequence number, what is the efficiency of the link

### Solution
1. For maximum efficiency window size = 1 + 2a = 1 + 2*5 = 11
2. Sequence number bits required = $\lceil log_2(1 + 2a) \rceil$ = $\lceil log_2(11) \rceil$ = 4
3. Maximum we can send is 11 but we are sending only 8 frames.  
   - Efficiency = 8/11 = 72.72%

> Efficiency = $\frac{Actual \; window \; size}{Maximum \; window \; size}$   
>   
> Maximum window size = 1 + 2a  

## GATE 2003
Host A is sending data to HostB. Sender & receiver window size = 5 packets. Packet Size = 1000 bytes, Transmission time = 50 $\mu$s, Propagation time = 200 $\mu$s. Size of ACK is negligible. Maximum Achievable throughput?

### Solution
B/W = 1000 $\times$ 8/50 $\mu$s = 160 Mbps  
Efficiency = $\frac{Actual \; window \; size}{Maximum \; window \; size}$ = $\frac{5}{1 + 2a}$ = $\frac{5}{9}$ = 55.55%
Throughput = 55.55% $\times$ 160 Mbps = 88.88 Mbps = 11.11 MBps

## GATE 2006
Station A sending 32 bytes packet to station B using sliding window protocol. The round trip delay between A & B is 80 ms & the bottleneck bandwidth on the path between A & B is 128 kbps. What is the optimal window size that A should use?

### Solution
RTT = 80 ms = 2TP  
TT = 32 $\times$ 8/128 kbps = 2 ms  
TP = 80/2 = 40 ms
Window Size = 1 + 2a = 1 + 2*40/2 = 41

## GATE 2007
Distance beetween 2 stations M & N is L km, frame size = K bits. Propagation speed per km is 't' sec. R bits/sec is the channel capacity. Minimum number of bits required for the sequence number field to achieve 100% utilization?

### Solution
For maximum efficiency, Actual Window Size = 1 + 2a  
a = $\frac{TP}{TT}$ = $\frac{(Lt)R}{K}$  
Actual Window Size = 1 + 2a = 1 + 2$\frac{(Lt)R}{K}$  
Number of bits required = $\lceil log_2(1 + 2\frac{(Lt)R}{K}) \rceil$