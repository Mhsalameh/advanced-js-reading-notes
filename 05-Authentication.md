## Review, Research, and Discussion

1. Explain what a “Singleton” is (in Computer Science terms)
   - A singleton is a class that allows only a single instance of itself to be created and gives access to that created instance.
2. Explain how the Singleton pattern can be used with Node modules, specifically with classes
   - We can create a class with a method called getInstance that returns on instance of that class.
   ```
   class logger(){
       constructor (){
           this.log=[];
       }
       log(message) {
       const timestamp = new Date().toISOString();
       this.logs.push({ message, timestamp });
       console.log(`${timestamp} - ${message}`);
        }
   }
   class singleton(){
       constructor(){
           if (!singleton.instance){
               sington.instance = new logger();
           }
       }
       getInstance(){
           return singlton.instance;
       }
   }
   ```
3. If you were tasked with building a middleware system like Express uses, what approach might you take to construct/operate it?
   - I don't understand the question, if what you mean by approach singleton or non-Singleton, I would probably use a singlton approach to create only one instance of the app, and if an instance already exists I will just use the new instance instead. and for the express router I would use non-singleton approach.

## Vocabulary Terms

- Router Middleware
  - take the original request, and forward it to a sub handler according to the path example : "/home" for a GET request is mapped to function getHome that handle it and eventually send a response to the client on the behalf of the original handler
- Dynamic Module Loading
    - Dynamic loading is a mechanism by which a computer program can, at run time, load a library (or other binary) into memory, retrieve the addresses of functions and variables contained in the library, execute those functions or access those variables, and unload the library from memory.
- Singleton Pattern
    - The singleton pattern is a software design pattern that restricts the instantiation of a class to one "single" instance. 
- CRUD -> REST Method Matches
    | CRUD | REST API HTTP METHODS |
    | ----- | ----- |
    | Create | POST |
    | Read | GET |
    | Update | PUT |
    | Delete | DELETE|
- Mock Testing
    - Creating a fake version of an external or internal service that can stand in for the real one during the test.

## Authentication

- Authentication is when a person's idetity is proven with a proof and confirmed by a system
- proofs can be:
  1. something you know i.e. password, username, pin
  2. something you are i.e. fingerprint
  3. something you have i.e. smart card
  4. something you do i.e. segneture
  5. somewhere you are. i.e. gps location
- Authentication is part of the AAA triad which inlcudes
  - Authentication
  - Authorization
  - Accounting
- Authentication is a way to minimize attack surfaces on a web application.

## Securing passwords

- Passwords `something you know` part of the authentication, it is the first line of defense for our data.
- A strong password.
  - Contains uppercase letters, lowercase letters, numbers, special characters, and at least 8 characters or more (preferably 14 or more)
  - always require the user to change default passwords.
- We all know storing passwords in clear text in your database is ridiculous. Many desktop applications and almost every web service including, blogs, forums eventually need to store a collection of user data and the passwords, that has to be stored using a hashing algorithm
- Cryptography
  - The practice and study of writing and solving codes in order to hide the true meaning of information
  - encryption is process of converting plaintext to ciphertext
- Hashing
  - Hash
    - A one-way cryptographic function which takes an input and produces a unique messege digest
  - Message Digest 5 (MD5)
    - Algorithm that creates a fixed-length 128-bit has value unique to the input file
  - Collision
    - Condition that occures when two different files creates the same hash digest.
  - Secure Hash Algorithm (SHA-3)
    - Family of algorithms that creates hash digests between 224-bits and 512-bits

## Authentication Attacks

- Spoofing
- Man-in-the-middle Attack
- Password Sprying
- Credential Stuffing
- Broken Authentication
- dictionary attacks
- Brute-Force Attack
- Rainbow Table attack

## Basic Access Authentication

- HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it does not require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header.
- In the context of an HTTP transaction, basic access authentication is a method for an HTTP user agent (e.g. a web browser) to provide a user name and password when making a request. In basic HTTP authentication, a request contains a header field in the form of `Authorization: Basic <credentials>`, where credentials is the Base64 encoding of ID and password joined by a single colon `:`
  - In computer programming, Base64 is a group of binary-to-text encoding schemes that represent binary data (more specifically, a sequence of 8-bit bytes) in sequences of 24 bits that can be represented by four 6-bit Base64 digits.

## [OWASP auth cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)

- The **OWASP Cheat Sheet** Series was created to provide a concise collection of high value information on specific application security topics
- **Session Management** is a process by which a server maintains the state of an entity interacting with it. This is required for a server to remember how to react to subsequent requests throughout a transaction. Sessions are maintained on the server by a session identifier which can be passed back and forward between the client and server when transmitting and receiving requests.

## [bcrypt docs](https://www.npmjs.com/package/bcrypt)

- A library to help you hash passwords.
