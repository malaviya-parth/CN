# Selective Repeat Protocol

- When the times expires for a packet then only that packet is retransmitted, but in GBN entire window of N packets were transmitted.
- Unlike GBN here out of order delivery is also allowed.
- Timer is maintained for each & every frame in window at sender side.
- Out of order delivery is accepting receiver but packets are delivered to upper layer in order. Hence, sorting of packets is done at receiver side.
- Unlike GBN here acknowlwdgements for each packet is sent to sender.
- For 1st out of order deliery or if packet received is corrupted then NAK for respective packet is sent to sender.
  - Like if 0 is expected and 1 is received, receiver will send NAK0 and ACK1.
  - Also, for further process, if still 0 not received and receiver gets 2 and then three, it will send ACK2 and ACK3 respectively not NAK0 this time.
  - NAK is sent only for first out of order delivery.
- When sender receives NAK for a packet then it retransmits that packet even though it's timer is not expired.
  - Searching is done at sender side for the packet.

## Note
> Sender Window Size = Receiver Window Size

- If m bit overhead is available then total $2^m$ sequence numbers are available.
- Here, Sender Window Size = Receiver Window Size = $\frac{2^m}{2}$ = $2^{m-1}$

## Eficiency
Efficiency = $\frac{Actual \; Window \; Size }{Maximum \; Window \; Size }$  
Efficieny = $\frac{N}{1+2a}$  
Where,  
N = Number of bits transmitted  
a = Propagation delay / Transmission delay  
$\eta$ = $\frac{2^{m-1}}{1+2a}$  
Here Selective repeat has efficiency less than GBN, but have better Bandwidth utilization.

## Question
If sender wants to send 10 packets and sender window size is 5, Every 5th packet is lost. Then how many frames will be transmitted by sender?

### Solution
- 1,2,3,4,\_,5,6,7,8,\_,9,10
- $\therefore$ Total number of 12 frames.
- This shows the better Bandwidth Utilization.

## GATE 2016
B/W = 128 kbps, Propagation delay = 150 ms, Selective Repeat Protocol, Frame Size = 1 KB, T.T. of ACK $\approx$ 0 ms. Minimum no. of bits for sequence number field to achieve 100% utilization.

### Solution
- Transmission Time = $\frac{Frame \; Size}{Bandwidth}$ = $\frac{1024 \times 8}{128 \; kbps}$ = 64 ms
- a = $\frac{Propagation \; Delay}{Transmission \; Time}$ = $\frac{150 \; ms}{64 \; ms}$ = 2.34
- Efficieny = 1
  - N = 1 +2a = 1 + 2(2.34) = 5.68 $\approx$ 6
  - We took 6 not 5 because sender must not remain idle
- N for Sender and N for receiver = 6
- Total = 12 frames
- $\therefore$ Minimum no. of bits for sequence number field = 4

## Comparison

| Properties| Stop & Wait | GBN | Selective Repeat |
|---|---|---|---|
| Sender Window Size | 1 | N | N |
| Receiver Window Size | 1 | 1 | N |
| Minimum Sequence Number | 2 | N+1 | 2N |
|Efficiency| $\frac{1}{1+2a}$ | $\frac{N}{1+2a}$ | $\frac{N}{1+2a}$ |
| ACK | Individual | Cumulative | Individual |
| NAK | No | No | Yes |
| Supported Order | - | In order | Out of order & In order |
| No. of retransmission | 1 | N | 1 |
| CPU Utilization | Low | Mid | High |