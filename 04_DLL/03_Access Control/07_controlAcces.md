# Control Access Protocol

- Here we have the concept of Primary and secondary station. Primary station will control all secondary stations
- If concept of Primary and secondary station is missing then station who wants to send data can send only if all other stations give permission to it.

## Reservation
- In reservation technique station needs to make reservation before sending data.
- Here we have contention period & it consists of exactly 'n' slots ('n' is no. of stations)
- If any station wants to send frame then it send only one bit i.e. '1' in it's reference slot else it send '0'.
- After contention period is over, stations who have send bit value as '1' will send this frame one after another.

## Polling
- Their is primary station which will send POLL message to secondary stations, asking whether they have data to send or not.
- If they don't want to send data they reply with 'NAK'
- If they want to send data they reply with 'data'
- In reponse of 'data' primary station will send 'ACK' which tells the data is received by primary station.
- Now Primary station sends SEL informing the receiver station to get ready to receive data.
- Receiver sends ACK in response of SEL to inform he is ready.
- Now Primary station will send data to receiver.
- Further after receiving data receiver station will send ACK to inform data is received.
- $\eta$ = $\frac{T_t}{T_{poll}+T_p+T_t}$ t

## GATE 2007
Nodes = 10, B/W = 10 Mbps & poling is access method. Polling delay = 80 $\mu$ sec. Node is allowed to send maximum of 1000 bytes data once it is polled. Maximum throughput?

### Solution
- $T_{poll}$ = 80 $\mu$ sec
- $T_t$ = 1000*8/10Mbps = 800 $\mu$ sec
- $\eta$ = $\frac{T_t}{T_{poll}+T_p+T_t}$ t
  - $\eta$ = $\frac{800}{80+800}$ = 0.9
- Throughput = $\eta$ * B/W
  - Throughput = 0.9 * 10Mbps = 9Mbps

## Token Passing
- Token is a special frame of 3 Bytes
- Token keeps circulating in the network, if any station wants to send data it will capture token and send data.
- Once the station gets back ACK from receiver it will release token.
- Token passing is unidirectional
- There is also other method called FDDI
  - Here there are dual rings one primary and one secondary, if primary fails we can use secondary.
