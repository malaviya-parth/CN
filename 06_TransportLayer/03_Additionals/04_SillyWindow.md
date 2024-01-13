## Silly Window Syndrome
- A serious problem can arise in the sliding window operation when either the sending program creates data slowly or the receiving application program consumes data slowly, or both.
- Any of these situations results in the sending of data in very small segments, which reduces the efficiency of the operation.
- For example, if TCP sends segments containing only 1 byte of data, it means that a 41-byte datagram transfers only 1 byte of user data.
- This indicates that we are using the capacity of the network very inefficiently.
- The inefficiency is even worse after accounting for the data link layer and physical layer overhead.
- This problem is called the silly window syndrome.

## Nagle's Solution (If sender is slow)
- The sending TCP sends the first piece of data it receives from the sending application program even if it is only 1 byte.
- After sending the first segment, the sending TCP accumulates data in the output buffer and waits until either the receiving TCP sends an acknowledgement or until enough data has accumulated to fill a maximum-size segment. At this time, the sending TCP can send the segment.
- Step 2 is repeated for the rest of the transmission. Segment 3 is sent immediately if an acknowledgement is received for segment 2, or if enough data have accumulated to fill a maximum-size segment.
- The elegance of Nagle's algorithm is in it's simplicity and in the fact that it takes into account the speed of the application program that creates the data and the speed of the network that transports the data. If the application program is faster than the network, the segments are larger(MSS). If application program is slower than the network, the segments are smaller(less than MSS).

## Clark's Solution
- Suppose receiver window is of 1000 bytes.
- First sender sent 999 bytes, receiver ACK with WS=1.
- Second Sender sent 1 B, Receiver being slow yet only able to process 2 bytes, so sent ACK with WS=2.
- Receiver being slow every time sents ACK with WS very less around 10.
- Due to this the efficiency decreases, to get rid of this we have Clark's Solution.
- **Clark's Solution is to announce a WS of zero until either there is enough space to accomodate a segment of MSS or until at least half of the receive buffer is empty.**