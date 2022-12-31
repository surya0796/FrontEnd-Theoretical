HTTP vs WebScokets

How HTTP works? 
In HTTP protocol web browser establishes TCP connection with server after DNS resolution figures out request's IP address. This connection is duplex and requires some handshake between client and server. The client establishes a connection with server, requests an update, gets a response from the server, then closes the connection.

HTTP is stateless. Why?
The TCP connection allows both client and server to speak with each other, but HTTP don't, which means only one will request and other will respond to that request. HTTP is stateless because it helps to easily scale backend architecture via horizontal scaling. Stateless means Http server needs not keep track of any state information present inside headers. That means every time client requests something from server it has to send those headers to server to make it understand what it clearly wants. This makes efficient handling of client's request, as any of the server computer is able to answer that request. Now if the traffic on server increases you can add more servers in backend to cope up with it.

How websockets works?
Web sockets also works on TCP layer4 communication. The intial reuest sent by client is of HTTP connection request, which asks server taht can we have a websocket connection between us. If the server responds in affirmation there connection is upgraded to Websocket, and now both client and server can communicate freely with this duplex stateful connection. A connection being stateful has some disadvantages, the websockets once setup can send messages back-forth with that single server, as that server only knows who the client is. This creates a scalability problem which HTTP never faces. This problem is somewhat solved by AWS api-gateway.

Other differences between HTTP and Websockets :: Http requests are slower than websockets as they are used to send more data at a time than websockets.