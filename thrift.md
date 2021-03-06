# Apache Thrift

*From: [Apache.org](https://thrift.apache.org)*

> The Apache Thrift software framework, for scalable cross-language services development, combines a software stack with a code generation engine to build services that work efficiently and seamlessly between C++, Java, Python, PHP, Ruby, Erlang, Perl, Haskell, C#, Cocoa, JavaScript, Node.js, Smalltalk, OCaml and Delphi and other languages.


Olmsted's Notes
=============

Thrift is a cross-language remote procedure call (RPC) framework. To meet this goal, it provides:
  1. A binary communication protocol
  2. An Interactive Data Language (IDL) to model services and resources available for RPC.
The Thrift IDLs can be used to auto-generate code for interacting with these services and resources.


## 1. Thrift Protocol


At a high level We can model Thrift's architecture like this:

```md
      CLIENT                                SERVER
------------------                    ------------------
| Your Code      |                    | Your Code      |
------------------                    ------------------
| Generated Code |                    | Generated Code |
------------------                    ------------------
| TProtocol      |                    | TProtocol      |
------------------                    ------------------
| TTransport     |                    | TTransport     |
------------------                    ------------------
        |                                     |
        |                                     |
        |____________[Input/Output)___________|
```

At the highest level of the stack, your code makes use of IDL-generated service code, which provides
language-specific clients and servers for handling RPC requests. From there we move down the stack to
the protocol layer.

`TProtocol` defines how the data is encoded and parsed. To list just a few options,
  * TBinaryProtocol  – a simple binary format.
  * TCompactProtocol – a more compact binary format.
  * TDebugProtocol   – a human-readable text for debugging purposes.
  * TJSONProtocol    – neat you can even use JSON!

Moving further down the stack we reach the transport layer. `TTransport` options include:
  * TFileTransport   – this transport just writes to a file.
  * TFramedTransport – required transport for a non-blocking server.
  * TMemoryTransport – uses memory for transport.
  * TSocket          – uses a blocking socket for transport.

## 2. Thrift IDL

When most people think of Thrift, they think of the Thrift IDL. The Thrift IDL allows you to define services
and resources that are exposed over RPC. IDL files can then be used to auto-generate code for these services
and resources in a wide range of languages.

### Base Types

* `bool`
* `byte`
* `i16`    – 16-bit signed integer
* `i32`    – 32-bit signed integer
* `i64`    – 64-bit signed integer
* `double` – 64-bit floating point number
* `string` – encoding agnostic string

### Collections

* `list<A>`  – an ordered list of elements of type A
* `set<A>    – an unordered set of elements of type A
* `map<A, B> – a map of unique keys of type A mapped to values of type B.

### Structs

Very similar to a C `struct`. Allows you to structure data within a defined type. Note that while
structs are similar to classes, they cannot be subtyped/extended.

```java
struct Email {
    1: required list<string> sentTo;
    2: required string sentFrom;
    3: optional string subject;
    4: optional string message;
    5: optional string encoding = "UTF-8";
}
```


### Enums

Enums allow you to define a type that may only have certain set values. These are just mapped to
integers (starting with 1), but you can also explicity assign an integer or hex value.

```java
enum Encoding {
   UTF-8,
   UTF-16,
   NONE = 0 // explicit value assignment
}
struct Email {
    1: required list<string> sentTo;
    2: required string sentFrom;
    3: optional string subject;
    4: optional string message;
    5: optional string encoding = Encoding.UTF-8; // Neat check it out
}
```

### Services

One of the strengths of Thrift is that it allows you to auto-generate RPC-based services. You
can think of a Service as an interface – the interface will be auto-generated, but it's up to
you to write a working implementation in your own code.

```java
service EmailService {
  void send(1:Email email);
  void reply(1:Email original, 2:Email reply);
  list<Email> get(1:string addressee);
}
```

### Constants

```java
const i32 MAGIC_NUMBER = 7;
// Complex types can be specified using JSON notation.
const list<string> EMAILS = ["foo@example.com", "bar@example.com"];
```

### Typedefs

Typedefs allow you to create simple type aliases.

```java
typedef string EmailAddress
```

### Namespaces

Thrift IDL files can be namespaced for easier organization. You can customize the namespacing on
a per-language basis.

```java
namespace scala com.example.email
namespace php example.email
```

### Includes

You can split your IDLs into multiple files. To include another Thrift file, you just need to supply a filepath.

```java
include "images.thrift"
struct ImageAttachments {
    1: list<image.Jpeg> files; // included types are prefixed with the file name.
}
```

## What Thrift is not

Since Thrift gives allows us to auto-generate a bunch of code for free, it's tempting to build new
RPC services with Thrift IDLs as a starting point. Some people even build services that rely almost
entirely on Thrift generated code.
This is a mistake. Thrift is an RPC framework, not a full-fledged microservice framework. Strictly speaking
Thrift only defines one thin layer of a service, the API/RPC layer. It's not a substitute for a properly
defined domain. Over-relying on auto-generated code tightly couples you with the Thrift framework and
makes it difficult to define your own domain-specific behaviors.
When creating a new service, start with the domain and work outward. Define your models and services in isolation
of the implementation details of your RPC system. Once the domain is fleshed out, only then should you start
writing Thrift IDLs and mapping the generated resources and services to your domain code.

## Resources

* [Thrift the Missing Guide](ihttps://diwakergupta.github.io/thrift-missing-guide/)
* [Apache Thrift](https://thrift.apache.org/)
* [Wikipedia on Thrift](https://en.wikipedia.org/wiki/Apache_Thrift)
