## TCP Congestion Control
- Main reason of packet loss is congestion.
- If time-out occurs then congestion is high.
  - All packets lost so no duplicate ACK hence congestion is high
- If 3 duplicate ACK comes then congestion is low.
  - Only one packet is lost & we get 3 duplicate ACK so congestion is low.
### How sender will find Wc?
- No way because there are lots of routers in N/W & we can't find capacity of each router at a given time.
- TCP uses AIMD algo to control the growth of Wc with extreme care such that chances of further congestion are least.
- 
## Additive Increase and Multiplicative Decrease
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

