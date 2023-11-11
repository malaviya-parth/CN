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