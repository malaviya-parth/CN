## Transport Layer
- It takes care of process to process delivery.
- In the era of multiuser and multi-programming environments, we don't know which process needs the help of which process as a remote computer can run several processes at the same time as on the client side. Hence, each process running on Machine must be identified by a unique number known as **port address** because without this packet can't be delivered to actual process which is communicating.

## Identification
1. Local host ( ip and physical address)
2. Local Process (port address)
3. Remote host ( ip and physical address)
4. Remote Process (port address)

## Port Number
- It is a 16 bit integer number.
- The client process when starts it is given a temporary port number by the OS, known as ephemeral port number.
- The port number for the server is not given randomly but it has some well-known universal port number like 13 is for daytime server.(Well-known/permanent/universal)

## IANA Ranges
1. 0 - 1023 ( Well Known Port Numbers )
2. 1024 - 49151 ( Registered Port Numbers )
3. 49152 - 65535 ( Dynamic/ Private Port Numbers )

- **Well-Known Ports:** Ports ranging from 0 - 1023 are assigned and controlled by IANA. These are assigned to processes which are related to core networking tasks like port number for DNS is 53, DHCP client and server is 67, 68, SNMP is 161 etc.
- **Registered Port:** These are not assigned or controlled by IANA. THey can only be registered with IANA to prevent duplication.
- **Dynamic Ports:** These are neither controlled nor recorded. They can be used by any process. These are temoparay ports.

## Socket Address
- To identify process uniquely in whole world.
- It is combination of IP and Port address.
- TL protocol needs a pair of socket addresses: client socket and server socket address.

## Multiplexing and Demultiplexing
- At sender side there are multiple processes who want to send their packets, but there is only one transport layer protocol. This is many-to-one relationship and requires multiplexing.
- At receiver site, the relationship is one-to-many and requires demultiplexing. Transport layer receives datagrams from Network layer. After error checking and dropping of the header, the transport layer delivers each message to the appropriate process based on the port number.