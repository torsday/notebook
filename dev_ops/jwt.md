# JSON Web Token (JWT)

An open standard ([RFC 7519](https://tools.ietf.org/html/rfc7519)) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.

The information is digitally signed using a secret (with HMAC algorithm) or a public/private key pair using RSA.

-   Compact: Because of its size, it can be sent through an URL, POST parameter, or inside an HTTP header. Additionally, due to its size its transmission is fast.
-   Self-contained: The payload contains all the required information about the user, to avoid querying the database more than once.

## Uses

### Authentication

This is the typical scenario for using JWT, once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used among systems of different domains.

### Information Exchange

JSON Web Tokens are a good way of securely transmitting information between parties, because as they can be signed, for example using public/private key pairs, you can be sure that the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't changed.

## Structure

JSON Web Tokens consist of three parts separated by dots (.), which are:

-   Header
-   Payload
-   Signature

Therefore, a JWT typically looks like the following.

xxxxx.yyyyy.zzzzz

### Header

The header typically consists of two parts:

1. the type of the token, which is JWT
2. the hashing algorithm such as HMAC SHA256 or RSA.

For example:

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

Then, this JSON is Base64Url encoded to form the first part of the JWT.

### Payload



### Signature






## References

-   [JWT.io](https://jwt.io)
-   [SlideShare: JWT Authentication with AngularJS](http://www.slideshare.net/robertjd/jwt-authentication-with-angularjs)
