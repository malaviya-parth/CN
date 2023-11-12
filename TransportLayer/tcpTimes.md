## TCP Timers
1. Time Wait Timer
2. Keep Alive Timer
3. Persistent Timer
4. Acknowledgement Timer
5. Time Out Timer ⭐

## Time Wait Timer
- When the TCP client peer want to terminate the connection, it sends FIN.
- Now, after receiving FIN from server, the client sets of Time Wait Timer equal to 2*MSL, then terminates the connection after timer expiration.

## Keep Alive Timer:
- A keepalive timer is used in some implementations to prevent a long idle connection between two TCPs.
- Suppose that a client opens a TCP connection to a server, transfers some data, and becomes silent. Perhaps the client has crashed.
- In this case, the connection remains open forever.
- To remedy this situation, most implementations equip a server with a keepalive timer.
- Each time the server hears from a client, it resets this timer. The time-out is usually 2 hours.
- If the server does not hear from the client after 2 hours, it sends a probe segment.
- If there is no response after 10 probes, each of which is 75 seconds apart, it assumes that the client is down and terminates the connection.

## Persistent Timer
- It is used in Flow control.
- When receiver sends WS = 0, persistent timer is set to some value.
- When persistent timer expires, sender sends a probe packet to know whether now the receiver is able to get data or not.

## Acknowledgement Timer
- Used if data comes, ACK packet wait for ACK timer so that if piggybacking is possible then it can be performed.
- If ACK timer expires then pure ACK is sent.

## Time out Timer / Retransmission Timer
- At DLL we have studied about Time Out Timer & it was easy to find because DLL work Hop to Hop.
- RTT = 2 * Tp
- TOT = 2 * RTT
- But at transport layer it will be difficult to find Time out because end to end.
- 3 Issues:
  - Finding Tp,TT,QT,PT, etc of each node is difficult
  - Segments are encapsulated in datagram & it may travel via different path so some times RTT decreases and some time RTT increases.
  - At different time we have different amount of traffic like at 6 am 10 ms and at 6 pm 40 ms.
- Considering all these factors, static Time out timer will not work for TCP.
- We need dynamic Time out timer for TCP which can increase or decrease according to the traffic.
### Basic Algorithm
- Time Out = 2 * RTT
- NRTT = $\alpha \times IRTT + (1-\alpha) \times ARTT$ [$\alpha$ is weight factor($0 \leq \alpha \leq 1$)]
  - NRTT = Next Round Trip Time
  - IRTT = Initial Round Trip Time (What we thought)
  - ARTT = Actual Round Trip Time (What actual came out)
- Generally $\alpha = \frac{7}{8}$, we give more priority to Predicted RTT rather than Actual RTT.
  - Same as in Stock Market we give calculations more priority than Current Price.
  - If $\alpha = \frac{1}{2}$, we give equal priority to both.
$$PRTT_{n+1} = \alpha \times PRTT_{n} + (1-\alpha) \times ARTT_{n}$$
- Using Recurrence Relation and keep on substituting $PRTT_{n}$, at last step we reach $PRTT_{1}$ which is genrally given in the question for the solving purpose.
  - Generally $PRTT_{1}$ is calculated during connection establishment when SYN flag is sent and ACK is received for it.
#### Example
- PRTT1 = 10 ms, $\alpha = \frac{1}{2}$, ARTT1 = 15 ms
- TimeOut1 = 20 ms
- PRTT2 = 5 + 7.5 = 12.5 ms
- TimeOut2 = 25 ms
#### Example
- PRTT1 = 10ms, ARTT1 = 15, ARTT2 = 20, ARTT3 = 10, PRTT4 = ?, T.O.4 = ?
- PRTT4 = $(\frac{1}{8} \times 10) + (\frac{1}{8} \times 15) + (\frac{1}{4} \times 20) + (\frac{1}{2} \times 10)$ = 1.25 + 1.875 + 5 + 5 = 13.125
- TO = 26.25