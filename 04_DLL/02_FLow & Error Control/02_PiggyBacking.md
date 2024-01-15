# Piggybacking

- In order to improve efficieny, ACK is not sent in seperate frame rather data frame is used to send ACK.
- The technique of temporary delaying the outgoing ACK. So that it can be hooked on to the next outgoing data frame is called as Piggybacking.
- It is not always possible to use piggybacking.

## Efficiency
- Here Receiver is also sending packet of some considerable size, so efficiency will depend on that as well
- $\eta$ = $\frac{TTs + TTr}{TTs + TTr + 2TP}$
- Sincde Receiver also has has transmission time, it will also be considered under useful cycle.

## Question
- Efficiency of Stop&Wait if piggybacking is used?

### Solution
- Here if piggbacking is used then Useful cycle time is 2 T.T. and total cycle time is 2 T.P. + 2 T.T.
- $\eta$ = $\frac{2 T.T.}{2 T.P. + 2 T.T.}$ = $\frac{T.T.}{T.P. + T.T.}$ = $\frac{1}{1 + \alpha}$, where $\alpha$ = $\frac{T.P.}{T.T.}$

## GATE 2005
B/W = 4kbps, Tp = 20 ms, TT of ACK is negligible, Efficiency atleast 50%, minimum frame size in bits?  

### Solution
Efficiency atleast 50%  
$\Rightarrow$ TT $\geq$ 2 Tp    
$\Rightarrow$ Packet size $\geq$ 2 Tp $\times$ B/W  
$\Rightarrow$ Packet size $\geq$ 2 $\times$ 20 $\times$ 10$^{-3}$ $\times$ 4 $\times$ 10$^3$    
$\Rightarrow$ Packet size $\geq$ 160 bits

## GATE 2015
B/W = 64 kbps, Tp = 20 ms, TT of ACK is negligible, Efficiency atleast 50%, minimum frame size in bits?

### Solution
Efficiency atleast 50%  
$\Rightarrow$ TT $\geq$ 2 Tp  
$\Rightarrow$ Packet size $\geq$ 2 Tp $\times$ B/W  
$\Rightarrow$ Packet size $\geq$ 2 $\times$ 20    $\times$ 10$^{-3}$ $\times$ 64 $\times$ 10$^3$   
$\Rightarrow$ Packet size $\geq$ 2560 bits  
$\Rightarrow$ Packet size $\geq$ 320 bytes

## GATE 2015
B/W = $10^6$ bps, Packet Size = 1000 bytes, TT of ACK is negligible, Efficiency = 25, Tp = ?

### Solution
Efficiency = 25  
$\Rightarrow$ $\eta$ = $\frac{TT}{TT + 2TP}$  
$\Rightarrow$ 25 = $\frac{\frac{1000 \times 8}{10^6}}{\frac{1000 \times 8}{10^6} + 2TP}$  
$\Rightarrow$ 25 = $\frac{8}{8 + 2TP \times 10^{3}}$  
$\Rightarrow$ Tp = 12 ms

## GATE 2016
Frame size = 1000 bytes, Transmission rate of sender = 80kbps, ACK size = 100 bytes, Transmission rate of receiver = 8 kbps, Tp = 100 ms. Assume no frame is lost. Find throughput in bytes/sec.

### Solution
Transmission Time of sender = 100 ms  
Transmission Time of receiver = 100 ms  
Efficiency = $\frac{TTs + TTr}{TTs + TTr + 2TP}$  
Efficiency = $\frac{200}{400}$
Also, 1 frame i.e. 8000 bits are sent in 400 ms  
Throughput = 20 Kbps = 2.5 KBps  

## GATE 2017
B/W = 1 Mbps, Tp = 0.75 ms, Time to process frame = 0.25 ms, No. of bytes in information frame = 1980. No. of bytes in ACK frame = 20. Assume no transmission error. Find efficiency.

### Solution
TTs = 15.84 ms, TTr = 0.16 ms, TP = 0.75 ms  
Efficiency = $\frac{TTs + TTr}{TTs + TTr + 2TP + 2Processing Time}$  
(2*Processing Time because once receiver will process frmae and once sender will process ACK)  
Efficiency = $\frac{16}{16 + 1.5 + 0.5}$ = 88.88%