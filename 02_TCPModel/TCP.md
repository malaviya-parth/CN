# Transmission Control Protocol (TCP)

- TCP is a connection-oriented & reliable protocol.
  - Connection-oriented means that there is a connection establishment between the sender and the receiver before sending the data.
    - Connection-orientted has 3 steps:
      1. Connection Establishment
      2. Data Transfer
      3. Connection Termination
  - Reliable means that there is a guarantee that the data will be delivered to the receiver.
  - Reliable suggest there is error checking and tracking and hence it is not a best-effort delivery protocol.
- TCP is byte-oriented or stream-oriented protocol.
  - It means that the data is sent in the form of a stream of bytes.
  - The data is divided into segments and each segment is assigned a sequence number.
  - The segments are sent in the form of packets called TCP segments.
  - The segments are reassembled at the destination to form the original data.
- TCP is not aware of message boundaries.
  - It means that the segment can contain data from multiple messages, or a message can be divided into multiple segments.

# User Datagram Protocol (UDP)

- It is unreliable and connectionless protocol.
  - Unreliable means that there is no guarantee that the data will be delivered to the receiver.
  - Connectionless means that there is no connection establishment between the sender and the receiver before sending the data.
- It has optional error detection mechanism.
- Packets are called User Datagram.
- It is a message oriented protocol i.e. UDP has knoledge about message boundaries & we can send only the message that fits in a single packet.

# Stream Control Transmission Protocol (SCTP)

- It uses best features of TCP and UDP.
- It is a reliable, connection-oriented and message-oriented protocol.

## Note:-
> To send small amount of data at real-time, UDP is used. For example, in video conferencing, UDP is used to send the video and audio data.  
> To send large amount of data, TCP is used. For example, in file transfer, TCP is used to send the file.