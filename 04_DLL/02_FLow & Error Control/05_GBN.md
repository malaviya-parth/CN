# Goback-N ARQ

- In Goback-N size of sender sliding window will be N. For e.g. in GB5, sender window size will be 5.
- Size of receiver sliding window will be only 1. For eg in GB5, GB10, etc. receiver window size will be 1.
- Assumption is that all frames are numbered from 0 to N-1 are received in the same order they are sent.

## Working 
- Suppose it is GB3
- Senders sends 3 frames and waits for ACK.
- Receiver receives first frame, then window slides to next frame. It receives second frame, then window slides to next frame. It receives third frame, then window slides to next frame. As soon as receiver receives frame it sends respective ACK.
- After sender receives ACK, it slides the window to the next of last frame sent.
- Example GB-3
   - Sender has frames 123456 to send
   - Initial window |123|456
   - Sender sends fame 123
   - Receiver receives 1 and sends ACK
   - Now Sender window will be 1|234|56
   - Receiver receives packet 2 and sends ACK
   - Now Sender window will be 12|345|6
   - Now packet 3 is lost, receiver still receives packet 45 but will be discarded as those are not the required packets.
   - Timeout occurs at sender side, sender again sends the window frames 345.
   - Like this the process occurs
- Also, sender sets a timer for the left most frame in the window. If it doesn't receive ACK for that frame, it will retransmit all the frames in the window. It assumes frames will be received in order.
- A timer is maintained at receiver side as well, like if the last packet sent by sender is lost then after the timer expires receiver will send cumulative of only those packets which are received.
- For Proper Impelementation Sender Timer should be greater than Receiver Timer.

## Case 1:
- If frames are unorderedly received at receiver side
-  If frames sent are 0,1,2 and receiver receives frames as 2,0,1.
   - As initially receiver was waiting for frame 0, so it will discard frame 2, later frame 0 comes so it accepts, similarly frame 1 comes so it accepts and sends ACK for frame 0,1.
   - Sender hence tis time slides the window accroding to the ACK received.
   - Next window = $2,0_1,1_1$
- If frames sent are 0,1,2 and received in order 1,0,2.
   - Next window at sender side = $1,2,0_1$

## Why we call it as Goback-N?
When the timer expires, the sender goes back to the left most frame which is N frames back and retransmits all the frames. Hence it is called as Goback-N.

## Efficiency
- Efficiency = $\frac{Actual\;Window\;Size}{Maximum\;Window\;Size}$ = $\frac{N}{1+2a}$ where a is the round trip time.
- Example: GB3, TT = 1 ms, Tp = 4 ms
  - Efficiency = $\frac{3}{1+2*4/1}$ = 0.33

## Question
If header of frame allow 'm' bit overhead for sequence no. then what can be maximum value of N in GobackN?

### Solution
- m bit overhead allowed so sequence no. can be 0 to $2^m-1$
- Suppose m =2, then we have window size 0,1,2,3
  - Now if 0,1,2,3 sent by sender but the ACK sent by receiver is lost, then sender will retransmit all the frames.
  - While retransmitting, it will send 0,1,2,3 again. This time the window at receiver side will be at $0_1$ and it will accept this 0 which will create duplicacy.
  - Hence, we can't implement GobackN where N = $2^m$
- Hence, maximum value of N = $2^m-1$   
  - Whenever ACK is lost if we have an extra sequence no. then receiver will discard the duplicate frame.

## Note:
Available sequence Number $\geq$ Sender Window Size + Receiver Window Size

## Question
For GBN what is the minimum no. of sequence no. needed? Also find minimum number of bits needed in header of each frame for sequence no.

### Solution
- Minimum no. of sequence no. needed = Sender Window Size + Receiver Window Size
- Minimum number of bits needed in header of each frame for sequence no. = $\lceil log_2(Sender\;Window\;Size + Receiver\;Window\;Size)\rceil$

## Question
If unique sequence numbers are N, then find maximum size of sender & receiver window in GBN.

### Solution
- Maximum size of sender window = N-1
- Maximum size of receiver window = 1

## Question
If header allows overhead of 'm' bits then find maximum size of sender & receiver window in GBN.

