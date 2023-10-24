## Fragmentation:
- Application Layer bits are segemented at transport layer
  - Maximum Segment size: 65515
  - Maximum Payload Size: 655495
- Then it is converted into Datagram in network layer
  - Maximum Datagram Size: 65535
  - Maximum Payload Size: 65515
- Then it is converted into fram at DLL
  - Maximum Frame Size: 1518 bytes
  - Maximum Payload Size: 1500 bytes
- From Netwrok layer to DLL we need to divide the packet into small frames known as fragmentation.
```
| Header(Network) | Header(Transport) | Data |
```
- In fragmentation we don't divide the packet, but we divide the segment
```
| Header(N/W) | Header(T/L) | Data |
| Header(N/W) | Data |
| Header(N/W) | Data |
```
- Above shown is packet divided into three fragments.
- As, we can see Header is there in every fragment so data of N/W in each fragment is 1480 bytes.
- Total 1518: 1480 N/W payload + 20 N/W header + 18 DLL Header.
- Segmentation is always done at the source, fragmentation is not done at all. Segmentation is done in such a way that we don't have need to do further fragmentation.
- So following steps are done
  - bits of data at application layer
  - Segmentation takes place at transport layer
    - Each block payload is of 1460 bytes
    - 20 bytes of TCP header is added.
  - 20 bytes of Network header is added.
  - Now, 18 bytes of DLL header is added.
- This is how 1518 byte of frame is made.

## Who does the fragmentation?
- Fragmentation is done by the **Intermediate Router.**
- Routers do fragmentation because different networks have different MTU values.
- Each fragment is carried independently through different paths.
- Suppose MTU of one N/W is 500, and other is 200 then fragmentation is required.