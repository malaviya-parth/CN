## Congestion Control
- Internet can be considered as a Queue of packets, where transmitting nodes are constantly adding packets and some of them are removing packets from the queue.
- So, consider a situation where too many packets are present in this queue, such that constantly transmitting nodes are pouring packets at a higher rate than receiving nodes are removing them. This degrades the performance, and such a situation is termed as Congestion.
- Main reason of congestion is more number of packets into the network than it can handle.
- So, the objective of congestion control can be summarized as to maintain the number of packets in the network below the maximum level at which performance falls off dramatically.
- Initially number of packets delivered is propotional to the number of packets sent. However, as traffic increases too far, the routers are no longer able to cope and they begin losing packets. This tends to make matters worse. At very high traffic, performance collapses completely and almost no packets are delivered.

## Cause of Congestion
- Congestion happens in any system that involves waiting. For example, congestion happens on a freeway because any abnormality in the flow, such as an accident during rush hour, creates blockage.
- Congestion in a network or internetwork occurs because routers and switches have queues-buffers that hold the packets before and after processing. A router, for example, has an input queue and an output queue for each interface.
- When a packet arrives at the incoming interface, it undergoes three steps before departing:
    1. The packet is put at the end of the input queue while waiting to be checked.
    2. The processing module of the router removes the packet from the input queue once it reaches the front of the queue and uses it's routing table and the destination address to find the route.
    3. The packet is put in the appropriate output queue and waits it's turn to be sent.
- We need to be aware of two issues:
  - if the rate of packet arrival is higher than the packet processing rate, the input queue becomes longer and longer.
  - if packet departure rate is less than packet processing rate, the output queues become longer and longer.
- If there is insufficient memory to hold these packets, then packets will be lost. Adding more also may not help in certain situations.
- If router have infinite amount of memory even then instead of congestion being reduced, it get's worse. Because by the time packets gets at the head of the queue, to be dispatched out to the output line, they have already timed-out(repeatedly), and duplicates may also be present(multiple copies of same packet will be sent by sender due to timeout).
- All the duplicate packets will be forwarded to next router up to the destination, all the way only increasing the load of the network more and more. Finally, when it arrives at the destination, the packet will be discarded, due to time out, so instead of been dropped at any intermediate router such a packet goes all the way up to the destination, increasing network load throughout and finally gets dropped there.
- So, the major cause of congestion is often the bursty nature of traffic. If hosts could be made to transmit at a uniform rate, then congestion problem will be less common and all other causes will not led to congestion.
- When a device sends a packet and does not receive an acknowledgement from the receiver, in most of the cases it can be assumed that the packets have been dropped by intermediate devices due to congestion. By detecting the rate at which segments are sent and not acknowledged, the source or an intermediate router can infer the level of congestion on the network.

## Traffic Shaping
- Traffic shaping is a mechanism to control the amount and rate of the traffic sent to the network.
- Two techniques:
  1. Leaky Bucket
  2. Token Bucket

## Leaky Bucket
- If a bucket has a small hole at the bottom, the water leaks form the bucket at a constant rate as long as there is water in the bucket. The rate at which the water leaks does not depend on the rate at which the water is input to the bucket unless the bucket is empty. The input rate may vary but the output rate is constant.
- Also, once the bucket is full any additional water entering it spills over the sides and is lost. Similarly, in networking a technique called leaky bucket can smooth out bursty traffic. Busty chunks are stored in the bucket and sent out at an average rate.
- Let us assume that the network has committed a bandwidth of 3 Mbps for a host. The use of the leaky bucket shapes the input traffic to make it conform to this commitment. The host sends a burst of data at a rate of 12 Mbps for 2s, for a total of 24 Mbits. The host is silent for 5s and then sends data at a rate of 2 Mbps for 3s for a total of 6 Mbits of data. In all host send 30 Mbits of data in 10s.
- The leaky bucket smooths the traffic by sending out data at a rate of 3Mbps during the same 10s. Without the leaky bucket, the beginnning burst may have hurt the network by consuming more bandwidth than is set for this host.
- We can also see that the leaky bucket may prevent congestion. As an analogy, consider the highway during office. If instead, people could change their working hours congestion on our highways could be avoided.

