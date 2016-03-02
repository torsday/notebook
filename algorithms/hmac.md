# Hash-based message authentication code (HMAC)

*From: [Wikipedia](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)*

> A specific construction for calculating a message authentication code (MAC) involving a cryptographic hash function in combination with a secret cryptographic key. As with any MAC, it may be used to simultaneously verify both the data integrity and the authentication of a message. Any cryptographic hash function, such as MD5 or SHA-1, may be used in the calculation of an HMAC; the resulting MAC algorithm is termed HMAC-MD5 or HMAC-SHA1 accordingly. The cryptographic strength of the HMAC depends upon the cryptographic strength of the underlying hash function, the size of its hash output, and on the size and quality of the key.

> An iterative hash function breaks up a message into blocks of a fixed size and iterates over them with a compression function. For example, MD5 and SHA-1 operate on 512-bit blocks. The size of the output of HMAC is the same as that of the underlying hash function (128 or 160 bits in the case of MD5 or SHA-1, respectively), although it can be truncated if desired.

> The definition and analysis of the HMAC construction was first published in 1996 by Mihir Bellare, Ran Canetti, and Hugo Krawczyk,[1] who also wrote RFC 2104. This paper also defined a variant called NMAC that is rarely, if ever, used. FIPS PUB 198 generalizes and standardizes the use of HMACs. HMAC-SHA1 and HMAC-MD5 are used within the IPsec and TLS protocols.

## References

-   [Wikipedia: HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)
