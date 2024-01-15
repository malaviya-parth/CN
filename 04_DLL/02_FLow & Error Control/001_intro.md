# Flow & Error Control

- Flow Control co-ordinates amount of data that can be sent by sender before receiving the ACK.
- Error Control is implemented by ARQ(Automatic Repeat Request) protocol i.e. if error is detected at receiver side then it silently discards the frame and when timer expires at sender side then it resends the frame.
- We call the mechanism as ARQ $\because$ receiver is not giving any instruction to sender for retransmission.

## Types of ARQ
1. Stop & Wait ARQ
2. Go Back N ARQ
3. Selective Repeat ARQ