# Search for the Right PHP LDAP Library

---

## The Process

1. Generate initial list

    - Well rated PHP LDAP libraries on GitHub

        * adLDAP
        * [adldap2]
        * ccottet/ldap
        * [ldaptools]

    - Well rated PHP LDAP Libraries on [Packagist](https://packagist.org/search/?q=ldap)

        * adldap
        * [adldap2]
        * [imag/ldap-bundle][ldap-bundle]
        * tiesa/ldap
        * [zend-ldap]

    - Others of interest
        * [symfony/ldap](https://github.com/symfony/ldap)

    - Removing duplicates leaves us:

        1. [adldap](https://github.com/adldap/adldap)
        1. [adldap2]
        1. [ccottet/ldap](https://github.com/ccottet/ldap)
        1. [imag/ldap-bundle][ldap-bundle]
        1. [ldaptools]
        1. [symfony/ldap](https://github.com/symfony/ldap)
        1. [zend-ldap]

1. Filter out dealbreakers

    1. [adldap](https://github.com/adldap/adldap)
        * > Version v5.0.0 is in heavy development, however it is close to completion. Use 'dev-master' at you're own risk.
        * ^ 8 months ago was the last commit
    1. [ccottet/ldap](https://github.com/ccottet/ldap)
        * Last commit was over 3 years ago.
        * Even then, it consists of only 3 commits total.
    1. [symfony/ldap](https://github.com/symfony/ldap)
        * > This component is currently marked as internal, as it still needs some work. **Breaking changes will be introduced in the next minor version** of Symfony.


1. The Shortlist:

    1. [adldap2]
    1. [ldap-bundle]
    1. [ldaptools]
    1. [zend-ldap]

---

## Comparison of the best

### [adldap2]

> Working with Active Directory doesn't need to be hard. Adldap2 is a tested PHP package that provides LDAP authentication and Active Directory management tools using the Active Record pattern.

#### Basic Characteristics

x            | y
-------------|------------
Last Commit  | 14 days ago
Contributors | 12 (1 primary)
Issues       | 5
Standing PRs | 0
Forks        | 23
Stars        | 74
YAML config  | ?


### [ldap-bundle]

> LdapBundle provides LDAP authentication without using Apache's mod_ldap. The bundle instead **relies on [PHP's LDAP extension](http://php.net/manual/en/book.ldap.php) along with a form to authenticate users**. LdapBundle can also be used for authorization by retrieving the user's roles defined in LDAP.

#### Basic Characteristics

x            | y
-------------|-------------
Last Commit  | > 1 year ago
Contributors | 27 (1 primary)
Issues       | 35
Standing PRs | 21
Forks        | 93
Stars        | 104
YAML config  | true



### [ldaptools]

> LdapTools is designed to be customizable for use with pretty much any directory service, but contains default attribute converters and schemas for Active Directory and OpenLDAP.

x            | y
-------------|-------------
Last Commit  | 20 hours ago
Contributors | 1
Issues       | 0
Standing PRs | 0
Forks        | 1
Stars        | 54
YAML config  | true
docs         | excellent




### [zend-ldap]

> `Zend\Ldap\Ldap` is a class for performing LDAP operations including but not limited to binding, searching and modifying entries in an LDAP directory.

#### Basic Characteristics

x            | y
-------------|------------
Last Commit  | 13 days ago
Contributors | 100
Issues       | 13
Standing PRs | 8
Forks        | 12
Stars        | 8
YAML config  | ?


---

## Most Exciting


### [ldaptools]

#### Pros

* Excellent documentation
* Actively developed
* Explicit support for OpenLDAP

#### Cons

* YAML




[adldap2]: https://github.com/adldap2/adldap2
[ldap-bundle]: https://github.com/BorisMorel/LdapBundle
[ldaptools]: https://github.com/ldaptools/ldaptools
[zend-ldap]: https://github.com/zendframework/zend-ldap
