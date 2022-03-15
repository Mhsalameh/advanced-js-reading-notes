# Event-Driven-Application

## questions

1. Why is access control important?
   - to increase the security posture of a web application, and to implement authorization concepts for different end points
2. Describe an application that would need access control.
   - any website that has an authentication process needs access contorl to identify users from admins
3. What is a role used for?
   - role is used to identify the role of a user and which actions they are permitted to do
4. Why is role based access control more scalable than discretionary or mandatory access control?
   - DAC: Access control policy is determined by the owner, DAC is commenly used
   - MAC: compares object labels and subject labels giving permission depending on the secrecy of the subject
   - RBAC: it's more broad and each role has access to different path.

## Vocabulary Terms

- Authorization
  - Occurs when a user is given access to a certain piece of data or certain areas of building
- Role Based Access Control
  - It's controlled by the system but utilizes a set of permissions instead of single data label to define the permission level
- Capabilities
  - system which functions to realize content, collaboration, communication, customer relations, resource planning, finance and monitoring applications. The purpose of the applications capability is to enable and assure the abilities of the IT applications of the enterprise.

## Event Driven Programming

system which functions to realize content, collaboration, communication, customer relations, resource planning, finance and monitoring applications. The purpose of the applications capability is to enable and assure the abilities of the IT applications of the enterprise.
Every time you interact with a webpage through it’s user interface, an event is happening. When you click a button a click event is triggered. When you press a key a keydown event is triggered. These events have associated functions that, when triggered, are executed to make a change to the user interface in some way

- EventEmitter
  We access the EventEmitter class through the events module. Once imported we’ll need to create a new object from the class to start using it.
  Node.js natively provides us with a useful module called EventEmitter that allows us to get started incorporating Event-Driven Programming in our project right away. Of course, creating our own version of EventEmitter wouldn’t be much of a challange, and in fact there are several modules published on npm such as EventEmitter2 and EventEmitter3 which promise a faster performance than the native EventEmitter.

```
const EventEmitter = require('events').EventEmitter;
const myEventEmitter = new EventEmitter;
function userJoined(username){
  // Assuming we already have a function to alert all users.
  alertAllUsers('User ' + username + ' has joined the chat.');
}

// Run the userJoined function when a 'userJoined' event is triggered.
chatRoomEvents.on('userJoined', userJoined);
```

We could expand further by creating events for when a user logs out, when a message is sent, when a message is received, or any other event we could possibly need for our chat room to be as dynamic as we want it.

## bookmarks
- [Event Driven Programming](https://alligator.io/nodejs/event-driven-programming/)
- [Node docs: events](https://nodejs.org/api/events.html)
