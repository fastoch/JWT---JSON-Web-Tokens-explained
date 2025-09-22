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


@3:12