### Leaky Bucket Implementation
- A FIFO queue holds the packets. If the traffic consists of fixed-size packets, the process removes a fixed number of packets from the queue at each tick of the clock.
- If the traffic consists of variable-length packets, the fixed output rate must be based on the number of bytes or bits instead of packets for e.g. if the rule is 1024 bytes per tick, a single 1024-byte packet can be admitted on a tick, two 512-byte packets, four 256-byte packets, and so on.
#### Algorithm for variable length packet
- Initialize a counter to n at the tick of the clock.
- If n is greater than the size of the packet, send the packet and decrement the counter by the packet size. Repeat this step until n is smaller than the packet size.
- Reset the countner and go to step 1.

## Question
A leaky bucket is used to shape the traffic. The host sends a burst of data at a rate of 12 Mbps for 2s then it is silent for 5s and then sends data at a rate of 2Mbps for 3s. If network can handle data @ 3Mbps only. How much time is needed to send this data using leaky bucket also find capacity of bucket.

### Solution
- Total data received is 30 Mbits.
- after one sec 3Mbits, ..., after 7 secs 21 Mbits, 8 secs 24 Mbits, 9 secs 27 Mbits, 10 secs 30 Mbits.
- Hence, it will take 10 seconds.
- Maximum Data in buffer can be at 2nd second i.e. 6 + 12 = 18 Mbits

## Question
A leaky bucket is used to shape the traffic. The host sends a burst of data at a rate of 2Mbps for 3s then it is silent for 5s and then sends data at a rate of 12 Mbps for 2s. If network can handle data @ 3 Mbps only. How much timem is needed to send this data using leaky bucket also find capacity of bucket.

### Solution
- First 3 seconds it will send data at rate of 2 Mbps.
- Next 5 seconds it will be silent.
- Next 8 seconds it will send 24 Mbits of data for 8 seconds.
- Total 16 seconds time is needed to send this data.
- Maximum buffer capacity required will be 18 Mbits.

## Question
As an example of a leaky bucket, imagine that a computer can produce data at 200 Mbps and that the network also runs at this speed. However, the routers can accept this data rate only for short intervals. For long intervals, they work best at rates not exceeding 16 Mbps. Now suppose station send one 40-msec burst every second. Find:
1. I/P rate
2. O/P rate
3. Capacity of leaky bucket
4. How much time bucket take to be emptied if no data comes from station

### Solution
- I/P rate: 200 Mbps
- O/P rate: 16 Mbps
- Data came for 40 ms:
  - $200 \times 10^{6} \times 40 \times 10^{-3}$
  - $800 \times 10^{4}$
- Data emtied upto 40ms:
  - $16 \times 10^{6} \times 40 \times 10^{-3}$
  - $64 \times 10^{4}$
- Capacity: 7.36 Mbits
- Time to empty:
  - $\frac{7.36}{16}$ = 0.46 seconds = 460 ms
  - 7.36M is left after 40ms, as we emptied 640K in the first 40 ms when the data was incoming.
  - Total time to empty: 40 + 460 = 500 ms

## Question
Computer A has 19.5 MB to send on a network and transmits the data in a burst @ 6 Mbps. The maximum transmission rate across routers in the network is 4 Mbps. If computer A's transmission is shaped using a leaky bucket, how much capacity must the queue in the bucket hold not to discard any data?

### Solution
- Time required to input 19.5 MB data:
  - Total data: 19.5*8 = 156 Mbits
  - Time = $\frac{156}{6} = 26s$
- Data emptied in 26s:
  - 26*4 = 104 Mbits
- Capacity maximum required:
  - 156 - 104 = 52 Mbits = 6.5 MB
- Also, $Capacity = Time \times Banwidth$
- $Capacity =\frac{26 \times (6-4)}{8}$ = 6.5 MB

## Question
A leaky bucket is at the host network interface. The data rate on the network is 2 MBps and the data rate on the link from the host to the bucket is 2.5 MBps.
1. Suppose the host has 250 MB to send onto the network and it sends the data in a burst. What should be the minimum capacity of the bucket in order that no data is lost?
2. Suppose the capacity of the bucket is 100MB. What is the longest burst time from the host in order that no data is lost?

