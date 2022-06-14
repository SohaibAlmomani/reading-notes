# Reading: Bearer Authorization

# JSON Web Token (JWT)

## Install :

```
npm install jsonwebtoken
```

## What is JSON Web Token?

- It is an open standard.
- Securely transfer information between any two bodies (users).
- Digitally signed >> Information is verified and trusted.
- Compact :
  - JWT can be sent via URL, POST request and HTTP headers.
  - Fast transmission.
- Self-contained :
  - Contains information about the user.
  - Avoiding query the database more than once.

## JWT is Useful When to use?

- Authentication
- Information Exchange

## JWT Structure

- Header: `a`
- Payload: `b`
- Signature: `c`
  Therefore, a JWT typically looks like the following :
  `aaaaa.bbbbb.ccccc`

### Header

Two parts:

- Type of the token.
- Signing algorithm being used, such as HMAC SHA256 or RSA.

example:

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

Then, this JSON is `Base64Url` encoded to form the first part of the JWT.

### Payload

The second part of the token is the payload, which contains the claims. `Claims` are statements about an entity (typically, the user) and additional data. There are three types of claims:

- Registered claims.
- Public claims.
- Private claims.

example :

```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```

### Signature

To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

For example if you want to use the HMAC SHA256 algorithm, the signature will be created in the following way:

```json
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

### Putting all together

The output is three Base64-URL strings separated by dots that can be easily passed in HTML and HTTP environments, while being more compact when compared to XML-based standards such as SAML.

The following shows a JWT that has the previous header and payload encoded, and it is signed with a secret :

![encoded-jwt3.png](./assets/encoded-jwt3.png)

If you want to play with JWT and put these concepts into practice, you can use jwt.io Debugger to decode, verify, and generate JWTs.

![legacy-app-auth-5.png](./assets/legacy-app-auth-5.png)

## How do JWT work?

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

```js
Authorization: Bearer <token>
```

## Bookmark and Review

- [npm jsonwebtoken docs](https://www.npmjs.com/package/jsonwebtoken)

## References:

- [JWTs Explained](https://www.youtube.com/watch?v=926mknSW9Lo)

- [Intro to JWT](https://jwt.io/introduction/)

- [Are JWTs Secure?](https://stackoverflow.com/questions/27301557/if-you-can-decode-jwt-how-are-they-secure)
