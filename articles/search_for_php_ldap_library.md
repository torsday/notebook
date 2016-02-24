# Search for the Right PHP LDAP Library

---

## The Process

1. Generate initial list

    - Well rated PHP LDAP libraries on GitHub

        * adldap/adLDAP
        * Adldap2/Adldap2
        * ccottet/ldap
        * ldaptools/ldaptools

    - Well rated PHP LDAP Libraries on [Packagist](https://packagist.org/search/?q=ldap)

        * adldap/adldap
        * adldap2/adldap2
        * imag/ldap-bundle
        * tiesa/ldap
        * zendframework/zend-ldap

    - Others of interest
        * [symfony/ldap](https://github.com/symfony/ldap)

    - Removing duplicates leaves us:

        1. [github.com/adldap/adldap](https://github.com/adldap/adldap)
        1. [github.com/adldap2/adldap2](https://github.com/adldap2/adldap2)
        1. [github.com/ccottet/ldap](https://github.com/ccottet/ldap)
        1. [github.com/imag/ldap-bundle](https://github.com/BorisMorel/LdapBundle)
        1. [github.com/ldaptools/ldaptools](https://github.com/ldaptools/ldaptools)
        1. [github.com/zendframework/zend-ldap](https://github.com/zendframework/zend-ldap)

1. Filter out dealbreakers

    1. [github.com/adldap/adldap](https://github.com/adldap/adldap)
        * > Version v5.0.0 is in heavy development, however it is close to completion. Use 'dev-master' at you're own risk.
        * ^ 8 months ago was the last commit
    1. [github.com/ccottet/ldap](https://github.com/ccottet/ldap)
        * Last commit was over 3 years ago.
        * Even then, it consists of only 3 commits total.
    1. [github.com/symfony/ldap](https://github.com/symfony/ldap)
        * > This component is currently marked as internal, as it still needs some work. **Breaking changes will be introduced in the next minor version** of Symfony.
    1. [github.com/ldaptools/ldaptools](https://github.com/ldaptools/ldaptools)
        * Only 1 contributor.



1. The Shortlist:

    1. [github.com/adldap2/adldap2](https://github.com/adldap2/adldap2)
    1. [github.com/imag/ldap-bundle](https://github.com/BorisMorel/LdapBundle)
    1. [github.com/zendframework/zend-ldap](https://github.com/zendframework/zend-ldap)

---

## Comparison of the best

### [adldap2/adldap2](https://github.com/adldap2/adldap2)


### [imag/ldap-bundle](https://github.com/BorisMorel/LdapBundle)


### [zendframework/zend-ldap](https://github.com/zendframework/zend-ldap)











---

### ldaptools/ldaptools

[github.com/ldaptools/ldaptools](https://github.com/ldaptools/ldaptools)

Pros:

* no issues
* recent commits
* nice docs: http://www.phpldaptools.com/

Cons:

* YAML
