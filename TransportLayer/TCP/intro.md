## Transmission Control Protocol
- It is connection oriented and reliable protocol.
- TCP works in full-Duplex mode.
- TCP is byte stream protocol i.e. every byte of data is numbered but IP is packet stream protocol i.e. every packet [ Datagram ] is numbered [ID field].
- Unlike UDP, TCP can be used to send large messages i.e. chopping of large message into segments can be done by TCP.
### Connection
- It is virtual connection & not physical i.e. segments of TCP may follow different paths, some of them may lost or duplicated or arrive out of order because they are encapsulated in IP datagram.
- Resources like buffer are allocated to client and server in advance before starting transmission.
- The buffers used are circular buffers.
### Reliable
- TCP has both flow and error control.
- For flow control there will be byte oriented sliding window protocol.

## TCP Header ⭐⭐⭐
- Minimum 20 bytes and maximum 60 bytes.
![Alt text](image.png)
- Source Port address 16 bit field used to identify application program in host sending the segment.
- Destination Port address 16 bit field used to identify application program in host receiving. the segment.
### Sequence Number
- 32 bit field
- As TCP is byte-oriented so every byte transmitted is numbered.
- Sequence number is the byte no. of 1st byte carried in the segment.
  - Suppose a 5 byte data is sent in a segment, each byte having numbers 500,502,502,503,504
  - Now the sequence number will be byte number of first byte i.e. 500.
- TCP works in full duplex mode i.e. both parties can send data to each other.
- During connection establishment both parties uses random number generator to create Initial sequence no., which is usually different in each direction.
  - Random because, if everytime we start with let's say 0, and data of 50 bytes is sent.
  - First segment has seq: 0
  - Second has seq: 50
  - Third has seq: 100, but this got lost
  - Fourth has seq: 150
  - No third ACK would have come so resent third with seq: 100
  - Now connection is terminated.
  - Again both process communicate for some other purpose.
  - Again numbering start with 0, data of 50 bytes.
  - Two packets accepted by receiver.
  - This time if that seq: 100 packet which got lost came to receiver, it cannot differentiate whether it is new or old one.
  - Due to this sequence numbers are generated randomly.
- 