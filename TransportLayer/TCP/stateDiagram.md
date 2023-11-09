## TCP State Transition Diagram
![Alt text](image-6.png)
### Transition States
| State | Description |
| ----- | ----------- |
| CLOSED | No connection exists |
| LISTEN | Passive open received; waiting for SYN |
| SYN-SENT | SYN sent; waiting for ACK |
| SYN-RCVD | SYN+ACK sent; waiting for ACK |
| ESTABLISHED | Connection established; data transfer in progess |
| FIN-WAIT-1 | First FIN sent; waiting for ACK |
| FIN-WAIT-2 | ACK to first FIN received; waiting for second FIN |
| CLOSE-WAIT | First FIN received, ACK sent; waiting for application to close |
| TIME-WAIT | Second FIN received, ACK sent; waiting for 2MSL time-out |
| LAST-ACK | Second FIN sent; waiting for ACK |
| CLOSING | Both Sides decided to close simultaneously |
### 3-Wayy handshaking Establishment and 4-way handshaking termination
![Alt text](image-7.png)
- TCP has two types of Input, Local input and remote Input.
  - Active open, Active close, Passive open, etc. are local input
  - SYN+ACK, ACK, FIN, etc. are remote Input
  - SYN, ACK, etc. are output
- Look we can see that when client sent SYn the server is in LISTEN state and so replies with SYN+ACK.
- If server is in closed state, server replies with RST and says to reset the connection.
#### Client and Server Side series of States
![Alt text](image-8.png)
- Closed(Active open/SYN) -> SYN-SENT(SYN+ACK/ACK) -> Established(Active Close/FIN) -> FIN-WAIT-1(ACK/-) -> FIN-WAIT-2(FIN/ACK) -> TIME-WAIT(Time-out) -> CLOSED
- Closed(Passive open/-) -> LISTEN(SYN/SYN+ACK) -> SYN-RCVD(ACK/-) -> ESTABLISHED(FIN/ACK) -> CLOSE-WAIT(Passive Close/FIN) -> LAST-ACK(ACK/-) -> CLOSED

### Time Out
- The time out time is 2 maximum segment lifetime, like if client sent ACK but not received by server than within 2MSL the server will again send FIN packet which indicates that the ACK packet sent by the client is lost.
  - Client resend the ACK and 2MSL timer is reset.
- To handle this lost packet cases of ACK after FIN client wait for 2MSL, if within 2MSL if FIN by server not comes, client understand that the packet might have reached the server and connection is successfully terminated.

## Question
Suppose Client sneds SYN but it does not reach to the server what state the client will be?

### Solution
- Doesn't matter about packet reached to server or not the state of client will be SYN-SENT.

## Note
> It does not matter whether the sent packet is received to opposite side or not, as soon as the source sends the packet it gets into the desired state.