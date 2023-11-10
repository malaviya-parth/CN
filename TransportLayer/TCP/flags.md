## Control Flags in TCP
- There are 6 control flag in TCP
- `|URG|ACK|PSH|RST|SYN|FIN|`
- Suppose control field of TCP has value $(24)_{10}$ then,
  - ACK and PSH flags are set.
- If only RST is set then control field value will be,
  - $(000100)_{2}$ = $(4)_{10}$
### PSH flag
- Generally sending TCP wait for 1MSS data from application layer & only then it apply header and make segment.
  - This is done because if data is less say 1 byte and + 20 byte header(TCP) + 20 byte header(IP) is applied still payload for ether is 41 bytes will it requires minimum 46 bytes because minimum frame size of Ehternet is 64 byte.
  - Somehow after padding we made Ethernet frame of 64 bytes but in this 64 bytes of frame just 1 byte of data is sent which reduces efficiency.
- Sometimes, we need even small data to be sent, like while chatting you send "Hi" considering each char of 1 byte it is just 2 bytes of data, but this data we need to send it immediately and hence here PSH flag is used.
- If TCP wait for 1MSS and then make segment, it will look like an email & not chat to other person
  - So, packet is sent immediately as well as receiving TCP also process the packet quickly and not wait for more data to come..
- Interactive chat applications do not need efficiency from TCP rather real time data transfer is priority.
- This PSH request can be ignored as well, depends upon TCP to choose this feature or not.