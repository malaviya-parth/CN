# Capacity of the link

- Number of bits needed to fill the link/channel/wire/media.

## Question
If B/W is 1 bps & propagation delay is 5 secs. Find capacity of the link.

### Solution
Bandwidth is 1 bps so every second 1 bit is transmitted.  
Propagation delay is 5 secs so after the 6th second the first bit will reach the destination.  
When 6th bit come on the channel meanwhile the 1st bit will reach the destination.  
At any time, there will be 5 bits in the link.  
So, capacity of the link is 5 bits.

## Capacity = Bandwidth * Propagation Delay
### Also known as Bandwidth Delay Product (BDP)

## Question
B/W = 1 Mbps & Propagation Delay = 1 ms, Packet size = 100 bits. How many packets can be in transit at a time?

### Solution
Capacity = 1 Mbps * 1 ms = 1000 bits  
No. of packets = 1000/100 = 10 packets

## Question
B/w = 10 Mbps, Tp = 1 ms, Packet Size = 100bits. Find Number of packets needed to maximally utilize the link.

### Solution
Capacity = 10 Mbps * 1 ms = 10000 bits  
Number of packets = 10000/100 = 100 packets  
Number of bits to label this packets = 7 bits (2^7 = 128)

## Question
What will be the effect of capacity of link on efficiency of stop & wait protocol?

### Solution
Capacity of link depends on Bandwidth & Propagation Delay.  
More Bandwidth means less Transmission Delay and Transmission delay is directly proportional to efficiency means less efficiency.  
Propagation delay is inversely proportional to efficiency so more propagation delay means less efficiency.
So, More capacity means less efficiency.

## Question
Stop and wait can work in which transmission mode?

### Solution
Stop and wait can work in both Simplex and Half Duplex mode but not in Full Duplex mode.