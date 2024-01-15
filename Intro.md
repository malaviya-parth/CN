# History & Introduction
- Earlier more & more computers were installed in different plalces of world. Need was to trasfer data between them.
- Floppy Disks and Tape drivers were used to transfer data, which wasn't efficient.
- Later started to connect them through wired networks.
- There are issues while transfering data through wired networks like:
  - Data transfer rate is slow.
  - Different format of data.
  - Binary data to Signals
  - Who can access channel when
- For all this we need a Network model which can handle all the issues related to data transfer b/w computers.
- There are layers in the Network model which perform subtasks to transfer data.

# Next Part
- Basically CN was introduced to solve the problem of Data sharing between different computers.
- Task of transferring data can be divided into 4 different subtasks
    1. Send data in the form of packets
    2. Send data in common format so that Windows/ Linux any machine can understand
    3. Convert Binary data to electrical signals
    4. Who can access the network and when
- Network Model handles all the issues related to data transfer
- There are 2 types of Network Models
    1. OSI Model
    2. TCP/IP Model

## OSI Model
- OSI Model is a 7 layer model
- OSI Model is a reference model and not an implementation model
- It is standardised by ISO
- Open System Interconnection, here Open System means that any system can connect to any other system irrespective of their software(Windows and Linux) and hardware(Pentium and Some Dual Core) architecture

### OSI Model Layers
- Layers are:
    1. Physical Layer
    2. Data Link Layer
    3. Network Layer
    4. Transport Layer
    5. Session Layer
    6. Presentation Layer
    7. Application Layer
(Aap Papa Se To Nhi Darte Pappu)

- At Sender side, data is passed from top to bottom layer and at receiver side, data is passed from bottom to top layer
- Top Layer is the Application Layer and Bottom Layer is the Physical Layer
- Layer take services from the layer above it and provide services to the layer below it
- Each layer communicates with its peer layer on the other machine
- Application Layer and Physical Layer do not add any header or trailer to the data
- Network Layer, Transport Layer, Session Layer, Presentation Layer and Data Link Layer add header to the data
- Data Link Layer adds both header and trailer to the data
- Application Layer is the layer which is used by the user, it provides interface to the user
- Physical Layer is the layer which is responsible for converting data into electrical signals

- Packet is called as Frame in Data Link Layer
- Packet is called as Segment or User Datagram in Transport Layer
- Packet is called as Datagram in Network Layer
- Packet is called as Data in Application Layer

- Layer 1,2,3 are called Network Support Layers (Provides Network Related Services)
- Layer 5,6,7 are called User Support Layers (Provides Open System Environment)
- Layer 4 is called Transport Layer (Provides End to End Communication)

### Physical Layer

- Physical Layer is responsible for converting data into electrical signals
- States about the physical medium used for data transfer (Copper Wire, Optical Fiber, Radio Waves)
- States type of Media used (Wired or Wireless)
- Provides representaion of bits
- Defines Data Rate (Speed of Data Transfer), Transmission Rate (Number of bits transferred per second), Bit Duration (How long bit last on Transmission Media)
- Data Rate can be measured in bps (bits per second), kbps (kilo bits per second), Mbps (Mega bits per second), Gbps (Giga bits per second)
- Bit Duration can be calculated as if Data Rate is 1kbps then Bit Duration is 1/1000 seconds
- Provides Synchronization of bits (Sender and Receiver should be in sync)
- Line Configuration (Point to Point or Multipoint)
    - Point to Point (Single Sender and Single Receiver)
        - Dedicated Line (Line is dedicated to the sender and receiver)
        - Example: Telephone Line, Cable TV
        - Topology (Ring, Mesh)
    - Multipoint (Single Sender and Multiple Receiver)
        - Shared Line (Line is shared between multiple receivers)
        - Example: Radio Station, TV Station, Internet
        - Topology (Bus, Star, Ring, Mesh)
- Topology (Bus, Star, Ring)
- Transmission Mode (Simplex, Half Duplex, Full Duplex)
    - Simplex (One way communication, only one can send and other can only receive)
        - Example: Radio Station, TV Station
    - Half Duplex (Two way communication, both can send and receive but not at the same time)
        - Example: Walkie Talkie
    - Full Duplex (Two way communication, both can send and receive at the same time)
        - Example: Telephone Line, Internet

#### Types of Addresses

- Physical Address 
    - Used to Identify the device uniquely within the LAN (Local Area Network)
    - Example: (MAC Address)
        - 48 bit address
        - Unique address
        - Address is burned in the NIC (Network Interface Card)
        - Address is provided by the manufacturer
        - Address is in hexadecimal format
        - Address is in the form of 6 pairs of hexadecimal digits
        - First 3 pairs are called OUI (Organizationally Unique Identifier) and last 3 pairs are called NIC (Network Interface Card)
        - Stored in ROM
        - Example: 00-0A-95-9D-68-16

- Logical Address
    - Used to Identify the device uniquely within the network
    - Example: IP Address
        - 32 bit address
        - Address is provided by the ISP (Internet Service Provider)
        - Address is in the form of 4 decimal numbers
        - Each decimal number is in the range of 0 to 255
        - Stored in RAM
        - Example:

- Port Address
    - Used to Identify the process uniquely within the device
    - Example: Port Number
        - 16 bit address
        - Address is provided by the OS (Operating System)
        - Address is in the form of 4 decimal numbers
        - Each decimal number is in the range of 0 to 65535
        - Example: 80 (HTTP), 21 (FTP), 23 (Telnet), 25 (SMTP), 53 (DNS), 443 (HTTPS)

### Question

1. Supose data is transferred from sender to receiver and there are n intermediate Nodes. 
    1. How many times data is copied?
    - Answer: n+1 times
    - Explanation: Data is copied at each node and at sender and receiver
    2. How many times Physical Layer is accessed?
    - Answer: 2n + 2 times
    - Explanation:  At each node it is accessed 2 times (1 for sending and 1 for receiving) and at sender and receiver it is accessed 1 time (1 for sending and 1 for receiving)
    3. How many times Data Link Layer is accessed?
    - Answer: 2n + 2 times
    - Explanation:  At each node it is accessed 2 times (1 for sending and 1 for receiving) and at sender and receiver it is accessed 1 time (1 for sending and 1 for receiving)
    4. How many times Network Layer is accessed?
    - Answer: n + 2 times
    - Explanation:  At each node it is accessed 1 time (for checking network address) and at sender and receiver it is accessed 1 time
    5. How many times Transport Layer is accessed?
    - Answer: 2 times
    - Explanation:  At sender and receiver it is accessed 1 time.
    6. How many times Application Layer is accessed?
    - Answer: 2 times
    - Explanation:  At sender and receiver it is accessed 1 time.
