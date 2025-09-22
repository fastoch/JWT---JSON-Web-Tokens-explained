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



@1:37
