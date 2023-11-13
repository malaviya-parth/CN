## Electronic Mail
- At the beginning of the Internet era, the messages sent by electronic mail were short and consisted of text only. Today, electronic mail is much more complex. It allows a message to include text, audio, and video. It also allows one message to be sent to one or more recipients.
### Architecture
- Tp explan the architecture of e-mail, we give **four scenarios.** we begin with the simplest situation and add complexity as we proceed. The foruth scenario is the most common in the exchange of email.
### First Scenario
- In the first scenario, the sender and the receiver of the email are users (or application programs) on the **same system;** they are directly connected to a shared system.
![Alt text](image-5.png)
- The administrator has created one **mailbox** for each user where the received messages are stored. A mailbox is a part of **local hard drive**, a spcial file with permission restrictions.
- Only the owner of the mailbox has **access** to it.
- When Alice, a user, needs to send a message to Bob, Alice runs a **user agent** program to prepare the message and **UA itself** will store it in Bob's mailbox.
- The message has the sender and receipient mailbox addresses (names of files).
- Bob can retrieve and **read the content** of his mailbox at his convenience, **using a user agent**
- Consider UA is **Gmail interface.**
- The computer are directly connected to the mail servers.
- ***NOTE:*** When the sender and the receiver of an e-mail are on the same system, we need only two User Agents.
### Second Scenario
- Bob can retireve and **read the contents** of his mailbox at his convenince, **using a user agent.**
![Alt text](image-6.png)
- Here if ALice is connected to google server
- Bob is connected to yahoo server
- Both are directly connected to the servers
- Alice sends mail to it's server which is stored in a **mail queue**to store messages waiting to be sent.
- MTA client keeps on checking the queue and when there is message then it will try to establish connection with MTA server and when connection is established then it pick the messages from queue and send them over internet to MTA server which is running at system from which Bob is connected.
- MTA server after receiving messages will store them at mail box of Bob.
- Like most client/server programs on the Internet, the server needs to run all the time because it don't know when a client will ask for a connection.
- Bob also needs a **user agent** program to retrieve messages stroed in the mailbox of the system at server site.
- ***NOTE:*** Here we need a pair of User Agents as well as a pair of Message Transfer Agents.
### Third Scenario
- Here receiver is directly connected to mail server but the sender is not directly connected to the mail server.
![Alt text](image-7.png)
- Either Alice is connected to the system via point-to-point WAN, suxh as a dial-up modem, a DSL, or a cable modem; or connected to a LAN in  an organisation that uses one mail server for handling e-mails-all users need to send their messages to this mail server.
- Alice still needs a user agent tp prepare message. Then needs to send the message through the LAN or WAN. This can be done through a pair of message transfer agents.
- Whenever Alice has a message to send, she calls the user agent which, in turn, calls the MTA client. The MTA client establishes a connection with the MTA server on the system, which is running all the time.
- The mail server computer at Alice's site manages all messages received and makes a mail queue. MTA client keeps on checking this queue and whenever there are messages to send it establishes a connection with MTA server at Bob's site and sends the messages. This server receives the messages and stores it in Bob's mailbox.
- At his convenience, Bob uses his user agent to retrieve the message and reads it.
- ***NOTE:*** Here we need 2 User Agents and 2 pair(4) MTAs.
### Foruth Scenario
- Both the sender and receiver are not direclty connected to the mail server directly.
![Alt text](image-8.png)
- We can't use a MTA client at Bob computer MTA server at mail server computer. This is because MTA client **push program** whic hpushes the messages to MTA server, it can't pull message from the MTA server.
- Other option is use MTA server at Bob computer which is impossible as now Bob can't shut down computer because he doesn't know when message will arrive.
- Hence, we need another set of client/server agents which we call **Message Access Agents**.
- Unlike MTA client, MAA client is a **pull program** and it can pull messages from MAA server.
- So Bob uses MAA client to retrieve his messages. The client sends a request to the MAA server, which is running all the time, and requests the transfer of the messages.