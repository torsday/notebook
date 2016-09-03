# Java

*From: Wikipedia <https://en.wikipedia.org/wiki/Java_(programming_language)>*

> Java is a general-purpose computer programming language that is **concurrent, class-based, object-oriented, and specifically designed to have as few implementation dependencies as possible**. It is intended to let application developers "write once, run anywhere" (WORA), meaning that compiled Java code can run on all platforms that support Java without the need for recompilation. Java applications are typically compiled to bytecode that can run on any Java virtual machine (JVM) regardless of computer architecture. As of 2016, Java is one of the most popular programming languages in use, particularly for client-server web applications, with a reported 9 million developers. Java was originally developed by James Gosling at Sun Microsystems (which has since been acquired by Oracle Corporation) and released in 1995 as a core component of Sun Microsystems' Java platform. The language derives much of its syntax from C and C++, but it has fewer low-level facilities than either of them.

> The original and reference implementation Java compilers, virtual machines, and class libraries were originally released by Sun under proprietary licences. As of May 2007, in compliance with the specifications of the Java Community Process, Sun relicensed most of its Java technologies under the GNU General Public License. Others have also developed alternative implementations of these Sun technologies, such as the GNU Compiler for Java (bytecode compiler), GNU Classpath (standard libraries), and IcedTea-Web (browser plugin for applets).

> The latest version is Java 8, which is the only version currently supported for free by Oracle, although earlier versions are supported both by Oracle and other companies on a commercial basis.



---

## SE, EE, ME...

### Java SE (Standard Edition)

The foundation on which Java EE is built.

This is the **core Java programming platform**.  It contains all of the libraries and APIs that any Java programmer should learn (java.lang, java.io, java.math, java.net, java.util, etc...).

### Java EE (Enterprise Edition)

It **adds libraries to Java SE** which provide functionality to deploy fault-tolerant, distributed, multi-tier Java software, based largely on modular components running on an application server.

If your application demands a very large scale, distributed system, then you should consider using Java EE.  Built on top of Java SE, it provides libraries for database access (JDBC, JPA), remote method invocation (RMI), messaging ([JMS](http://en.wikipedia.org/wiki/Java_Message_Service)), web services, XML processing, and defines standard APIs for Enterprise JavaBeans, servlets, portlets, Java Server Pages, etc...

### Java ME

Java Micro Edition.  This is the platform for developing applications for mobile devices and embedded systems such as set-top boxes.  Java ME **provides a subset of the functionality of Java SE**, but **also introduces libraries specific to mobile devices**.  Because Java ME is based on an earlier version of Java SE, some of the new language features introduced in Java 1.5 (e.g. generics) are not available.

---

## See Also

* 
* <https://en.wikipedia.org/wiki/Classpath_(Java)>
