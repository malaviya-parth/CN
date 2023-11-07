## User Datagram Protocol
- Is is a connectionless protocol, unreliable transport protocol.
- If a process want to sned a small message and does not care about reliability, it can use UDP.
- **Connectionless:** No need of connection establishment or connection release.
  - The packets are not numbered, they may be deleted or lost or may arrive out of sequence.
  - There is no acknowledgement either.
  - Path of packets to be sent is not fixed.
- Also data size is only that much which can be sent because here segmentation of data is not done.
- Unreliable means no need of flow and error control, it can be because of own error and flow control mechanism by application program or it needs fast service or the nature of the service does not demand flow and error control(real-time applications).
  - TFTP uses UDP because it has it's own error and flow control mechanism.
- We need error and flow control at transport layer because it is not provided at the network layer and DLL provides error and flow control between two nodes only. So what about end to end control, this is done by transport layer.
- ![Alt text](image.png)
- For flow sliding window is applied at transport layer as well, but here window is character oriented instead of frame-oriented.

> UDP has got limited error control.  
> Checksum is used in UDP but it is optional.
