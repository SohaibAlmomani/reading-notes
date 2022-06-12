# Authentication :

Authentication : is the process of verifying that an individual, entity or website is whom it claims to be. Authentication in the context of web applications is commonly performed by submitting a username or ID and one or more items of private information that only a given user should know.

Session Management : is a process by which a server maintains the state of an entity interacting with it. This is required for a server to remember how to react to subsequent requests throughout a transaction. Sessions are maintained on the server by a session identifier which can be passed back and forward between the client and server when transmitting and receiving requests.

## Basic access authentication :

In the context of an HTTP transaction, basic access authentication is a method for an HTTP user agent (e.g. a web browser) to provide a user name and password when making a request. In basic HTTP authentication, a request contains a header field in the form of `Authorization: Basic <credentials>`, where credentials is the Base64 encoding of ID and password joined by a single colon :  .

HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it does not require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header.

HTTP does not provide a method for a web server to instruct the client to "log out" the user. However, there are a number of methods to clear cached credentials in certain web browsers.

To clear cached credentials using JavaScript method :
~~~js
<script>document.execCommand('ClearAuthenticationCache');</script>
~~~
In modern browsers, cached credentials for basic authentication are typically cleared when clearing browsing history.

### Protocol :

- Server side :
    When the server wants the user agent to authenticate itself towards the server after receiving an unauthenticated request, it must send a response with a HTTP 401 Unauthorized status line and a WWW-Authenticate header field.
    
    `WWW-Authenticate: Basic realm="User Visible Realm", charset="UTF-8"`
    - This parameter indicates that the server expects the client to use UTF-8 for encoding username and password.

- Client side :
    When the user agent wants to send authentication credentials to the server, it may use the Authorization header field.

The Authorization header field is constructed as follows:

1. The username and password are combined with a single colon (:). This means that the username itself cannot contain a colon.

2. The resulting string is encoded into an octet sequence. the server may suggest use of UTF-8 by sending the charset parameter.

3. The resulting string is encoded using a variant of Base64 (+/ and with padding).\

4. The authorization method and a space (e.g. "Basic ") is then prepended to the encoded string.

## Authentication General Guidelines :

1. User IDs :
Make sure your usernames or user IDs are case-insensitive. User 'sohaib' and user 'Sohaib' should be the same user. Usernames should also be unique. For high-security applications, usernames could be assigned and secret instead of user-defined public data.

2. Authentication Solution and Sensitive Accounts :

- Do NOT allow login with sensitive accounts (i.e. accounts that can be used internally within the solution such as to a back-end / middle-ware / DB) to any front-end user-interface.
- Do NOT use the same authentication solution (e.g. IDP / AD) used internally for unsecured access (e.g. public access / DMZ).

## Password Strength Controls :
A key concern when using passwords for authentication is password strength. A "strong" password policy makes it difficult or even improbable for one to guess the password through either manual or automated means.

### The following characteristics define a strong password:

- Password Length :
    - Minimum length of the passwords should be enforced by the application. Passwords shorter than 8 characters are considered to be weak .
    - Maximum password length should not be set too low, as it will prevent users from creating passphrases. It is important to set a maximum password length to prevent long password Denial of Service attacks.

- Do not silently truncate passwords.
- Allow usage of all characters including unicode and whitespace. There should be no password composition rules limiting the type of characters permitted.
- Ensure credential rotation when a password leak, or at the time of compromise identification.
- Include password strength meter to help users create a more complex password and block common and previously breached passwords
- Pwned Passwords is a service where passwords can be checked against previously breached passwords. You can host it yourself or use API.

## Implement Secure Password Recovery Mechanism :
It is common for an application to have a mechanism that provides a means for a user to gain access to their account in the event they forget their password.

## Store Passwords in a Secure Fashion :

It is critical for an application to store a password using the right cryptographic technique. 

# Hashing algorithm :

Passwords are the first line of defense against cyber criminals. It is the most vital secret of every activity we do over the internet and also a final check to get into any of your user account.

Cryptographic hash algorithms MD5, SHA1, SHA256, SHA512, SHA-3 are general purpose hash functions, designed to calculate a digest of huge amounts of data in as short a time as possible. 

Hashing is the greatest way for protecting passwords and considered to be pretty safe for ensuring the integrity of data or password.

The benefit of hashing is that if someone steals the database with hashed passwords, they only make off with the hashes and not the actual plaintext passwords. 

### Problems with cryptographic Hash algorithm :

- Brute Force attack:
 Hashes can't be reversed, so instead of reversing the hash of the password, an attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value, called brute force attack.

- General-purpose hash function designed for speed,because they are often used to calculate checksum values for large data sets and files, to check for data integrity.

    Using a modern computer one can crack a 16 Character Strong password in less than an hour, thanks to GPU.

- Hash Collision attack:
 Hash functions have infinite input length and a predefined output length, so there is inevitably going to be the possibility of two different inputs that produce the same output hash. MD5, SHA1, SHA2 are vulnerable to Hash Collision Attack i.e. two input strings of a hash function that produce the same hash result.

### what exactly could be a good for securing your passwords with hashing?

- BCrypt :
To overcome such issues, we need algorithms which can make the brute force attacks slower and minimize the impact.it use a technique called Key Stretching.

- Bcrypt is an adaptive hash function based on the Blowfish symmetric block cipher cryptographic algorithm and introduces a work factor (also known as security factor), which allows you to determine how expensive the hash function will be.

This work factor value determines how slow the hash function will be, means different work factor will generate different hash values in different time span, which makes it extremely resistant to brute force attacks. When computers become faster next year we can increase the work factor to balance it out i.e. to make the attack slower.

## Compare Password Hashes Using Safe Functions :

The user-supplied password should be compared to the stored password hash using a secure password comparison function provided by the language or framework. 

- Comparison function:
    - Has a maximum input length, to protect against denial of service attacks with very long inputs.
    - Explicitly sets the type of both variable, to protect against type confusion attacks such as Magic Hashes in PHP.
    - Returns in constant time, to protect against timing attacks.

## Logging and Monitoring :
Enable logging and monitoring of authentication functions to detect attacks/failures on a real-time basis

- Ensure that all failures are logged and reviewed
- Ensure that all password failures are logged and reviewed
- Ensure that all account lockouts are logged and reviewed

## Use of authentication protocols that require no password :

- OAuth
- OpenId
- SAML
- FIDO

## node.bcrypt.js :

A library to help you hash passwords.

# References :

- [OWASP auth cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [bcrypt docs](https://www.npmjs.com/package/bcrypt)
- [Securing Passwords](https://thehackernews.com/2014/04/securing-passwords-with-bcrypt-hashing.html)
- [Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication)

