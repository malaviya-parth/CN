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

## Identification
- The Identification field in the IP header is used to recognize whether the fragments belong to the same segment.
- IP protocol maintains a counter to enable the datagrams.
- THis counter is initialized by a +ve no. & is incremented whenever a datagram leaves a machine.
- When Datagram is fragmented then every field of header is copied & so is this field.[Except 3 field flags, FO & TL]
- Whenever 2 or more datagrams have same ID then this means they are fragmented datagrams of a single datagram.
- Combination of SIP & ID must uniquely define a datagram as it leaves the source host.

## Flag
- It is a 3 bit field.
- First one is reserved
- Second (D): Do not Fragment:
  - 0 means fragmentation can be done
  - 1 means fragmentation can't be done
- Third (M): More Fragment
  - 0 means it is last fragment
  - 1 means it is not last fragment

| D | F | Fragmentated | Last Fragment |
| - | - | ------------- | ------------- |
| 0 | 0 | Can't say | If fragment, then last |
| 0 | 1 | Yes | Not last |
| 1 | 0 | No | Last fragment |
- Last possibility of 11 do not exist due to contradiction.

## Fragmentation Offset
- It is a 13 bit field
- Suppose there is a segment of 2000 bytes
  - Now we are allowed maximum of 800 bytes so we need to do fragmentation
  - Fragments:
    - 0 - 799
    - 800 - 1599
    - 1600 - 1999
  - Fragment offsets:
    - $\frac{0}{8} = 0$
    - $\frac{800}{8} = 100$
    - $\frac{1600}{8} = 200$
- This fragment offset calculated are stored in 13 bits fragment offset field.

## Question
Sender needs to send 5000 byte data & fragmentation is done in such a way that 5 fragments are made of equal size. Find FO of 3rd fragment.

### Solution
- $1^{st}$ fragment: 0 - 999
- $2^{nd}$ fragment: 1000 - 1999
- $3^{rd}$ fragment: 2000 - 2999
- $4^{th}$ fragment: 3000 - 3999
- $5^{th}$ fragment: 4000 - 4999
- FO of 3rd fragment: $\frac{2000}{8}=250$

## Question
If the packet arrives with m bit value 0. Is it first, middle or last fragment? Can we say about fragmentation is done or not?

### Solution
- If m bit is 0, means more fragments are not there.
- So it for sure is last fragment
- But it can also be the first fragment if fragmentation is not done.
- We can't say anything about fragmentation since D bit is not provided and M bit is not set to 1.
- Also, value of fragmentation offset is not given else we can tell about fragmentation.

## Question
If the packet arrives with m bit value 0. Is it first, middle or last fragment? Can we say about fragmentation is done or not?

### Solution
- Since m bit is one, so it is not last fragment.
- Since it is not last fragment so fragmentation is surely done.
- Now if FO = 0, then first else middle.

## Question
If fragmentation is done, how to check whether fragment is $1^{st}$ or middle?

### Solution
- If Fragment Offset has value 0 then surely it is the first fragment.
- If Fragmentation Offset is != 0 and M bit is set to 1, then it is middle.

| FO | M | Fragmentation | Position |
| -- | - | ------------- | -------- |
| 0 | 0 | No | First/Last(Single block) |
| 0 | 1 | Yes | First |
| !=0 | 0 | Yes | Last |
| !=0 | 1 | Yes | Middle |

## Question
Fragmentation offset is 100, then find the first byte no. carried in the fragment. Can we find last byte No.?

### Solution
- First Byte: 100 * 8 = 800
- We can't find last byte number as we don't know size of fragment.

## Question
If FO = 100 & TL = 100. Can we find last byte No?

### Solution
- First byte = 100 * 8 = 800
- Still we can't find the last byte as we don't know the header length.
- If question encountered in GATE, consider minimum header length.
- If Data insufficient option present, tick that.

## Question
If FO = 100 & TL = 100, HLEN = 20. Can we find last byte No?

### Solution
- Fisrt byte = 800
- As Header Length is 20 so it would be included there in the fragment.
- Remaining 80 bytes of data will be there
  - So, Last byte = 800 + 79 = 879

## Question
If length of IP datagram is 1000 bytes & we need to make fragments of 100 bytes. How many fragments will be constructed assuming header is of 20 bytes.

### Solution
- As IP datagram is of 1000 byte and HLEN = 20, total data in it = 980.
- First fragment will have upto 100 bytes from the datagram.
- From second fragment onwards we can only have 80 bytes of data as 20 byte will always be present in that fragment as header.
  - Second Fragment = 180
  - Third Fragment = 260
  - So on...
- Number of fragments for 900 byte of data = $\frac{900}{80} = 12$\
- Total Fragments = 13
- The last fragment contains only 20 byte of data(80*11=880) + 20 byte of header.
- Total number of bytes sent = 1200 + 40 = 1240 bytes