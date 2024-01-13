## TCP Congestion Control
- Main reason of packet loss is congestion.
- If time-out occurs then congestion is high.
  - All packets lost so no duplicate ACK hence congestion is high
- If 3 duplicate ACK comes then congestion is low.
  - Only one packet is lost & we get 3 duplicate ACK so congestion is low.
### How sender will find Wc?
- No way because there are lots of routers in N/W & we can't find capacity of each router at a given time.
- TCP uses AIMD algo to control the growth of Wc with extreme care such that chances of further congestion are least.

---
- Let capacity of receiver is $W_{R}$ & capacity of Network is $W_{C}$.
- $W_{S} = min(W_{C},W_{R})$
- Wr is known to sender because in each packet receiver send amount of space available in it's buffer(Wr).

## Question
Buffer Size at receiver = 5KB  
Unprocessed data at receiver = 1KB  
Congestion Window Size = 2KB  
Find W.S. choosen by sender

### Solution
- Ws = min(4,2) = 2KB

## GATE 2005
On a TCP connection, current congestion window size is Congestion Window = 4KB. The window advertised by the receiver is Advertise Window = 6KB. The last byte sent by the sender is LastByteSent = 10240 and the last byte acknowledged by the receiver is LastByteAcked = 8192. The current window size at the sender is
1. 2048 bytes
2. 4096 bytes
3. 6144 bytes
4. 8192 bytes

### Solution
- Window Size is simple min(4,6) = 4 KB
- Current Window Size = 4096 bytes
- Last byte sent - Last byte Acked = 10240 - 8192 = 2048 bytes = 2 KB
- More data that can be sent by the sender will be just 2 KB, as 2 KB unacknowledged data is left.

## Additive Increase Multiplicative Decrease
- During connection establishment receiver sent Window Size = 8 KB & for simplicity we assume that always it's size remains fixed i.e. at receiver side always 8 KB space is available.
- Hence Wr becomes 8 KB & let MSS = 1 KB
- Initially we assume Wc = 1 KB [ Equal to size of 1MSS]
- Hence, Wr = 8 MSS, Wc = 1 MSS, Ws = min(Wr,Wc) = 1 MSS
- Now, first sender will send 1 MSS data and wait for acknowledgement.
- If, ack comes now sender will increase sending window size slowly say makes it 2 MSS.
- If ACK goes on coming properly, window size updates to 4,8,16,32...
- The value increases upto threshold,
  - Threshold = Wr/2 = 8/2 = 4 MSS
- So window size will be 1,2,4,5,6,...
  - 1,2,4 is slow start phase
  - 4,5,6 is congestion Avoidance phase (additive increase)
- In Congestion avoidance phase Wc increases linearly till time out occur or it reaches Wr.
  - Window Size increases 4,5,6,7,8,8,8,...
- Till now we don't consider case of time out i.e. what if packet is lost or it's ACK is lost [unsuccessful transmission]
- In this case the AIMD enters 3rd phase called congestion detection [multiplicative decrease]
- Hence AIMD has 3 phases
  1. Slow start [ Exponential increase till Wr/2 ]
  2. Congestion Avoidance [ Additivie increase till Wr or TimeOut or 3 duplicate ACK ]
  3. Congestion detection [ multiplicative decrease ]
### Congestion Detection
- If Congestion Detection is due to Time Out,
  - New Threshold = Wc/2
  - Slow start phase is started
- If Congestion Detection is due to 3 Dup ACKs
  - New Threshold = Wc/2
  - Congestion avoidance phase starts from new threshold only.

## Question
After how many RTT Wc = Wr? Wr = 8 KB, MSS = 1 KB

### Solution
- Wr = 8 MSS
- Threshold = Wr/2 = 4 MSS
- After 1RTT Wc = 2 MSS
- After 2RTT Wc = 4 MSS
- After 3RTT Wc = 5 MSS
- After 4RTT Wc = 6 MSS
- After 5RTT Wc = 7 MSS
- After 6RTT Wc = 8 MSS
- Therefore, After 6 RTTs Wc = Wr.

## Question
Wr = 16 KB, MSS = 1 KB. After how many RTT Wc becomes Wr i.e. Wc will have max capacity.

### Solution
- Wr = 16 MSS
- Threshold = 8 MSS
- Wc = 1,2,4,8,9,10,11,12,13,14,15,16
- Therefore after 11 RTTs.

## Question
Wr = 64 KB, MSS = 1 KB
1. When Wc = 34 KB, Time Out occurred
2. When Wc = 20 KB, 3 duplicate ACK arrived
3. When Wc = 12 KB, Time Out occurred
4. When Wc = 64 KB, Time Out occurred
5. When Wc = 32 KB, 3 duplicate ACK arrived
6. When Wc = 17 KB, Time Out occurred

### Solution
- Threshold = 32 MSS
- Wc = 1,2,4,8,16,32,33,34 (Con 1 hit)
1. Threshold = 17 MSS
   - 1,2,4,8,16,17,18,19,20 (Con 2 hit)
2. Threshold = 10 MSS
   - 10,11,12 (Con 3 hit)
3. Threshold = 6 MSS
   - 1,2,4,6,7,8,9,10,...,62,63,64 (Con 4 hit)
4. Threshold = 32 MSS
   - 1,2,4,8,16,32 (Con 5 hit)
5. Threshold = 16 MSS
   - 16,17 (Con 6 hit)
6. Threshoold = 8 MSS
   - 1,2,4,8,9,10,11,...,62,63,64,64,64,...

## GATE 2012
Consider an instance of TCP's Additive Increase Multiplicative Decrease(AIMD) algorithm where the window size at the start of the slow start phase is 2 MSS and the threshold at the start of the first transmission is 8 MSS. Assume that a time out occurs during the fifth transmission. Find the congestion window size at the end of the tenth transmission.
1. 8 MSS
2. 14 MSS
3. 7 MSS
4. 12 MSS

### Solution
- 2,4,8,9,10,2,4,5,6,7
- Hence the window size at end of tenth transmission is 7 MSS
- Here it is asked after transmission, if it asked after tenth RTT then it will be 8 MSS.

## GATE 2014
Let the size of congestion window of a TCP connection be 32 KB when a timeout occurs. The round trip of the connection is 100 ms and the maximum segment size used is 2 KB. The time taken (in ms) by the TCP connection to get back to 32 KB congestion window is __.
1. 1100 to 1300
2. 800 to 1000
3. 1400 to 1600
4. 1500 to 1700

### Solution
- MSS = 2 KB
- Time out at 16 MSS
- Threshold = 8 MSS
- Again as Time Out occured so we need to do slow start
- 1,2,4,8,9,10,11,12,13,14,15,16
- Total it took 11 RTT to reach 16 MSS = 32 KB
- Therefore time taken = 1100 to 1300 ms