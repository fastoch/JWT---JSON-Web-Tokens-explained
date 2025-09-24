src = https://www.youtube.com/watch?v=Y2H3DXDeS3Q  

# Introduction

## Understanding Authentication & Authorization

**Authentication** is the process of identifying a user through their credentials.  

Upon successful authentication, the user will be issued 2 things:
- the refresh token
- the access token

The access token is a **JWT** (JSON Web token), and it's used for **authorization**.  
**Authorization** is the process of ensuring the user is granted access to the resource/service they're trying to access.  

The Authorization part is where many applications use JWTs.  
These tokens are usually provided in the **Authorization Header** as a bearer token.  

# Anatomy of a JSON Web Token

<img width="681" height="92" alt="image" src="https://github.com/user-attachments/assets/5c9d9472-8feb-47c6-8098-ae6a037a595e" />

It consists of 3 parts:
- the **header**: contains metadata about the token like its type and the algorithm that is used to create the signature
- the **payload**, which includes fields such as:
  - the token issuer (where does the token come from),
  - the subject (e.g., userId),
  - the expiry time (Unix timestamp of when this token is not valid anymore),
  - the issuedAt (**iat**) timestamp of when the token was created
  - and other fields needed for your application, such as the user email and role (access level)...
- the **signature**

## The signature

When a JWT is issued to a user, the authenticating server (the issuing authority) needs to sign that token.  
The signature is a mechanism to ensure that the payload can be trusted.  

### How does it work?

- The server takes some secret key, to which it adds the header and the payload
- Then, it runs these 3 things through a hashing function to output the signature

The signature is just a hash that is created based on the header + payload + secret key.  
That signature is included in the token itself.  

### How do we verify the signature of JSON Web Token?

- When verifying a JWT, the receiver uses the same secret key and hashing algorithm to re-compute the HMAC (hash message authentication code) over the header and payload. 
- Then it compares this recomputed signature with the signature presented in the JWT.  
- If and only if both signatures match, it proves that the JWT is valid and unaltered.
- If signatures don't match, then the authorization fails

# JWTs are stateless

The JWT is sent as part of each and every HTTP request, most commonly in the Authorization header using the Bearer schema.  

JWTs are called **stateless** because the token itself carries the full information needed for authentication, removing the requirement for the server to keep user session state.

# Why do we need refresh tokens?

JWTs need to be very short-lived (a few minutes), because if a JWT is compromised, an attacker could use it to access resources until the token expires.  
Every time a token expires, a request is automatically being sent to refresh that token.  

The refresh token we've mentioned earlier is saved in the database and associated with the user ID (or with the session or device).  
That way, whenever the access token (JWT) expires, the user can provide their refresh token to ask for a new access token.  

# How to secure the refresh token?

- by renewing (rotating) the refresh token after each refresh request
- 

@7:32/9:17
