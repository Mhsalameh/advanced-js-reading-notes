# Authorization/Authentication

## Review, Research, and Discussion

1. What header(s) are used in authentication and authorization
    - In Authorization headers of the request, there will be `Basic encoded username:password` and `Bearer "token"`
2. What is safe to put into a JWT
    - JWT is a combination of a secret key and a unique identifyer like username or ID.
3. How are JWTs validated
    - Using the SECRET we can verify if the user that is requesting the path generated the same token when he signed in.

## Vocabulary Terms

- RBAC
    - Role-Based Access Control, It's controlled by the system but utilizes a set of permissions instead of single data label to define the permission level
- User Roles
    - defines which action can the user do in a specific path
- JWT Tokens
    - Token generated is an open standard used to share security information between two parties a client and a server