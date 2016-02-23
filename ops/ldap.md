# Lightweight Directory Access Protocol *(LDAP)*

*From: [Zytrax](http://www.zytrax.com/books/ldap/ch2/index.html#history)*
> A protocol that defines the method by which directory data is accessed. Necessarily, it also defines and describes how data is represented in the directory service (the Data (Information) Model). Finally, it defines how data is loaded (imported) into and saved (exported) from a directory service (using LDIF). LDAP does not define how data is stored or manipulated. Data storage and access methods are automagical processes as far as the standard is concerned and are generally handled by back-end modules (typically using some form of transaction database) within any specific LDAP implementation.

* A directory service protocol.
* Runs on a layer above the TCP/IP stack.
* Provides a mechanism for CRUD operations on internet directories.
* Based on a client-server model.

---

**Table of Contents**

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Why?](#why)
- [Basics](#basics)
	- [Permissions](#permissions)
	- [Schema](#schema)
		- [Example](#example)
- [Setting up an LDAP Server](#setting-up-an-ldap-server)
- [LDAP Data Interchange Format *(LDIF)*](#ldap-data-interchange-format-ldif)
	- [Fields](#fields)
	- [Examples](#examples)
- [See Also](#see-also)
- [References](#references)

<!-- /TOC -->

---

## Why?

* System administrators have embraced LDAP because it offers them a way to centralize and make available all sorts of infrastructure information.
* Industry standard for directory access.


## Vocabulary

Term                 | Definition
---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
base `dn`            | the point from where a server will search for users. e.g. An LDAP search for the user admin will be done by the server starting at the base `dn` ( `dc=example,dc=com` )
`dn` | Distinguished Name, an entry's fully qualified name, unambiguously refers to an entry in the tree. It's the concatenation of its `rdn` and its immediate superior's `dn`. e.g. `UID=nobody@example.com,DC=example,DC=com`, `CN=John Smith,OU=Sales,O=ACME Limited,L=Moab,ST=Utah,C=US`
filter               | allows certain entries in the subtree and excludes others.
One level            | indicates a search of objects immediately subordinate to the base object, but does not include the base object itself.
search base          | (the distinguished name of the search base object) defines the location in the directory from which the LDAP search begins.
search scope         | defines how deep to search within the search base.
selection            | indicates what attributes to return from objects that match the filter criteria.
Subtree              | indicates a search of the base object and the entire subtree of which the base object distinguished name is the topmost object.
`rdn` | Relative Distinguished Name.
DIT | Directory Information Tree. The hierarchy of objects that make up the local directory structure. More than one DIT may be supported by an LDAP server.
bind | When connection is made to an LDAP server the first operation of the sequence is called a bind. The bind operation sends the `dn` of the entry that will be used for authentication and the password (usually contained in the userPassword attribute) to be used. In the case of an anonymous bind both values will be `NULL`. A Bind operation does not allow searching and therefore the DN used for authentication must be the same as the DN which initially created the entry.


## Basics



### Binding

Connecting with authentication is the usual first step in any LDAP client/server transaction. In LDAP-speak this is known as “binding to the server.”

*From: [SuperUser](http://superuser.com/questions/592650/what-does-binding-to-a-ldap-server-mean)*
> An LDAP client transmits a `BIND` request to a server in order to change the authorization state of the client connection. When a client first connects to an LDAP directory server, the server sets the authorization state of the connection to unauthenticated. When the server receives a `BIND` request, the server sets the authorization state of the connection to unauthenticated immediately. Should the `BIND` request be successful, the server **sets the authorization state of the connection to the state associated with the distinguished-name in the `BIND` request**. LDAPv3 allows a connection to change states any number of times, with the caveat that no requests be outstanding when the `BIND` request is received.

### Permissions

Set by the administrator to allow only certain people to access the LDAP database, and optionally keep certain data private.

### `ObjectClasses`

An identified family of objects that share certain characteristics.

Used in the Directory for a number of purposes:

* describing and categorizing objects and the entries that correspond to these objects.
* where appropriate, controlling the operation of the Directory.
* regulating the position of entries in the DIT.
* regulating the attributes that are contained in entries.
* identifying classes of entry that are to be associated with a particular policy by the appropriate administrative authority.

*From: [ietf.org](http://web.archive.org/web/20130812025333/http://tools.ietf.org/html/rfc4512#section-2.4)*
> An object class (a subclass) may be derived from an object class (its direct superclass) which is itself derived from an even more generic object class.  For structural object classes, this process stops at the most generic object class, 'top' (defined in [Section 2.4.1](http://web.archive.org/web/20130812025333/http://tools.ietf.org/html/rfc4512#section-2.4.1)).  An ordered set of superclasses up to the most superior object class of an object class is its superclass chain.



### Attributes

### Schema

A way to describe the format and attributes of data in the server. For example: a schema entered in an LDAP server might define a `groovyPerson` entry type, which has attributes of `instantMessageAddress`, and `coffeeRoastPreference`. The normal attributes of `name`, `email` `address`, etc., would be inherited from one of the standard schemas, which are rooted in X.500.


*From: [Efytimes][efytimes_openldap_series]*
> Each schema file can be understood to be analogous to a spreadsheet file. Each schema file defines certain `ObjectClasses` and attributes.

> Continuing with our analogy, `ObjectClasses` can be considered to be similar to each sheet within a spreadsheet file. Attributes are then analogous to each column within a sheet. In other words, multiple attributes are grouped together in an `ObjectClass`. Multiple `ObjectClasses` can be grouped to form a record.

#### Comparison to spreadsheets

LDAP            | Spreadsheet
----------------|-----------------
schema file     | spreadsheet file
`ObjectClasses` | each sheet
attributes      | columns

#### Example

*source: [O'Reilly: LDAP Tutorial][oreilly-tutorial]*

```sh
residentialPerson
   ( 2.5.6.10 NAME 'residentialPerson' SUP person STRUCTURAL MUST l
     MAY ( businessCategory $ x121Address $ registeredAddress $
     destinationIndicator $ preferredDeliveryMethod $ telexNumber $
     teletexTerminalIdentifier $ telephoneNumber $
     internationaliSDNNumber $
     facsimileTelephoneNumber $ preferredDeliveryMethod $ street $
     postOfficeBox $ postalCode $ postalAddress $
     physicalDeliveryOfficeName $ st $ l ) )
```

This definition says that an entry of object class `residentialPerson` must have a `l` attribute (short for locality) and may have a whole other set of attributes (`registeredAddress`, `postOfficeBox`, etc.). The key part of the specification is the `SUP` person string. It says that the superior class (the one from which `residentialPerson` inherits its attributes) is the `person` object class. That class’s definition looks like this:

```sh
person
   ( 2.5.6.6 NAME 'person' SUP top STRUCTURAL MUST ( sn $ cn )
     MAY ( userPassword $ telephoneNumber $ seeAlso $ description ) )
```

So, an entry with object class of `residentialPerson` must have `sn` (surname), `cn` (common name), and `l` (locality) attributes and may have the other attributes listed in the `MAY` sections of these two RFC excerpts. We also know that person is the top of the object hierarchy for `residentialPerson`, since its superior class is the special abstract class top.

In most cases, you can get away with using the predefined standard object classes. If you need to construct entries with attributes not found in an existing object class, it is usually good form to locate the closest existing object class and build upon it, like `residentialPerson` builds upon person.






## Setting up an LDAP Server


## LDAP Data Interchange Format *(LDIF)*

A standard plain text data interchange format for representing LDAP directory CRUD requests.

1. Conveys directory content as a set of records, one record for each object (or entry).
1. Represents update requests, such as Add, Modify, Delete, and Rename, as a set of records, one record for each update request.


### Fields

- `dn`: **Distinguished Name**
    - This refers to the name that uniquely identifies an entry in the directory.
    - DNs have a “most specific component first” ordering, like postal addresses.
- `dc`: **Domain Component**
    - This refers to each component of the domain. For example `www.google.com` would be written as `DC=www,DC=google,DC=com`
- `ou`: **Organizational Unit**
    - This refers to the organizational unit (or sometimes the user group) that the user is part of. If the user is part of more than one group, you may specify as such, e.g., `OU= Lawyer,OU= Judge`.
- `cn`: **Common Name**
    - This refers to the individual object (person's name; meeting room; recipe name; job title; etc.) for whom/which you are querying.


### Examples

Directory entry with several attributes, represented as a record.

```sh
dn: cn=The Postmaster,dc=example,dc=com
objectClass: organizationalRole
cn: The Postmaster
```

Modify multiple single-valued attributes for two different directory entries.

```sh
dn: CN=John Smith,OU=Legal,DC=example,DC=com
changetype: modify
replace:employeeID
employeeID: 1234
-
replace:employeeNumber
employeeNumber: 98722
-
replace: extensionAttribute6
extensionAttribute6: JSmith98
-

dn: CN=Jane Smith,OU=Accounting,DC=example,DC=com
changetype: modify
replace:employeeID
employeeID: 5678
-
replace:employeeNumber
employeeNumber: 76543
-
replace: extensionAttribute6
extensionAttribute6: JSmith14
-
```

Note:
- the `-` character between each attribute change is required.
- each directory entry ends with a `-` followed by a blank line.
- The final `-` is required.

Add a telephone number to an existing user.

```sh
dn: cn=Peter Michaels, ou=Artists, l=San Francisco, c=US
changetype: modify
add: telephonenumber
telephonenumber: +1 415 555 0002
```

## See Also

* [self: directory](../persistence/README.md#Directory-vs-Database)


## References

* [CentOS: LDIF Update Statements](https://www.centos.org/docs/5/html/CDS/ag/8.0/Creating_Directory_Entries-LDIF_Update_Statements.html)
* [LDAP Authentication Best Practices](http://web.archive.org/web/20130801091446/http://www.ldapguru.info/ldap/authentication-best-practices.html)
* [Microsoft](https://msdn.microsoft.com/en-us/library/windows/desktop/aa367008)
* [O'Reilly: LDAP Tutorial][oreilly-tutorial]
* [OpenLDAP Series][efytimes_openldap_series]
* [OpenLDAP Setup Overview](https://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-ldap-quickstart.html)
* [TLDP: LDAP, How To](http://www.tldp.org/HOWTO/LDAP-HOWTO/index.html)
* [Wikipedia: LDAP](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)
* [Wikipedia: LDIF](https://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format)
* [Zytrax: LDAP for Rocket Scientists](http://www.zytrax.com/books/ldap/)
* [Zytrax: LDAP Glossary](http://www.zytrax.com/books/ldap/apd/index.html)

[oreilly-tutorial]: http://archive.oreilly.com/pub/a/perl/excerpts/system-admin-with-perl/ten-minute-ldap-utorial.html
[efytimes_openldap_series]: http://opensourceforu.efytimes.com/tag/openldap-series/
[ietf_ldap_protocol]: http://web.archive.org/web/20130812025333/http://tools.ietf.org/html/rfc4512
