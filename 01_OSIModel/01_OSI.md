# OSI (Open Systems Interconnection) Model

- This model was standardized by ISO( International Organization for Standardization)
- Open System here means that 2 system can communicate regardless of their underlying architecture (WHatever Hardware and Software it has).
- OSI model has 7 Layers

## 7 Layers of OSI Model
1. Physical Layer
2. Data Link Layer
3. Network Layer
4. Transport Layer
5. Session Layer
6. Presentation Layer
7. Application Layer

- Each Layer takes services from the layer above it and provides services to the layer below it, i.e. Transport Layer takes services from Session Layer and provides services to Network Layer.
- Each layer x of a system communicates with its peer layer x of another system.
- Each layer has a specific function to perform on the data.
- Each layer has a protocol which defines the rules and conventions for communication between 2 layers.
- Except application layer and physical layer, all layer add their own header or trailer to the data coming from the above layer.
- Layers 6,5,4,3 adds only header while layer 2 adds both header and trailer.
- Application layers provides interface with the help of which user can interact with the system.
- Physical layer does not add header or trailer because it mainly deals with transferring signals from sender to receiver.

<br/>

- Data Packet at transprot layer is called Segment (TCP) or User Datagram (UDP).
- Data Packet at network layer is called Packet or Datagram (IP).
- Data Packet at data link layer is called Frame (Ethernet).

<br/>

- Layer 1,2,3 are known as Network Support Layers, they mainly deals with physical aspects of moving data from one device to another.
- Layer 5,6,7 are known as User Support Layers, because they mainly deal with concept of interporability between different systems.
- Layer 4 is known as Transport Layer, used for end to end delivery of entire message.