# Namespacing in PHP

*From: [PHP.net](http://php.net/manual/en/language.namespaces.rationale.php)*

> In the broadest definition namespaces are a way of encapsulating items. This can be seen as an abstract concept in many places. For example, in any operating system directories serve to group related files, and act as a namespace for the files within them. As a concrete example, the file `foo.txt` can exist in both directory `/home/greg` and in `/home/other`, but two copies of `foo.txt` cannot co-exist in the same directory. In addition, to access the `foo.txt` file outside of the `/home/greg` directory, we must prepend the directory name to the file name using the directory separator to get `/home/greg/foo.txt`. This same principle extends to namespaces in the programming world.

---

## Defining

*From: [PHP.net](http://php.net/manual/en/language.namespaces.definition.php)*

> Namespaces are declared using the `namespace` keyword. A file containing a namespace must declare the `namespace` at the top of the file before any other code - with one exception: the `declare` keyword.

```php
namespace MyProject;

const CONNECT_OK = 1;
class Connection { /* ... */ }
function connect() { /* ... */ }
```

---

## References

-   <http://www.phptherightway.com/#namespaces>