### Solution
- Maximum size of sender window = $2^m-1$
- Maximum size of receiver window = 1

## GATE 2004
Transmitter window Size = N, Receiver Window Size = m. Find minimum number of distinct sequence number required tto ensure correct operation of ARQ scheme.

### Solution
- Minimum number of distinct sequence number required = N+m

## GATE 2004
B/w = 20kbps, Tp = 400 ms, GB10, Frame Size = 100 Bytes. What is the maximum data rate possible?

### Solution
Maximum Data Rate possible = Throughput  
Efficiency = $\frac{N}{1+2a}$
  - TT = (100*8)/20*1000 = 40 ms
  - Efficiency = $\frac{10}{1+2*400*10^{-3}/40*10^{-3}}$ = 47.6%
Throughput = Efficiency * Bandwidth = 47.6% * 20 kbps = 9.52 kbps

## GATE 2008
1 Mbps satelite link connects 2 ground stations. B/W = 1 Mbps, Distance = 36,504 Km, Speed = 3 $\times 10^8$, GobackN with window size 127 is used. Channel utilization = 25%. What is the packet size?

### Solution
Station are not connected directly they are connected via satellite.  
Propogation delay for this will be two times as one for uplink and one for downlink.  
Propagation Delay = 2* $\frac{Distance}{Speed}$ = 2* $\frac{36,504}{3 \times 10^8}$ = 243360 $\mu$ s = 243.36 ms
Efficiency = $\frac{N}{1+2a}$ = 25%  
  - 0.25 = $\frac{127}{1+2a}$
  - a = 507/2 = 253.5 ms
- Tp/Tt = 253.5
- Tt = Tp/253.5 = 243.36/253.5 = 0.96 ms
- Packet Size = 1 Mbps * 0.96 ms = 960 bits = 120 bytes

## GATE 2006
Station A needs to send 9 packets to station B using GB-N(N=3). If every 5th packet is lost then how many packets are actually sent by A?

### Solution
- The answer is 16
- |123|456789, 123 will be sent.
- ACK of 1 received then 4 will be sent. New window 1|234|56789. Packets sent = 4
- ACK of 2 received then 5 will be sent. New window 12|345|6789. Packets sent = 5
- ACK of 3 received then 6 will be sent. New window 123|456|789. Packets sent = 6
- ACK of 4 received then 7 will be sent. New window 1234|567|89. Packets sent = 7
- ACK of 5 won't be received as 5th packet will be lost.
- Timeout occurs, this window will send 567. Packets sent = 10
- ACK of 5 received then 8 will be sent. New window 12345|678|9. Packets sent = 11
- ACK of 6 received then 9 will be sent. New window 123456|789|. Packets sent = 12
- ACK of 7 won't be received as it is 10th packet send, multiple of 5, so will be lost.
- Timeout occurs, this window will send 789. Packets sent = 15.
- ACK of 7 received. New window 1234567|89|.
- ACK of 8 received. New window 12345678|9|.
- ACK of 9 won't be received as it is the 15th packet so will be lost.
- Timeout occurs, this window will send 9. Packets sent = 16.
- ACK of 9 will be received.
- Process over, total packets sent = 16.

### GATE 2015
Distance is 8000 km, B/W =500 Mbps, Speed = 4 * $10^6$ m/s, GBN protocol is used with packet size = $10^7$ bits. Network is to be used to it's full capacity. Minimum Size in bits of the sequence no. field??

### Solution
- Propogation Delay = $\frac{Distance}{Speed}$ = $\frac{8000}{4 \times 10^6}$ = 2 s
- Transmission Time = $\frac{Packet\;Size}{Bandwidth}$ = $\frac{10^7}{500 \times 10^6}$ = 0.02 s
- a = $\frac{Propogation\;Delay}{Transmission\;Time}$ = $\frac{2}{0.02}$ = 100
- Full Capacity is asked so Efficiency = 1
  - 1 = $\frac{N}{1+2a}$
  - N = 1+2a
  - N = 201
- So, 201 window size at sender side and 1 at receiver side.
- Minimum Size in bits of the sequence no. field = $\lceil log_2(202)\rceil$ = 8
