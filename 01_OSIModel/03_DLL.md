# Data Link Layer (DLL)
- DLL is responsible for transferring data from one node to adjacent node (Node to node or Hop to Hop).

## Functions:-

1. Framing:- 
    - Adding a header and trailer to the data received from the Network Layer and resulting in the packet called as Frame.
2. Physical Addressing:-
    - Header of frame contain physical address of both Sender & Receiver if both are in same network, if not then only the physical address of the next hop is present.
3. Flow Control:-
    - Amount of Data that can be sent from sender to receiver before receiving ACK.
4. Error Control:-
    - Error Detection and Retransmission of frames that are corrupted or lost.
    - Error Correction
    - Error Detection and Retransmission is more efficient than Error Correction.
5. Access Control;-
    - Who can accesss the shared channel when there are multiple devices connected to the same channel.