# Message Queues

## questions

1. What does it mean that web sockets are bidirectional? Why is this useful?
    - means that the client can communication to the socket server and vise versa
2. Does socket.io use HTTP? Why?
    - the client side uses HTTP protocol to communicate with the server side using either port (443 or 80)
3. What happens when a client emits an event?
    - the server will be listening to that event and trigger the callback function
4. What happens when a server emits an event?
    - clients connected to that server will be listenening and trigger a callback function on the client side
5. What happens if a client “misses” an event?
    - a client will not trigger the event and might include security issues
6. How can we mitigate this?
    - we need to buffer the events before emitting anything

## Vocabulary Terms

- **Socket**: Sockets allow communication between two different processes on the same or different machines.
- **Web Socket**: WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection
- **Socket.io**: Socket.IO is a library that enables low-latency, bidirectional and event-based communication between a client and a server
- **Client**: The clients run programs and access data that are stored on the server. Compare peer-to-peer network
- **Server**:  A computer program or device that provides a service to another computer program and its user, also known as the client.
- **OSI Model**: The OSI Model Defined. The OSI Model (Open Systems Interconnection Model) is a conceptual framework used to describe the functions of a networking system
- **TCP Model**: The TCP/IP Protocol Stack is made up of four primary layers: the Application, Transport, Network, and Link layers (Diagram 1). Each layer within the TCP/IP protocol suite has a specific function. When the layers of the model are combined and transmitted, communication between systems can occur.
- **TCP**: The Transmission Control Protocol (TCP) is a transport protocol that is used on top of IP to ensure reliable transmission of packets
- **UDP**: User Datagram Protocol (UDP) is a communications protocol that is primarily used to establish low-latency and loss-tolerating connections between applications on the internet.
- **Packets**: A packet is a small segment of a larger message. Data sent over computer networks*, such as the Internet, is divided into packets. These packets are then recombined by the computer or device that receives them.

## Chat example

Sockets have traditionally been the solution around which most real-time chat systems are architected, providing a bi-directional communication channel between a client and a server.<br/>
This means that the server can push messages to clients. Whenever you write a chat message, the idea is that the server will get it and push it to all other connected clients.

- The web framework
  The first goal is to set up a simple HTML webpage that serves out a form and a list of messages. We’re going to use the Node.JS web framework express to this end. Make sure Node.JS is installed.

```js
const express = require("express");
const app = express();
const http = require("http");
const server = http.createServer(app);

app.get("/", (req, res) => {
  res.send("<h1>Hello world</h1>");
});

server.listen(3000, () => {
  console.log("listening on *:3000");
});
```

- Integrating Socket.IO

```js
const express = require("express");
const app = express();
const http = require("http");
const server = http.createServer(app);
const { Server } = require("socket.io");
const io = new Server(server);

app.get("/", (req, res) => {
  res.sendFile(__dirname + "/index.html");
});

io.on("connection", (socket) => {
  console.log("a user connected");
});

server.listen(3000, () => {
  console.log("listening on *:3000");
});
```

Each socket also fires a special disconnect event:

```js
io.on("connection", (socket) => {
  console.log("a user connected");
  socket.on("disconnect", () => {
    console.log("user disconnected");
  });
});
```

## Bookmarks

[chat example](https://socket.io/get-started/chat/)
[rooms](https://socket.io/docs/v4/rooms/)
[namespaces](https://socket.io/docs/v4/namespaces/)
[emit-cheatsheet](https://socket.io/docs/v4/emit-cheatsheet/)
