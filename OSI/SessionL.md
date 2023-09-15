# Session Layer
- It is also known as the **dialogue control layer**.
- It is responsible for **establishing, managing and terminating** the connections between the local and remote application.
- It is also responsible for **synchronizing** the dialogue between the presentation layer entities and **managing their data exchange**.

## Functions of Session Layer

1. **Session establishment**: It allows two application processes on different machines to **establish, use and terminate** a connection called a **session**.

2. **Network dialog control**: It establishes, maintains, synchronizes and terminates the interaction between sender and receiver processes.

3. **Syncrhonization of data**: It adds some synchronization bits to the message & this this bits are used as a **check point** for the data transfer.

4. **Token Management**: Cookies or Tokens are generated at server side & sent to client, So next time when client sends request to server, it sends the token along with the request. Server verifies the token & sends the response.

5. **Authentication & Authorization**: It verifies the credentials of the user & authorizes the user to access the resources. 