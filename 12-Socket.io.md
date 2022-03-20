# socket.io

## questions

1. What is the benefit of transforming data into packets?
   - This is an efficient way of transfering data over networks and it limits latency.
2. UDP is often refereed to as a connectionless protocol. Why is this?
   - This is because with UPD no connection needs to be established between the origin and destination before tranferring data.
3. Can a socket server application have multiple socket connections?
   - Yes, multiple client sockets can be bound to the same local IP/port pair at the same time.
4. Can a socket connection application be connected to multiple socket servers?
   - the socket server can listen to multiple ports, but I think that the application can only be connected to a single scoket server
5. Can an application be both a socket server and a socket connection?
   - You can use the same socket for whatever you want, as long as your protocol handles it.

## Vocabulary-Terms

- OSI Model
  - OSI stands for Open System Interconnection. It is a conceptual framework for understanding the networking process. The seven layers of OSI are Physical, Data Link, Network, Transport, Session, Presentation, and Application.
- TCP Model
  - This is a more concise version of the OSI Model, and it consists of four layers: Application, Transport, Internet, and Network.
- TCP
  - This stands for Transmission Control Protocol. In this, the server must be listening for connections from clients.
- UDP
  - This stands for User Datagram Protocol. Unlike TCP, there is no need to establish a connection before transfering data.
- Packets
  - A unit of data that goes from one place to another over a network.
- Socket
  - A socket is an endpoint for sending and receiving data. Sometimes this refers to an internet socket, where a socket is identified to other hosts by its socket address.

## Web Sockets

The WebSocket API is an advanced technology that makes it possible to open a two-way interactive communication session between the user's browser and a server. With this API, you can send messages to a server and receive event-driven responses without having to poll the server for a reply
WebSockets typically run from browsers connecting to Application Server over a protocol similar to HTTP that runs over TCP/IP. So they are primarily for Web Applications that require a permanent connection to its server. On the other hand, plain sockets are more powerful and generic

## Socket.io

Socket.IO is the popular javascript library that helps us to create a real-time web application. With the help of it, we can manage the real-time, bidirectional and event-based communication between two applications. It works on every platform, browser or device, focusing equally on reliability and speed

Socket.IO allows bi-directional communication between client and server. Bi-directional communications are enabled when a client has Socket.IO in the browser, and a server has also integrated the Socket.IO package. While data can be sent in a number of forms, JSON is the simplest.

## bookmarks
- [video - OSI mode explained](https://www.youtube.com/watch?v=vv4y_uOneC0)
- [video - TCP Handshakes Explained](https://www.youtube.com/watch?v=xMtP5ZB3wSk)
- [web sockets](https://en.wikipedia.org/wiki/WebSocket)
- [socket.io toturial](https://www.tutorialspoint.com/socket.io/)
- [sockets vs web sockets](https://www.educba.com/websocket-vs-socket-io/)
- [Socket.io Documentation](https://socket.io/docs/)
- [Socket.io Server API](https://socket.io/docs/server-api)
- [Socket.io Client API](https://socket.io/docs/client-api)
- [Socket Testing Tool](https://amritb.github.io/socketio-client-tool/)