### Solution
1. - Time to fill in 250 MB data = 100 seconds
    - Capacity = Time * B/W
    - 100 * 0.5 = 50 MB
2. - Capacity = 100MB
   - Time = Capacity / Bandwidth
   - 100 / 0.5 = 200 seconds

## Token Bucket
- The leaky bucket is very restrictive. It does not credit an idle host. For example, if a host is not sending for a while, it's bucket becomes empty. Now if the host has bursty data, the leaky bucket allows only an average rate. The time when the host was idle is not taken into account. On the other hand, **the token bucket algorithm allows idle hosts to send data at faster rates.**
- In this algorithm, the leaky bucket holds tokens, generated by a clock at the rate of one token every $\Delta$T sec. A bucket say has 3 tokens and there are 5 packets waiting to be transmitted. For a token to be transmitted, it must capture and destroy one token. Here, three of five packets go through, but the other two will be stuck waiting for two more tokens to be generated.
- The leaky bucket algorithm does not allow idle hosts to save up permission to send large bursts later. The token Bucket algorithm does allow saving, up to the maximum size of the bucket, n. This property means that bursts of up to n packets can be sent at once, allowning some business in the output stream and giving faster response to sudden bursts of input.
- Another difference between the two algorithms is that the token bucket algorithm throws away tokens when the bucket fills up but never discards packets. In contrast, the leaky bucket algorithm discards packets. In contrast, the leaky bucket algorithm discards packets when the bucket fills up.
- Here, too a minor variation is possible in which each token represents the right to send not one packet, but k bytes. A packet can only be transmitted if enough tokens are available to cover it's length in bytes. Fractional tokens are kept for future use.
- The implementation of the basic token bucket algorithm is just a variable that counts tokens. The counter is incremented by one every $\Delta$ T and decremented by one whenever a packet is sent. When the counter hits zero, no packets may be sent. In the byte-count variant, the counter is incremented by k bytes every $\Delta$T and decremented by the length of each packet sent.

## Question
**We have token bucket with capacity of 250KB**  
[Destroying all tokens in the bucket, station can send 250KB data at once].  
**Token arrives at rate allowing O/P @ 2MBps, Assume Token bucket is full when 1MB burst arrives**  
[Bucket is filled with tokens and not data, & station can destroy all these tokens to send 250KB data].  
**The bucket can drain @ 25MBps**  
[If few tokens are saved in bucket & data arrives then it can destroy all of them and send data @  25MBps].  
**Find amount of time for which data is sent @ 25MBps. Also find total time to send entire data.**

### Solution
1. - Initially the bucket is filled and it contains 250KB of token data.
   - Every second 2 MB data is sent when tokens are now not all filled.
   - $250 \times 10^{3} + (2 \times 10^{6} \times S) = 25 \times 10^{6} \times S$
   - $250 \times 10^{3} = 23 \times 10^{6} \times S$
   - S = 10.87 ms
2. - Total data sent in 11 ms = $11 \times 25 \times 10^{3}$ = 275 KB
   - Data left to sent is 725 KB
   - Time for that data $\frac{725}{2} \times 10^{-3}$
   - 373.5 ms(approx)
- Earlier data was sent @ 25MBps because that time the token bucket was filled
- In phase two now bucket was empty and new data empty rate depending on token is 2 MBps.
#### Formula
- Let S is time for which data is sent @ M bps
- Let C be capacity of the bucket
- P be the O/P rate
- C + (P * S) = M * S

## Question
For a host machine that uses the token bucket algorithm for congestion control, the token bucket has a capacity of 1 MB and the maximum output rate is 20 MBps. Tokens arrive at a rate to sustain output at a rate of 10 MBps. The token bucket is currently full and the machine needs to send 12 MB of data. What is the minimum time required to transmit the data in seconds.

### Solution
- Currently the bucket is full so it will send 1MB of data at maximum rate
- $S = \frac{1}{20-10}$
- S = 0.1 Sec
- The data sent for this 0.1 Second at rate 20MBps = 2MB
- Data left = 12 - 2 = 10 MB
- This data now will be sent @ 10 MBps, so it will require 1 second to send that data.
- Hence total time = 1.1 seconds