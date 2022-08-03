### How it works
1) User authenticates with user id and password for the first time
2) Server authenticates the user
3) Server creates a JWT token
4) JWT is passed to the client
5) Client saves JWT either on local storage or cookie
6) JWT is sent with the HTTP header with key "authorization" and value "Bearer JWT"

### Structure
![image](https://user-images.githubusercontent.com/44560576/182671240-4ff1f104-f0db-4767-b664-e9048d00517a.png)

### How it guarantees integerity
1) If someone modifies the payload, the hash value of header + payload won't match with the original hash (3rd portion)
2) Only the server has the key used for hashing with HMACSHA256, so fake hashes cannot be generated.

### Note that
1) Header and payload are merely base64 encoded and are open information. Must not include sensitive info
2) It is useful compared to other stateful mechanisms 
3) Traditionally, after authentication, server creates a session and passes the session ID, which gets saved in cookie. This session ID + cookies don't work nice when multiple instances are working with load balancer as it's hard to propagate sessions.
4) JWT is not an authentication method itself, it's a mechanism for interaction after the authentication has been finished.
