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
### Urgent Data
- TCP is a stream oriented protocol.
- Data are presented from application to TCP as stream of bytes, each byte has position in stream.
- Sometimes application needs to send urgent bytes, means program needs piece of data to be read out of oreder by receiving application program.
#### Example
- Suppose sending application is sending data to be processed by receiving application.
- When the result of processing comes back, sending application finds everything is wrong.
- It wants to abort the process, but there is already huge data  in the buffer.
- It issues (ctrl + C) command to stop, but this will be stored at the end of the queue.
- It will be delivered to receiving application program after all data have been processed.
- The solution is to send with IRG bit set.
- Application program tells sending TCP that piece of data is urgent.
- Sending TCP creates a segment and inserts the urgent data at beginning of the segment.
- Rest segment can contian normal data of buffer.
- The urgent pointer field in header defines the end of urgent data and start of normal data.
- The receiving TCP receives a segment with URG bit set, it extracts the urgent data from segment, using value of urgent pointer, and delivers them out of order to receiving application program.

### RST Flag
- It is used when anyone peer want to reset the connection in case if it is closed or the packet which was required instead of that some other packet arrived.
#### Example
- If Client was sending packets to server, but meanwhile the server shutdown and restart.
  - Now, server after restarting without any connection establishment gets data packet from client, then server responds with RST packet.
  - **C-S:-** SN:2000, data, ACKNo:1001, ACK:1
  - **S-C:-** SN:1001, RST, ACKNo:2001
- No SYN and No ACK is set with RST flag set.

## Question
URG flag =1; SN=1000; URGP:100, what is byte no. of last byte of ugrent data and how many bytes are delivered out of order to receiver Application program.

### Solution
- Last byte no: 1000 + 100 = 1100
- Total 101 bytes received out of order (1000 - 1100)