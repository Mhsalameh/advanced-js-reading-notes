# Acess Control & Access Control List (ACL)

- Access Control:
  - Methods used to secure data and information by verifying a user has permissions to read, write , delete or otherwise modify it
- Acess Control Models:
  - DAC (Discretionary Access Control)
    - Access control policy is determined by the owner, DAC is commenly used!
    - Every object in a system must have an owner and each owner determines access rights and permissions for each object
  - MAC (Mandatory Access Control)
    - Computer chooses the permissions and access control of system objects MAC uses rule-based and lattice-based access control methods
    - Rule-base access control
      - compares object labels and subject labels and define whether to give access or not
    - Lattice-base access control
      - Uses complex mathematics to create sets of objects and subjects to define how they interact
      - Only used in high security systems due to its copmlex configuration
    - MAC is a feature in **FreeBSD & SELinux**
  - RBAC (Role-Base Access Control)
    - It's controlled by the system but utilizes a set of permissions instead of single data label to define the permission level
    - Power Users is a role-based permission
  - ABAC (Attribute-Based Access Control)
    - An access control model that is dynamic and context-aware using IF-THEN statements
    - if someone is in HR then give him access to /fileserver/HR

## Review, Research, and Discussion

- encryption
  - It's the process of turning a plaintext into a ciphertext using encryption algorithms
- token
  - it's a string that is generated when signed in and it's used to allow authorize users to get access to an endpoint with their specific data
- bearer
  - bearer token is sent by the front end and when decrypted using a secret key will give out a unique id or username that idintifies the user who is signed in
- secret
  - It's a secret key that is used to generate or verify a token using JWT library
- JSON Web Token
  - JWT library is used to generate or verify tokens using methods like `jwt.sign()` and `jwt.verify()`

## RBAC tutorial

- Role-based access control (RBAC) is a policy-neutral access-control mechanism defined around roles and privileges. The components of RBAC such as role-permissions, user-role and role-role relationships make it simple to perform user assignments. A study by NIST has demonstrated that RBAC addresses many needs of commercial and government organizations.[4] RBAC can be used to facilitate administration of security in large organizations with hundreds of users and thousands of permissions. Although RBAC is different from MAC and DAC access control frameworks, it can enforce these policies without any complication.
- Within an organization, roles are created for various job functions. The permissions to perform certain operations are assigned to specific roles. Members or staff (or other system users) are assigned particular roles, and through those role assignments acquire the permissions needed to perform particular system functions. Since users are not assigned permissions directly, but only acquire them through their role (or roles), management of individual user rights becomes a matter of simply assigning appropriate roles to the user's account; this simplifies common operations, such as adding a user, or changing a user's department. Role based access control interference is a relatively new issue in security applications, where multiple user accounts with dynamic access levels may lead to encryption key instability, allowing an outside user to exploit the weakness for unauthorized access. Key sharing applications within dynamic virtualized environments have shown some success in addressing this problem.[5]

Three primary rules are defined for RBAC:

1. Role assignment: A subject can exercise a permission only if the subject has selected or been assigned a role.
2. Role authorization: A subject's active role must be authorized for the subject. With rule 1 above, this rule ensures that users can take on only roles for which they are authorized.
3. Permission authorization: A subject can exercise a permission only if the permission is authorized for the subject's active role. With rules 1 and 2, this rule ensures that users can exercise only permissions for which they are authorized.

## Bookmarks

- [RBAC video by udecity](https://www.youtube.com/watch?v=C4NP8Eon3cA)
- [5 steps for RBAC](https://www.csoonline.com/article/3060780/5-steps-to-simple-role-based-access-control.html)
- [RBAC wiki](https://en.wikipedia.org/wiki/Role-based_access_control)
