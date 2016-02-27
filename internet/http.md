# Hypertext Transfer Protocol (HTTP)

---

## Basics

### Notable Status Codes

|       |                     |
|-------|---------------------|
| `1--` | Informational       |
| `2--` | Success             |
| `200` | OK                  |
| `3--` | Redirection         |
| `301` | Moved Permanently   |
| `4--` | Client Error        |
| `400` | Bad Request         |
| `401` | Unauthorized        |
| `403` | Forbidden           |
| `404` | Not Found           |
| `5--` | Server Error        |
| `503` | Service Unavailable |
| `504` | Gateway Timeout     |

## Request methods *(verbs)*

Indicates the desired action to be performed on the identified resource.

|           |                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:---------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   `GET`   | The GET method requests a representation of the specified resource. Requests using GET should only retrieve data and should have no other effect.                            |
|  `HEAD`   | The `HEAD` method asks for a response identical to that of a `GET` request, but without the response body. ...useful for retrieving meta-information written in response headers, without having to transport the entire content.                                                                                                                                                                                                   |
|  `POST`   | The `POST` method requests that the server accept the entity enclosed in the request as a new subordinate of the web resource identified by the URI. The data POSTed might be, for example, an annotation for existing resources; a message for a bulletin board, newsgroup, mailing list, or comment thread; a block of data that is the result of submitting a web form to a data-handling process; or an item to add to a database. |
|   `PUT`   | The `PUT` method requests that the enclosed entity be stored under the supplied URI. If the URI refers to an already existing resource, it is modified; if the URI does not point to an existing resource, then the server can create the resource with that URI.                                                                                                                                                                      |
| `DELETE`  | The `DELETE` method deletes the specified resource.                                                                                                                                                                                                                                                                                                                                                                                    |
|  `TRACE`  | The `TRACE` method echoes the received request so that a client can see what (if any) changes or additions have been made by intermediate servers.                                                                                                                                                                                                                                                                                     |
| `OPTIONS` | The `OPTIONS` method returns the HTTP methods that the server supports for the specified URL. This can be used to check the functionality of a web server by requesting `*` instead of a specific resource.                                                                                                                                                                                                                            |
| `CONNECT` | The `CONNECT` method converts the request connection to a transparent TCP/IP tunnel, usually to facilitate SSL-encrypted communication (HTTPS) through an unencrypted HTTP proxy. See [`HTTP CONNECT` tunneling](https://en.wikipedia.org/wiki/HTTP_tunnel#HTTP_CONNECT_tunneling).                                                                                                                                                                                                                          |
|  `PATCH`  | The `PATCH` method applies partial modifications to a resource.                                                                                                                                                                                                                                                                                                                                                                        |

### Request Message

Consists of:

-   A request line (e.g., `GET /images/logo.png HTTP/1.1`, which requests a resource called `/images/logo.png` from the server).
-   Request header fields (e.g., `Accept-Language: en`).
-   An empty line.
-   An optional message body.

#### Example Client Request

```http
GET /index.html HTTP/1.1
Host: www.example.com
```

### Response Message

Consists of:

-   A status line which includes the status code and reason message (e.g., `HTTP/1.1 200 OK`, which indicates that the client's request succeeded).
-   Response header fields (e.g., `Content-Type: text/html`).
-   An empty line.
-   An optional message body.

#### Example Server Response

```http
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Server: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)
Last-Modified: Wed, 08 Jan 2003 23:11:55 GMT
ETag: "3f80f-1b6-3e1cb03b"
Content-Type: text/html; charset=UTF-8
Content-Length: 138
Accept-Ranges: bytes
Connection: close

<html>
<head>
  <title>An Example Page</title>
</head>
<body>
  Hello World, this is a very simple HTML document.
</body>
</html>
```

---

## Sequence Diagram

---

## HTTP/2 Protocol

---

## References

-   [Allen, "What Every Web Developer Should Know About HTTP "](http://www.amazon.com/Developer-Should-OdeToCode-Programming-Series-ebook/dp/B0076Z6VMI)
-   [http2 explained](https://bagder.gitbooks.io/http2-explained/content)
-   [Wikipedia: HTTP Status Codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)
