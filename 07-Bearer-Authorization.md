# Bearer Authorization
## Review, Research, and Discussion
1. What can you do with an authorization code?
- purchase, sell or transfer items, or to enter information into a security-protected space.
2. What can you do with an access token?
- Identifies the user, the user's groups, the user's privileges, and, in some cases, a particular application. In some instances, one may be asked to enter an access token rather than the usual password
3. What’s a benefit of using OAuth instead of your own basic authentication?
- to enable apps to obtain limited access (scopes) to a user's data without giving away a user's password. It decouples authentication from authorization and supports multiple use cases addressing different device capabilities.
##  Vocabulary Terms
- Client ID
    - The Client ID is a public identifier of your application
- Client Secret
    - The Client Secret is confidential and should only be used to authenticate your application and make requests to LinkedIn's APIs
- Authentication Endpoint
    -  a security mechanism designed to ensure that only authorized devices can connect to a given network, site or service.
- Access Token Endpoint
    - where apps make a request to get an access token for a user.
- API Endpoint
    - a point at which an API -- the code that allows two software programs to communicate with each other -- connects with the software program.
- Authorization Code
    - a temporary code that the client will exchange for an access token.
- Access Token
    - An access token is an object encapsulating the security identity of a process or thread. A token is used to make security decisions and to store tamper-proof information about some system entity.

## JWT
- JWT, or JSON Web Token, is an open standard used to share security information between two parties a client and a server. 
- Each JWT contains encoded JSON objects, including a set of claims.
- JWTs are signed using a cryptographic algorithm to ensure that the claims cannot be altered after the token is issued
- A JSON web token (JWT) is a JSON object that is used to send information securely over the internet (between two parties). It can be used as an authentication mechanism as well as a means of exchanging data. The header, payload, and signature make up the majority of the token.

## Are JWTs Secure?
- Local storage is not as secure as using cookies (reference) but cookies can be subject to CSRF or XSRF exploits. Some people think JWT was safer than cookies, because cookies were subject to CSRF attacks. But storing JWT in local storage is not safe either.
- Although JWT does eliminate the database lookup, it introduces security issues and other complexities while doing so. Security is binary—either it's secure or it's not. Thus making it dangerous to use JWT for user session