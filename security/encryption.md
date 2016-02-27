# Encryption

## Cryptographic hash functions

A hash function which is considered practically impossible to invert, that is, to recreate the input data from its hash value alone.

### Checking Hashes

#### Calculate SHA-1 checksum

```sh
shasum -a 1 <file>
```

#### Calculate SHA-256 checksum

```sh
shasum -a 256 <file>
```

#### Calculate SHA-512 checksum

```sh
sha512sum <file>
```

#### Calculate MD5 checksum

```sh
md5 <file>
```

## References

-   [Wikipedia: Cryptographic hash function](https://en.wikipedia.org/wiki/Cryptographic_hash_function)
