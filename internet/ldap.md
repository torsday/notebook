# Lightweight Directory Access Protocol *(LDAP)*

*From: [Zytrax](http://www.zytrax.com/books/ldap/ch2/index.html#history)*
> A protocol that defines the method by which directory data is accessed. Necessarily, it also defines and describes how data is represented in the directory service (the Data (Information) Model). Finally, it defines how data is loaded (imported) into and saved (exported) from a directory service (using LDIF). LDAP does not define how data is stored or manipulated. Data storage and access methods are automagical processes as far as the standard is concerned and are generally handled by back-end modules (typically using some form of transaction database) within any specific LDAP implementation.

* A directory service protocol and binary protocol.
* Runs on a layer above the TCP/IP stack. *(port 389 for non-ssl, 636 for SSL via an SSL-Tunnel)*
* Provides a mechanism for CRUD operations on internet directories.
* Based on a client-server model.

---

**Table of Contents**

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Why?](#why)
- [Vocabulary](#vocabulary)
	- [Fields](#fields)
	- [General](#general)
- [Overview](#overview)
	- [Timeline](#timeline)
		- [The client may request the following operations:](#the-client-may-request-the-following-operations)
	- [Directory Structure](#directory-structure)
		- [Example of an entry when represented using LDIF](#example-of-an-entry-when-represented-using-ldif)
- [Operations](#operations)
	- [Add](#add)
	- [Bind (authenticate)](#bind-authenticate)
	- [Delete](#delete)
	- [Search and Compare](#search-and-compare)
	- [Modify](#modify)
		- [Adding](#adding)
		- [Modifying](#modifying)
	- [Modify DN](#modify-dn)
	- [Extended operations](#extended-operations)
	- [StartTLS](#starttls)
	- [Abandon](#abandon)
- [Basics](#basics)
	- [Binding](#binding)
	- [Schema](#schema)
		- [Comparison to spreadsheets](#comparison-to-spreadsheets)
		- [Example](#example)
- [Setting up an LDAP Server](#setting-up-an-ldap-server)
- [LDAP Data Interchange Format *(LDIF)*](#ldap-data-interchange-format-ldif)
	- [Examples](#examples)
- [See Also](#see-also)
- [References](#references)

<!-- /TOC -->

---

## Why?

* Centralize and make available all sorts of infrastructure information.
* Industry standard for directory access.


## Vocabulary

### Fields

Term | Definition
-----|------------------------
`cn` | *see Common Name.*
`dc` | *see Domain Component.*
`dn` | *see Distinguished Name.*
`l`  | *see locality.*
`ou` | *see Organization Unit.*
`sn` | *see surname.*

### General

Term                              | Definition
----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Attribute                         | The data in an entry is contained in attribute-value pairs. Each attribute has a name and belongs to (in contained in) one or more `objectClass`(es). Attributes may be categorised as either user (`userApplication`) or operational (`dSAOperation`).
Base                              | The base/root/suffix entry describes the topmost entry in a DIT or naming-context.
bind                              | The first operation when connecting to an LDAP server; then authentication step.
Common Name                       | `cn` (`commonName`). One of the most commonly used attributes, widely used as the attribute to name some "thing" or real-world entity.
Directory Information Tree (DIT)  | The hierarchy of objects that make up the local directory structure. More than one DIT may be supported by an LDAP server.
Distinguished Name (DN)           | An entry's fully qualified name, unambiguously refers to an entry in the tree. It's the concatenation of its `rdn` and its immediate superior's `dn`. e.g. `UID=nobody@example.com,DC=example,DC=com`, `CN=John Smith,OU=Sales,O=ACME Limited,L=Moab,ST=Utah,C=US`
Domain Component                  | This refers to each component of the domain. For example `www.google.com` would be written as `DC=www,DC=google,DC=com`
Directory System Agent (DSA)      | Any DAP or LDAP enabled directory service e.g. an LDAP server.
DSA Specific Entry (DSE)          | A control entry in a local directory server.
LDIF                              | LDAP Data Interchange Format. A plain text data interchange format for representing LDAP directory CRUD requests. *(see more below)*
Object Classes                    | Collections of attributes. Each `objectClass` is uniquely identified by an OID
Object IDentifier (OID)           | A dot-separated valued e.g. `2.5.6.2` that uniquely defines an object and who is responsible for its definition
Organization Unit                 | a.k.a. user group. The group(s)/unit(s) that a user is part of e.g., `OU= Lawyer,OU= Judge`.
Relative Distinguished Name (RDN) | Attributes *unique at their level in the hierarchy*. RDNs may be multi-valued, combining two or more attributes using `+` e.g. cn+uid.
search base                       | (the DN of the search base object) defines the location in the directory from which the LDAP search begins.
search scope                      | defines how deep to search within the search base.
selection                         | indicates what attributes to return from objects that match the filter criteria.
Subtree                           | indicates a search of the base object and the entire subtree of which the base object distinguished name is the topmost object.

## Overview

### Timeline

1. A client starts an LDAP session by connecting to an LDAP server, called a Directory System Agent (DSA).
1. The client then sends an operation request to the server, and the server sends responses in return.
	* With some exceptions, the client does not need to wait for a response before sending the next request, and the server may send the responses in any order.

#### The client may request the following operations:

* StartTLS — use the LDAPv3 Transport Layer Security (TLS) extension for a secure connection
* Bind — authenticate and specify LDAP protocol version
* Search — search for and/or retrieve directory entries
* Compare — test if a named entry contains a given attribute value
* Add a new entry
* Delete an entry
* Modify an entry
* Modify Distinguished Name (DN) — move or rename an entry
* Abandon — abort a previous request
* Extended Operation — generic operation used to define other operations
* Unbind — close the connection (not the inverse of Bind)

### Directory Structure

The protocol provides an interface with directories that follow the 1993 edition of the X.500 model:

* An entry consists of a set of attributes.
* An attribute has a name (an attribute type or attribute description) and one or more values. The attributes are defined in a schema (see below).
* Each entry has a unique identifier: its Distinguished Name (DN). This consists of its Relative Distinguished Name (RDN), constructed from some attribute(s) in the entry, followed by the parent entry's DN. Think of the DN as the full file path and the RDN as its relative filename in its parent folder (e.g. if /foo/bar/myfile.txt were the DN, then myfile.txt would be the RDN).

A DN may change over the lifetime of the entry, for instance, when entries are moved within a tree. To reliably and unambiguously identify entries, a UUID might be provided in the set of the entry's operational attributes.

#### Example of an entry when represented using LDIF

```sh
dn: cn=John Doe,dc=example,dc=com
cn: John Doe
givenName: John
sn: Doe
telephoneNumber: +1 888 555 6789
telephoneNumber: +1 888 555 1232
mail: john@example.com
manager: cn=Barbara Doe,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: organizationalPerson
objectClass: person
objectClass: top
```

* `dn` is the distinguished name of the entry; it is neither an attribute nor a part of the entry.
* `cn=John Doe` is the entry's RDN (Relative Distinguished Name)
* `dc=example,dc=com` is the DN of the parent entry, where `dc` denotes 'Domain Component'.

* The other lines show the attributes in the entry. Attribute names are typically mnemonic strings, like
	* `cn` for common name
	* `dc` for domain component
	* `mail` for e-mail address
	* `sn` for surname

A server holds a subtree starting from a specific entry, e.g. `dc=example,dc=com` and its children. Servers may also hold references to other servers, so an attempt to access `ou=department,dc=example,dc=com` could return a referral or continuation reference to a server that holds that part of the directory tree. The client can then contact the other server. Some servers also support chaining, which means the server contacts the other server and returns the results to the client.

LDAP rarely defines any ordering: The server may return the values of an attribute, the attributes in an entry, and the entries found by a search operation in any order. This follows from the formal definitions - an entry is defined as a set of attributes, and an attribute is a set of values, and sets need not be ordered.



## Operations

### Add

```sh
dn: uid=user,ou=people,dc=example,dc=com
changetype: add
objectClass: top
objectClass: person
uid: user
sn: last-name
cn: common-name
userPassword: password
```


### Bind (authenticate)


### Delete


### Search and Compare


### Modify

#### Adding

```sh
dn: dc=example,dc=com
changetype: modify
add: cn
cn: the-new-cn-value-to-be-added
-
```

#### Modifying

```sh
dn: uid=user.0,ou=people,dc=example,dc=com
changetype: modify
increment: employeeNumber
employeeNumber: 5
-
```

### Modify DN


### Extended operations


### StartTLS


### Abandon







## Basics

### Binding

Connecting with authentication is the usual first step in any LDAP client/server transaction. In LDAP-speak this is known as “binding to the server.”

*From: [SuperUser](http://superuser.com/questions/592650/what-does-binding-to-a-ldap-server-mean)*
> An LDAP client transmits a `BIND` request to a server in order to change the authorization state of the client connection. When a client first connects to an LDAP directory server, the server sets the authorization state of the connection to unauthenticated. When the server receives a `BIND` request, the server sets the authorization state of the connection to unauthenticated immediately. Should the `BIND` request be successful, the server **sets the authorization state of the connection to the state associated with the distinguished-name in the `BIND` request**. LDAPv3 allows a connection to change states any number of times, with the caveat that no requests be outstanding when the `BIND` request is received.

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



## Examples

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

### Ruby

[Ruby Docs: net/ldap][ruby_docs_net_ldap]

#### User Auth
```ruby
require 'rubygems'
require 'net/ldap'

ldap = Net::LDAP.new
ldap.host = your_server_ip_address
ldap.port = 389
ldap.auth "joe_user", "opensesame"
if ldap.bind
  # authentication succeeded
else
  # authentication failed
end
```

#### Search

```ruby
require 'rubygems'
require 'net/ldap'

ldap = Net::LDAP.new :host => server_ip_address,
     :port => 389,
     :auth => {
           :method => :simple,
           :username => "cn=manager,dc=example,dc=com",
           :password => "opensesame"
     }

filter = Net::LDAP::Filter.eq( "cn", "George*" )
treebase = "dc=example,dc=com"

ldap.search( :base => treebase, :filter => filter ) do |entry|
  puts "DN: #{entry.dn}"
  entry.each do |attribute, values|
    puts "   #{attribute}:"
    values.each do |value|
      puts "      --->#{value}"
    end
  end
end

p ldap.get_operation_result
```


### PHP

Baked-in PHP Functions ([php.net/manual/en/ref.ldap.php](http://php.net/manual/en/ref.ldap.php))

```php
<?php
// basic sequence with LDAP is connect, bind, search, interpret search
// result, close connection

echo "<h3>LDAP query test</h3>";
echo "Connecting ...";
$ds=ldap_connect("localhost");  // must be a valid LDAP server!
echo "connect result is " . $ds . "<br />";

if ($ds) {
    echo "Binding ...";
    $r=ldap_bind($ds);     // this is an "anonymous" bind, typically
                           // read-only access
    echo "Bind result is " . $r . "<br />";

    echo "Searching for (sn=S*) ...";
    // Search surname entry
    $sr=ldap_search($ds, "o=My Company, c=US", "sn=S*");
    echo "Search result is " . $sr . "<br />";

    echo "Number of entries returned is " . ldap_count_entries($ds, $sr) . "<br />";

    echo "Getting entries ...<p>";
    $info = ldap_get_entries($ds, $sr);
    echo "Data for " . $info["count"] . " items returned:<p>";

    for ($i=0; $i<$info["count"]; $i++) {
        echo "dn is: " . $info[$i]["dn"] . "<br />";
        echo "first cn entry is: " . $info[$i]["cn"][0] . "<br />";
        echo "first email entry is: " . $info[$i]["mail"][0] . "<br /><hr />";
    }

    echo "Closing connection";
    ldap_close($ds);

} else {
    echo "<h4>Unable to connect to LDAP server</h4>";
}
?>
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
* [PHP Docs: LDAP](http://php.net/manual/en/ref.ldap.php)
* [RubyDocs: Net: LDAP][ruby_docs_net_ldap]
* [SitePoint: Essentials of LDAP with PHP](http://www.sitepoint.com/essentials-ldap-php/)
* [TLDP: LDAP, How To](http://www.tldp.org/HOWTO/LDAP-HOWTO/index.html)
* [Wikipedia: LDAP](https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)
* [Wikipedia: LDIF](https://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format)
* [Zytrax: LDAP for Rocket Scientists](http://www.zytrax.com/books/ldap/)
* [Zytrax: LDAP Glossary](http://www.zytrax.com/books/ldap/apd/index.html)

[oreilly-tutorial]: http://archive.oreilly.com/pub/a/perl/excerpts/system-admin-with-perl/ten-minute-ldap-utorial.html
[efytimes_openldap_series]: http://opensourceforu.efytimes.com/tag/openldap-series/
[ietf_ldap_protocol]: http://web.archive.org/web/20130812025333/http://tools.ietf.org/html/rfc4512
[ruby_docs_net_ldap]: http://www.rubydoc.info/gems/ruby-net-ldap/Net/LDAP