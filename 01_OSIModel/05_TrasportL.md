# Transport Layer
- End to End delivery of entire message or process to process delivery.

## Functions of Transport Layer

1. Service Point Addressing:- Header of transport layer contains port addresses of both sender & receiver processes

2. Segmentation & Reassembly:- Transport layer divides-stream of bits into segments & reassembles them at receiver side. Each segment contains a sequence number so that segments can be reassembled in order.

3. Connection Control:- Connectionless (UDP Protocol) or connection oriented service (TCP/IP Protocol).

4. FLow Control:- Transport layer ensures that sender & receiver are synchronized. It ensures that sender is not sending data faster than receiver is receiving it.

5. Error Control:- Transport layer adds error control bits to the data so that errors can be detected & corrected at receiver side.

6. Congestion Control:- Transport layer ensures that sender is not sending data faster than network can handle.

7. Multiplexing & Demultiplexing:- Transport layer combines data from multiple application into single stream of data for transmission. At receiver side, transport layer receives data from network layer & passes it to the appropriate application.
   - There are multiple processes sending packets to transport layer from application layer, so transport layer multiplexes these packets into single stream of data & passes it to network layer. Vice versa at receiver side.