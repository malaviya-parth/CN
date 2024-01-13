| Port Number | Protocol | Application |
| ----------- | -------- | ----------- |
| 20 | TCP | FTP DATA |
| 21 | TCP | FTP CONTROL |
| 22 | TCP | SSH |
| 23 | TCP | TELNET |
| 25 | TCP | SMTP |
| 53 | UDP,TCP | DNS |
| 67,68 | UDP | DHCP |
| 69 | UDP | TFTP |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP4 |

## GATE 2007
Which Application Layer protocol uses UDP?
1. HTTP
2. Telnet
3. DNS
4. SMTP

### Solution
- DNS

## GATE 2012
Which Transprot layer protocol is used to support Email?
1. SMTP
2. IP
3. TCP
4. UDP

### Solution
- TCP

## GATE 2013
Transport Protocol for reat time multimedia, file transfer, DNS & email respectively.
1. TCP, UDP, UDP & TCP
2. UDP, TCP, TCP & UDP
3. UDP, TCP, UDP & TCP
4. TCP, UDP, TCP & UDP

### Solution
- UDP, TCP, UDP, TCP

## Question
Match the following
| Protocol | Port |
| -------- | ---- |
| DNS | 23 |
| DHCP | 53 |
| IMAP | 67 |
| POP3 | 68 |
|    | 110 |
|    | 143 | 

### Solution
- DNS -> 53
- DHCP -> 67,68
- IMAP -> 143
- POP3 -> 110

## ⭐⭐⭐
| | DNS | HTTP | SMTP | POP | FTP | IMAP |
|-| --- | ---- | ---- | --- | --- | ---- |
| Stateless/Stateful | Stateless | Stateless | Stateful | Stateful | Stateful | Stateful |
| Transport Protocol | UDP/TCP | TCP | TCP | TCP | TCP | TCP |
| Connectionless/oriented | Connectionless | Connectionless | Connection Oriented | Connection Oriented | Connection Oriented | Connection Oriented |
| Persistent/Non-P | Non | 1.0-Non, 1.1-P | P | P | Control-P, Data-Non | P |
| Port | 53 | 80 | 25 | 110 | 20-data. 21-control | 143 |
| In band/Out-of-band | In | In | In | In | Out | In |

## GATE 2016
Stateful application layer protocol
1. HTTP
2. FTP
3. TCP
4. POP3

### Solution
- FTP, POP3
- TCP is also stateful but it is not application layer protocol

## GATE 2011
Consider thedifference activities related to email.
- m1: Send an email from mail client to mail server
- m2: Download an email from mailbox server to a mail client
- m3: Checking email in web browser
Which app. protocol is used in each activitiy?
1. HTTP,SMTP,POP
2. SMTP,FTP,HTTP
3. SMTP,POP,HTTP
4. POP,SMTP,IMAP

### Solution
- SMTP, POP/IMAP, HTTP

## GATE 2019
Which protocols to send and retrieve emails?

### Solution
- Send: SMTP
- Retrieve: POP3, IMAP4

## GATE 2005
Consider the three commands: PROMPT, HEAD and RCPT. They are related to which protocols?
1. HTTP, SMTP, FTP
2. FTP, HTTP, SMTP
3. HTTP, FTP, SMTP
4. SMTP, HTTP, FTP

### Solution
- FTP, HTTP, SMTP

## GATE 2016
HELO and PORT, are protocols from?
1. FTP and HTTP
2. TELNET and POP3
3. HTTP and TELNET
4. SMTP and FTP

### Solution
- SMTP and FTP

## GATE 2016
Identify the correct sequence in which the following packets are transmitted on the network by a host when a browser requests a webpage from a remote server, assuming that the host has just been restarted.
1. HTTP GET request, DNS query, TCP SYN
2. DNS query, HTTP GET request, TCP SYN
3. DNS query, TCP SYN, HTTP GET request.
4. TCP SYN, DNS query, HTTP GET request.

### Solution
- DNS query, TCP SYN, HTTP GET

## GATE 2020
Assume that you have made a request for a web page through your web browser to a web server. Initially the browser cache is empty. Further, the browser is configured to send HTTP requests in non-persistent mode. The web page contains text and five very small images. The minimum number of TCP connections required to display the web page completely in your browser is __.

### Solution
- 5 for small images, 1 for whole webpage: Minimum 6 connections are required.