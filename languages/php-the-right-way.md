# [PHP the Right Way](https://github.com/codeguy/php-the-right-way)

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Getting Started](#getting-started)
	- [Use the Current Stable Version (7.0)](#use-the-current-stable-version-70)
	- [Built-in web server](#built-in-web-server)
	- [Mac Setup](#mac-setup)
		- [Install PHP via Homebrew](#install-php-via-homebrew)
		- [Install PHP via Macports](#install-php-via-macports)
		- [Install PHP via phpbrew](#install-php-via-phpbrew)
		- [Install PHP via Liip's binary installer](#install-php-via-liips-binary-installer)
		- [Compile from Source](#compile-from-source)
		- [All-in-One Installers](#all-in-one-installers)
	- [Windows Setup](#windows-setup)
- [Code Style Guide](#code-style-guide)
- [Language Highlights](#language-highlights)
	- [Programming Paradigms](#programming-paradigms)
		- [Object-oriented Programming](#object-oriented-programming)
		- [Functional Programming](#functional-programming)
		- [Meta Programming](#meta-programming)
	- [Namespaces](#namespaces)
	- [Standard PHP Library](#standard-php-library)
	- [Command Line Interface](#command-line-interface)
	- [Xdebug](#xdebug)
- [Dependency Management](#dependency-management)
	- [Composer and Packagist](#composer-and-packagist)
		- [How to Install Composer](#how-to-install-composer)
			- [Installing on Windows](#installing-on-windows)
		- [How to Install Composer (manually)](#how-to-install-composer-manually)
		- [How to Define and Install Dependencies](#how-to-define-and-install-dependencies)
		- [Updating your dependencies](#updating-your-dependencies)
		- [Update Notifications](#update-notifications)
		- [Checking your dependencies for security issues](#checking-your-dependencies-for-security-issues)
		- [Handling global dependencies with Composer](#handling-global-dependencies-with-composer)
	- [PEAR](#pear)
		- [How to install PEAR](#how-to-install-pear)
		- [How to install a package](#how-to-install-a-package)
		- [Handling PEAR dependencies with Composer](#handling-pear-dependencies-with-composer)
- [Coding Practices](#coding-practices)
	- [The Basics](#the-basics)
	- [Date and Time](#date-and-time)
	- [Design Patterns](#design-patterns)
	- [Working with UTF-8](#working-with-utf-8)
		- [There's no one-liner. Be careful, detailed, and consistent.](#theres-no-one-liner-be-careful-detailed-and-consistent)
		- [UTF-8 at the PHP level](#utf-8-at-the-php-level)
		- [UTF-8 at the Database level](#utf-8-at-the-database-level)
		- [UTF-8 at the browser level](#utf-8-at-the-browser-level)
		- [Further reading](#further-reading)
- [Dependency Injection](#dependency-injection)
	- [Basic Concept](#basic-concept)
	- [Complex Problem](#complex-problem)
		- [Inversion of Control](#inversion-of-control)
		- [Dependency Inversion Principle](#dependency-inversion-principle)
	- [Containers](#containers)
	- [Further Reading](#further-reading)
- [Databases](#databases)
	- [MySQL Extension](#mysql-extension)
	- [PDO Extension](#pdo-extension)
	- [Interacting with Databases](#interacting-with-databases)
	- [Abstraction Layers](#abstraction-layers)
- [Templating](#templating)
	- [Benefits](#benefits)
	- [Plain PHP Templates](#plain-php-templates)
		- [Simple example of a plain PHP template](#simple-example-of-a-plain-php-template)
		- [Example of plain PHP templates using inheritance](#example-of-plain-php-templates-using-inheritance)
	- [Compiled Templates](#compiled-templates)
		- [Simple example of a compiled template](#simple-example-of-a-compiled-template)
		- [Example of compiled templates using inheritance](#example-of-compiled-templates-using-inheritance)
	- [Further Reading](#further-reading)
		- [Articles & Tutorials](#articles-tutorials)
		- [Libraries](#libraries)
- [Errors and Exceptions](#errors-and-exceptions)
	- [Errors](#errors)
		- [Error Severity](#error-severity)
		- [Changing PHP's Error Reporting Behaviour](#changing-phps-error-reporting-behaviour)
		- [Inline Error Suppression](#inline-error-suppression)
		- [ErrorException](#errorexception)
	- [Exceptions](#exceptions)
		- [SPL Exceptions](#spl-exceptions)
- [Security](#security)
	- [Web Application Security](#web-application-security)
	- [Password Hashing](#password-hashing)
	- [Data Filtering](#data-filtering)
		- [Sanitization](#sanitization)
		- [Unserialization](#unserialization)
		- [Validation](#validation)
	- [Configuration Files](#configuration-files)
	- [Register Globals](#register-globals)
	- [Error Reporting](#error-reporting)
		- [Development](#development)
		- [Production](#production)
- [Testing](#testing)
	- [Test Driven Development](#test-driven-development)
		- [Unit Testing](#unit-testing)
		- [Integration Testing](#integration-testing)
		- [Functional Testing](#functional-testing)
			- [Functional Testing Tools](#functional-testing-tools)
	- [Behavior Driven Development](#behavior-driven-development)
		- [BDD Links](#bdd-links)
	- [Complementary Testing Tools](#complementary-testing-tools)
		- [Tool Links](#tool-links)
- [Servers and Deployment](#servers-and-deployment)
	- [Platform as a Service (PaaS)](#platform-as-a-service-paas)
	- [Virtual or Dedicated Servers](#virtual-or-dedicated-servers)
		- [nginx and PHP-FPM](#nginx-and-php-fpm)
		- [Apache and PHP](#apache-and-php)
	- [Shared Servers](#shared-servers)
	- [Building and Deploying your Application](#building-and-deploying-your-application)
		- [Build Automation Tools](#build-automation-tools)
			- [Chef resources for PHP developers:](#chef-resources-for-php-developers)
			- [Further reading:](#further-reading)
		- [Continuous Integration](#continuous-integration)
			- [Further reading:](#further-reading)
- [Virtualization](#virtualization)
	- [Vagrant](#vagrant)
		- [A little help](#a-little-help)
	- [Docker](#docker)
		- [Example: Running your PHP Applications in Docker](#example-running-your-php-applications-in-docker)
		- [Learn more about Docker](#learn-more-about-docker)
- [Caching](#caching)
	- [Opcode Cache](#opcode-cache)
	- [Object Caching](#object-caching)
		- [Learn more about popular object caching systems:](#learn-more-about-popular-object-caching-systems)
- [Documenting your Code](#documenting-your-code)
	- [PHPDoc](#phpdoc)
- [Resources](#resources)
	- [From the Source](#from-the-source)
	- [People to Follow](#people-to-follow)
	- [Mentoring](#mentoring)
	- [PHP PaaS Providers](#php-paas-providers)
	- [Frameworks](#frameworks)
	- [Components](#components)
	- [Other Useful Resources](#other-useful-resources)
		- [Cheatsheets](#cheatsheets)
		- [More best practices](#more-best-practices)
		- [PHP universe](#php-universe)
	- [Video Tutorials](#video-tutorials)
		- [Youtube Channels](#youtube-channels)
		- [Paid Videos](#paid-videos)
	- [Books](#books)
		- [Free Books](#free-books)
		- [Paid Books](#paid-books)
- [Community](#community)
	- [PHP User Groups](#php-user-groups)
	- [PHP Conferences](#php-conferences)
	- [ElePHPants](#elephpants)

<!-- /TOC -->

## Getting Started




### Use the Current Stable Version (7.0)

If you are getting started with PHP, start with the current stable release of [PHP 7.0][php-release]. PHP 7.0 is very
new, and adds many amazing [new features](#language_highlights) over the older 5.x versions. The engine has been largely re-written, and PHP is now even quicker than older versions.

Most commonly in the near future you will find PHP 5.x being used, and the latest 5.x version is 5.6. This is not a bad option, but you should try to upgrade to the latest stable quickly. Upgrading is really quite easy, as there are not many [backwards compatibility breaks][php70-bc]. If you are not sure which version a function or feature is in, you can check the PHP documentation on the [php.net][php-docs] website.

[php-release]: http://php.net/downloads.php
[php-docs]: http://php.net/manual/
[php70-bc]: http://php.net/manual/migration70.incompatible.php



### Built-in web server

With PHP 5.4 or newer, you can start learning PHP without installing and configuring a full-fledged web server.
To start the server, run the following command from your terminal in your project's web root:

```sh
> php -S localhost:8000
```

* [Learn about the built-in, command line web server][cli-server]


[cli-server]: http://php.net/features.commandline.webserver



### Mac Setup

OS X comes prepackaged with PHP but it is normally a little behind the latest stable. Mavericks has 5.4.17,
Yosemite has 5.5.9 and El Capitan has 5.5.29, but with PHP 7.0 out that is often not good enough.

There are multiple ways to install PHP on OS X.

#### Install PHP via Homebrew

[Homebrew] is a powerful package manager for OS X, which can help you install PHP and various extensions easily.
[Homebrew PHP] is a repository that contains PHP-related "formulae" for Homebrew, and will let you install PHP.

At this point, you can install `php53`, `php54`, `php55`, `php56` or `php70` using the `brew install` command, and switch
between them by modifying your `PATH` variable. Alternatively you can use [brew-php-switcher][brew-php-switcher] which will switch automatically for you.

#### Install PHP via Macports

The [MacPorts] Project is an open-source community initiative to design an
easy-to-use system for compiling, installing, and upgrading either
command-line, X11 or Aqua based open-source software on the OS X operating
system.

MacPorts supports pre-compiled binaries, so you don't need to recompile every
dependencies from the source tarball files, it saves your life if you don't
have any package installed on your system.

At this point, you can install `php54`, `php55`, `php56` or `php70` using the `port install` command, for example:

    sudo port install php56
    sudo port install php70

And you can run `select` command to switch your active php:

    sudo port select --set php php70

#### Install PHP via phpbrew

[phpbrew] is a tool for installing and managing multiple PHP versions. This can be really useful if two different
applications/projects require different versions of PHP, and you are not using virtual machines.

#### Install PHP via Liip's binary installer

Another popular option is [php-osx.liip.ch] which provides one liner installation methods for versions 5.3 through 7.0.
It doesn't overwrite the php binaries installed by Apple, but installs everything in a separate location (/usr/local/php5).

#### Compile from Source

Another option that gives you control over the version of PHP you install, is to [compile it yourself][mac-compile].
In that case be sure to have installed either [Xcode][xcode-gcc-substitution] or Apple's substitute
["Command Line Tools for XCode"] downloadable from Apple's Mac Developer Center.

#### All-in-One Installers

The solutions listed above mainly handle PHP itself, and do not supply things like Apache, Nginx or a SQL server.
"All-in-one" solutions such as [MAMP][mamp-downloads] and [XAMPP][xampp] will install these other bits of software for
you and tie them all together, but ease of setup comes with a trade-off of flexibility.


[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: http://php-osx.liip.ch/
[mac-compile]: http://php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[xampp]: http://www.apachefriends.org/en/xampp.html
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher



### Windows Setup

You can download the binaries from [windows.php.net/download][php-downloads]. After the extraction of PHP, it is recommended to set the [PATH][windows-path] to the root of your PHP folder (where php.exe is located) so you can execute PHP from anywhere.

For learning and local development you can use the built in webserver with PHP 5.4+ so you don't need to worry about
configuring it. If you would like an "all-in-one" which includes a full-blown webserver and MySQL too then tools such
as the [Web Platform Installer][wpi], [XAMPP][xampp], [EasyPHP][easyphp] and [WAMP][wamp] will
help get a Windows development environment up and running fast. That said, these tools will be a little different from
production so be careful of environment differences if you are working on Windows and deploying to Linux.

If you need to run your production system on Windows then IIS7 will give you the most stable and best performance. You
can use [phpmanager][phpmanager] (a GUI plugin for IIS7) to make configuring and managing PHP simple. IIS7 comes with
FastCGI built in and ready to go, you just need to configure PHP as a handler. For support and additional resources
there is a [dedicated area on iis.net][php-iis] for PHP.


[php-downloads]: http://windows.php.net/download/
[windows-path]: http://www.windows-commandline.com/set-path-command-line/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[xampp]: http://www.apachefriends.org/en/xampp.html
[easyphp]: http://www.easyphp.org/
[wamp]: http://www.wampserver.com/en/
[phpmanager]: http://phpmanager.codeplex.com/
[php-iis]: http://php.iis.net/



## Code Style Guide

The PHP community is large and diverse, composed of innumerable libraries, frameworks, and components. It is common for
PHP developers to choose several of these and combine them into a single project. It is important that PHP code adhere
(as close as possible) to a common code style to make it easy for developers to mix and match various libraries for
their projects.

The [Framework Interop Group][fig] has proposed and approved a series of style recommendations. Not all of them related
to code-style, but those that do are [PSR-0][psr0], [PSR-1][psr1], [PSR-2][psr2] and [PSR-4][psr4]. These
recommendations are merely a set of rules that some projects like Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK,
FuelPHP, Lithium, etc are starting to adopt. You can use them for your own projects, or continue to use your own
personal style.

Ideally you should write PHP code that adheres to a known standard. This could be any combination of PSR's, or one
of the coding standards made by PEAR or Zend. This means other developers can easily read and work with your code, and
applications that implement the components can have consistency even when working with lots of third-party code.

* [Read about PSR-0][psr0]
* [Read about PSR-1][psr1]
* [Read about PSR-2][psr2]
* [Read about PSR-4][psr4]
* [Read about PEAR Coding Standards][pear-cs]
* [Read about Symfony Coding Standards][symfony-cs]

You can use [PHP_CodeSniffer][phpcs] to check code against any one of these recommendations, and plugins for text
editors like [Sublime Text 2][st-cs] to be given real time feedback.

You can fix the code layout automatically by using one of the two following tools. One is the [PHP Coding Standards Fixer][phpcsfixer] which has a very well tested codebase.
Another option is [php.tools][phptools], which is made popular by the [sublime-phpfmt][sublime-phpfmt] editor plugin. While being newer, it makes great improvements in performance, meaning real-time editor fixing is more fluid.

And you can run phpcs manually from shell:

    phpcs -sw --standard=PSR2 file.php

It will show errors and descriptions how to fix them.
It can also be helpful to include this command in a git hook.
That way branches which contain violations against the chosen standard cannot enter the repository
until those violations have been fixed.

English is preferred for all symbol names and code infrastructure. Comments may be written in any language easily
readable by all current and future parties who may be working on the codebase.


[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
[phptools]: https://github.com/phpfmt/php.tools
[sublime-phpfmt]: https://github.com/phpfmt/sublime-phpfmt



## Language Highlights



### Programming Paradigms

PHP is a flexible, dynamic language that supports a variety of programming techniques. It has evolved dramatically over
the years, notably adding a solid object-oriented model in PHP 5.0 (2004), anonymous functions and namespaces in
PHP 5.3 (2009), and traits in PHP 5.4 (2012).

#### Object-oriented Programming

PHP has a very complete set of object-oriented programming features including support for classes, abstract classes,
interfaces, inheritance, constructors, cloning, exceptions, and more.

* [Read about Object-oriented PHP][oop]
* [Read about Traits][traits]

#### Functional Programming

PHP supports first-class functions, meaning that a function can be assigned to a variable. Both user-defined and
built-in functions can be referenced by a variable and invoked dynamically. Functions can be passed as arguments to
other functions (a feature called _Higher-order Functions_) and functions can return other functions.

Recursion, a feature that allows a function to call itself, is supported by the language, but most PHP code
is focused on iteration.

New anonymous functions (with support for closures) are present since PHP 5.3 (2009).

PHP 5.4 added the ability to bind closures to an object's scope and also improved support for callables such that they
can be used interchangeably with anonymous functions in almost all cases.

* Continue reading on [Functional Programming in PHP](/pages/Functional-Programming.html)
* [Read about Anonymous Functions][anonymous-functions]
* [Read about the Closure class][closure-class]
* [More details in the Closures RFC][closures-rfc]
* [Read about Callables][callables]
* [Read about dynamically invoking functions with `call_user_func_array()`][call-user-func-array]

#### Meta Programming

PHP supports various forms of meta-programming through mechanisms like the Reflection API and Magic Methods. There are
many Magic Methods available like `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, etc. that allow
developers to hook into class behavior. Ruby developers often say that PHP is lacking `method_missing`, but it is
available as `__call()` and `__callStatic()`.

* [Read about Magic Methods][magic-methods]
* [Read about Reflection][reflection]
* [Read about Overloading][overloading]


[oop]: http://php.net/language.oop5
[traits]: http://php.net/language.oop5.traits
[anonymous-functions]: http://php.net/functions.anonymous
[closure-class]: http://php.net/class.closure
[closures-rfc]: https://wiki.php.net/rfc/closures
[callables]: http://php.net/language.types.callable
[call-user-func-array]: http://php.net/function.call-user-func-array
[magic-methods]: http://php.net/language.oop5.magic
[reflection]: http://php.net/intro.reflection
[overloading]: http://php.net/language.oop5.overloading




### Namespaces

As mentioned above, the PHP community has a lot of developers creating lots of code. This means that one library's PHP
code may use the same class name as another library. When both libraries are used in the same namespace, they collide
and cause trouble.

_Namespaces_ solve this problem. As described in the PHP reference manual, namespaces may be compared to operating
system directories that _namespace_ files; two files with the same name may co-exist in separate directories. Likewise,
two PHP classes with the same name may co-exist in separate PHP namespaces. It's as simple as that.

It is important for you to namespace your code so that it may be used by other developers without fear of colliding
with other libraries.

One recommended way to use namespaces is outlined in [PSR-4][psr4], which aims to provide a standard file, class and
namespace convention to allow plug-and-play code.

In October 2014 the PHP-FIG deprecated the previous autoloading standard: [PSR-0][psr0], which has been replaced with
[PSR-4][psr4]. Currently both are still perfectly usable and PSR-0 is not going away. As PSR-4 requires PHP 5.3 and
many PHP 5.2-only projects currently implement PSR-0. Luckily those PHP 5.2-only projects are starting to up their
version requirements, meaning PSR-0 is being used less and less.

If you're going to use an autoloader standard for a new application or package then you almost certainly want
to look into PSR-4.

* [Read about Namespaces][namespaces]
* [Read about PSR-0][psr0]
* [Read about PSR-4][psr4]


[namespaces]: http://php.net/language.namespaces
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md



### Standard PHP Library

The Standard PHP Library (SPL) is packaged with PHP and provides a collection of classes and interfaces. It is made up
primarily of commonly needed datastructure classes (stack, queue, heap, and so on), and iterators which can traverse
over these datastructures or your own classes which implement SPL interfaces.

* [Read about the SPL][spl]
* [SPL video course on Lynda.com(Paid)][spllynda]


[spl]: http://php.net/book.spl
[spllynda]: http://www.lynda.com/PHP-tutorials/Up-Running-Standard-PHP-Library/175038-2.html



### Command Line Interface

PHP was created to write web applications, but is also useful for scripting command line interface (CLI) programs.
Command line PHP programs can help automate common tasks like testing, deployment, and application administration.

CLI PHP programs are powerful because you can use your app's code directly without having to create and secure a web
GUI for it. Just be sure **not** to put your CLI PHP scripts in your public web root!

Try running PHP from your command line:

```sh
> php -i
```

The `-i` option will print your PHP configuration just like the [`phpinfo()`][phpinfo] function.

The `-a` option provides an interactive shell, similar to ruby's IRB or python's interactive shell. There are a number
of other useful [command line options][cli-options], too.

Let's write a simple "Hello, $name" CLI program. To try it out, create a file named `hello.php`, as below.

```php
<?php
if ($argc !== 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
```

PHP sets up two special variables based on the arguments your script is run with. [`$argc`][argc] is an integer
variable containing the argument *count* and [`$argv`][argv] is an array variable containing each argument's *value*.
The first argument is always the name of your PHP script file, in this case `hello.php`.

The `exit()` expression is used with a non-zero number to let the shell know that the command failed. Commonly used
exit codes can be found [here][exit-codes].

To run our script, above, from the command line:

```sh
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
```


 * [Learn about running PHP from the command line][php-cli]
 * [Learn about setting up Windows to run PHP from the command line][php-cli-windows]


[phpinfo]: http://php.net/function.phpinfo
[cli-options]: http://php.net/features.commandline.options
[argc]: http://php.net/reserved.variables.argc
[argv]: http://php.net/reserved.variables.argv
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&amp;topic=sysexits
[php-cli]: http://php.net/features.commandline
[php-cli-windows]: http://php.net/install.windows.commandline



### Xdebug

One of the most useful tools in software development is a proper debugger. It allows you to trace the execution of your
code and monitor the contents of the stack. Xdebug, PHP's debugger, can be utilized by various IDEs to provide
Breakpoints and stack inspection. It can also allow tools like PHPUnit and KCacheGrind to perform code coverage
analysis and code profiling.

If you find yourself in a bind, willing to resort to `var_dump()`/`print_r()`, and you still can't find the solution -
maybe you need to use the debugger.

[Installing Xdebug][xdebug-install] can be tricky, but one of its most important features is "Remote Debugging" - if
you develop code locally and then test it inside a VM or on another server, Remote Debugging is the feature that you
will want to enable right away.

Traditionally, you will modify your Apache VHost or .htaccess file with these values:

{% highlight ini %}
php_value xdebug.remote_host=192.168.?.?
php_value xdebug.remote_port=9000
```

The "remote host" and "remote port" will correspond to your local computer and the port that you configure your IDE to
listen on. Then it's just a matter of putting your IDE into "listen for connections" mode, and loading the URL:

    http://your-website.example.com/index.php?XDEBUG_SESSION_START=1

Your IDE will now intercept the current state as the script executes, allowing you to set breakpoints and probe the
values in memory.

Graphical debuggers make it very easy to step through code, inspect variables, and eval code against the live runtime.
Many IDE's have built-in or plugin-based support for graphical debugging with Xdebug. MacGDBp is a free, open-source,
stand-alone Xdebug GUI for Mac.

 * [Learn more about Xdebug][xdebug-docs]
 * [Learn more about MacGDBp][macgdbp-install]


[xdebug-install]: http://xdebug.org/docs/install
[xdebug-docs]: http://xdebug.org/docs/
[macgdbp-install]: http://www.bluestatic.org/software/macgdbp/



## Dependency Management

There are a ton of PHP libraries, frameworks, and components to choose from. Your project will likely use
several of them — these are project dependencies. Until recently, PHP did not have a good way to manage
these project dependencies. Even if you managed them manually, you still had to worry about autoloaders.
That is no longer an issue.

Currently there are two major package management systems for PHP - [Composer] and [PEAR]. Composer is currently
the most popular package manager for PHP, however for a long time PEAR was the primary package manager in use.
Knowing PEAR's history is a good idea, since you may still find references to it even if you never use it.

[Composer]: /#composer_and_packagist
[PEAR]: /#pear



### Composer and Packagist

Composer is a **brilliant** dependency manager for PHP. List your project's dependencies in a `composer.json` file and,
with a few simple commands, Composer will automatically download your project's dependencies and setup autoloading for
you. Composer is analogous to NPM in the node.js world, or Bundler in the Ruby world.

There are already a lot of PHP libraries that are compatible with Composer, ready to be used in your project. These
"packages" are listed on [Packagist], the official repository for Composer-compatible PHP libraries.

#### How to Install Composer

You can install Composer locally (in your current working directory) or globally (e.g. /usr/local/bin, recommended).
Let's assume you want to install Composer globally:

```sh
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
```

**Note:** If the above fails due to permissions, run the `mv` line again with `sudo`.

This will download `composer.phar` (a PHP binary archive). You can run this with `php` to manage your project
dependencies.

**Please Note:** If you pipe downloaded code directly into an interpreter, please read the
code online first to confirm it is safe.

##### Installing on Windows

For Windows users the easiest way to get up and running is to use the [ComposerSetup] installer, which
performs a global install and sets up your `$PATH` so that you can just call `composer` from any
directory in your command line.

#### How to Install Composer (manually)

Manually installing Composer is an advanced technique; however, there are various reasons why a
developer might prefer this method vs. using the interactive installation routine. The interactive
installation checks your PHP installation to ensure that:

- a sufficient version of PHP is being used
- `.phar` files can be executed correctly
- certain directory permissions are sufficient
- certain problematic extensions are not loaded
- certain `php.ini` settings are set

Since a manual installation performs none of these checks, you have to decide whether the trade-off is
worth it for you. As such, below is how to obtain Composer manually:

```sh
curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
chmod +x $HOME/local/bin/composer
```

The path `$HOME/local/bin` (or a directory of your choice) should be in your `$PATH` environment
variable. This will result in a `composer` command being available.

When you come across documentation that states to run Composer as `php composer.phar install`, you can
substitute that with:

```sh
composer install
```

This section will assume you have installed composer globally.

#### How to Define and Install Dependencies

Composer keeps track of your project's dependencies in a file called `composer.json`. You can manage it
by hand if you like, or use Composer itself. The `composer require` command adds a project dependency
and if you don't have a `composer.json` file, one will be created. Here's an example that adds [Twig]
as a dependency of your project.

```sh
composer require twig/twig:~1.8
```

Alternatively the `composer init` command will guide you through creating a full `composer.json` file
for your project. Either way, once you've created your `composer.json` file you can tell Composer to
download and install your dependencies into the `vendor/` directory. This also applies to projects
you've downloaded that already provide a `composer.json` file:

```sh
composer install
```

Next, add this line to your application's primary PHP file; this will tell PHP to use Composer's
autoloader for your project dependencies.

```php
<?php
require 'vendor/autoload.php';
```

Now you can use your project dependencies, and they'll be autoloaded on demand.

#### Updating your dependencies

Composer creates a file called `composer.lock` which stores the exact version of each package it
downloaded when you
first ran `composer install`. If you share your project with other coders and the `composer.lock` file
is part of your distribution, when they run `composer install` they'll get the same versions as you.
To update your dependencies, run `composer update`.

This is most useful when you define your version requirements flexibly. For instance a version
requirement of `~1.8` means "anything newer than `1.8.0`, but less than `2.0.x-dev`". You can also use
the `*` wildcard as in `1.8.*`. Now Composer's `composer update` command will upgrade all your
dependencies to the newest version that fits the restrictions you define.

#### Update Notifications

To receive notifications about new version releases you can sign up for [VersionEye], a web service
that can monitor your GitHub and BitBucket accounts for `composer.json` files and send emails with new
package releases.

#### Checking your dependencies for security issues

The [Security Advisories Checker] is a web service and a command-line tool, both will examine your `composer.lock`
file and tell you if you need to update any of your dependencies.

#### Handling global dependencies with Composer

Composer can also handle global dependencies and their binaries. Usage is straight-forward, all you need
to do is prefix your command with `global`. If for example you wanted to install PHPUnit and have it
available globally, you'd run the following command:

```sh
composer global require phpunit/phpunit
```

This will create a `~/.composer` folder where your global dependencies reside. To have the installed
packages' binaries available everywhere, you'd then add the `~/.composer/vendor/bin` folder to your
`$PATH` variable.

* [Learn about Composer]

[Packagist]: http://packagist.org/
[Twig]: http://twig.sensiolabs.org
[VersionEye]: https://www.versioneye.com/
[Security Advisories Checker]: https://security.sensiolabs.org/
[Learn about Composer]: http://getcomposer.org/doc/00-intro.md
[ComposerSetup]: https://getcomposer.org/Composer-Setup.exe



### PEAR

A veteran package manager that some PHP developers enjoy is [PEAR][1]. It behaves similarly to Composer,
but has some notable differences.

PEAR requires each package to have a specific structure, which means that the author of the package must prepare it for
usage with PEAR. Using a project which was not prepared to work with PEAR is not possible.

PEAR installs packages globally, which means after installing them once they are available to all projects on that
server. This can be good if many projects rely on the same package with the same version but might lead to problems if
version conflicts between two projects arise.

#### How to install PEAR

You can install PEAR by downloading the `.phar` installer and executing it. The PEAR documentation has
detailed [install instructions][2] for every operating system.

If you are using Linux, you can also have a look at your distribution package manager. Debian and Ubuntu,
for example, have an apt `php-pear` package.

#### How to install a package

If the package is listed on the [PEAR packages list][3], you can install it by specifying the official name:

```sh
pear install foo
```

If the package is hosted on another channel, you need to `discover` the channel first and also specify it when
installing. See the [Using channel docs][4] for more information on this topic.

* [Learn about PEAR][1]

#### Handling PEAR dependencies with Composer

If you are already using [Composer][5] and you would like to install some PEAR code too, you can use Composer to
handle your PEAR dependencies. This example will install code from `pear2.php.net`:

{% highlight json %}
{
    "repositories": [
        {
            "type": "pear",
            "url": "http://pear2.php.net"
        }
    ],
    "require": {
        "pear-pear2/PEAR2_Text_Markdown": "*",
        "pear-pear2/PEAR2_HTTP_Request": "*"
    }
}
```

The first section `"repositories"` will be used to let Composer know it should "initialize" (or "discover" in PEAR
terminology) the pear repo. Then the require section will prefix the package name like this:

> pear-channel/Package

The "pear" prefix is hardcoded to avoid any conflicts, as a pear channel could be the same as another packages vendor
name for example, then the channel short name (or full URL) can be used to reference which channel the package is in.

When this code is installed it will be available in your vendor directory and automatically available through the
Composer autoloader:

> vendor/pear-pear2.php.net/PEAR2_HTTP_Request/pear2/HTTP/Request.php

To use this PEAR package simply reference it like so:

```php
<?php
$request = new pear2\HTTP\Request();
```

* [Learn more about using PEAR with Composer][6]


[1]: http://pear.php.net/
[2]: http://pear.php.net/manual/en/installation.getting.php
[3]: http://pear.php.net/packages.php
[4]: http://pear.php.net/manual/en/guide.users.commandline.channels.php
[5]: /#composer_and_packagist
[6]: http://getcomposer.org/doc/05-repositories.md#pear



## Coding Practices



### The Basics

PHP is a vast language that allows coders of all levels the ability to produce code not only quickly, but efficiently.
However while advancing through the language, we often forget the basics that we first learnt (or overlooked) in favor
of short cuts and/or bad habits. To help combat this common issue, this section is aimed at reminding coders of the
basic coding practices within PHP.

* Continue reading on [The Basics](/pages/The-Basics.html)



### Date and Time

PHP has a class named DateTime to help you when reading, writing, comparing or calculating with date and time. There
are many date and time related functions in PHP besides DateTime, but it provides nice object-oriented interface to
most common uses. It can handle time zones, but that is outside this short introduction.

To start working with DateTime, convert raw date and time string to an object with `createFromFormat()` factory method
or do `new DateTime` to get the current date and time. Use `format()` method to convert DateTime back to a string for
output.

```php
<?php
$raw = '22. 11. 1968';
$start = DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('Y-m-d') . "\n";
```

Calculating with DateTime is possible with the DateInterval class. DateTime has methods like `add()` and `sub()` that
take a DateInterval as an argument. Do not write code that expect same number of seconds in every day, both daylight
saving and timezone alterations will break that assumption. Use date intervals instead. To calculate date difference
use the `diff()` method. It will return new DateInterval, which is super easy to display.

```php
<?php
// create a copy of $start and add one month and 6 days
$end = clone $start;
$end->add(new DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Difference: 1 month, 6 days (total: 37 days)
```

On DateTime objects you can use standard comparison:

```php
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
```

One last example to demonstrate the DatePeriod class. It is used to iterate over recurring events. It can take two
DateTime objects, start and end, and the interval for which it will return all events in between.

```php
<?php
// output all thursdays between $start and $end
$periodInterval = DateInterval::createFromDateString('first thursday');
$periodIterator = new DatePeriod($start, $periodInterval, $end, DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('Y-m-d') . ' ';
}
```

* [Read about DateTime][datetime]
* [Read about date formatting][dateformat] (accepted date format string options)

[datetime]: http://php.net/book.datetime
[dateformat]: http://php.net/function.date



### Design Patterns

When you are building your application it is helpful to use common patterns in your code and common patterns for the
overall structure of your project. Using common patterns is helpful because it makes it much easier to manage your code
and lets other developers quickly understand how everything fits together.

If you use a framework then most of the higher level code and project structure will be based on that framework, so a
lot of the pattern decisions are made for you. But it is still up to you to pick out the best patterns to follow in the
code you build on top of the framework. If, on the other hand, you are not using a framework to build your application
then you have to find the patterns that best suit the type and size of application that you're building.

* Continue reading on [Design Patterns](/pages/Design-Patterns.html)



### Working with UTF-8

_This section was originally written by [Alex Cabal](https://alexcabal.com/) over at
[PHP Best Practices](https://phpbestpractices.org/#utf-8) and has been used as the basis for our own UTF-8 advice_.

#### There's no one-liner. Be careful, detailed, and consistent.

Right now PHP does not support Unicode at a low level. There are ways to ensure that UTF-8 strings are processed OK,
but it's not easy, and it requires digging in to almost all levels of the web app, from HTML to SQL to PHP. We'll aim
for a brief, practical summary.

#### UTF-8 at the PHP level

The basic string operations, like concatenating two strings and assigning strings to variables, don't need anything
special for UTF-8. However most string functions, like `strpos()` and `strlen()`, do need special consideration. These
functions often have an `mb_*` counterpart: for example, `mb_strpos()` and `mb_strlen()`. These `mb_*` strings are made
available to you via the [Multibyte String Extension], and are specifically designed to operate on Unicode strings.

You must use the `mb_*` functions whenever you operate on a Unicode string. For example, if you use `substr()` on a
UTF-8 string, there's a good chance the result will include some garbled half-characters. The correct function to use
would be the multibyte counterpart, `mb_substr()`.

The hard part is remembering to use the `mb_*` functions at all times. If you forget even just once, your Unicode
string has a chance of being garbled during further processing.

Not all string functions have an `mb_*` counterpart. If there isn't one for what you want to do, then you might be out
of luck.

You should use the `mb_internal_encoding()` function at the top of every PHP script you write (or at the top of your
global include script), and the `mb_http_output()` function right after it if your script is outputting to a browser.
Explicitly defining the encoding of your strings in every script will save you a lot of headaches down the road.

Additionally, many PHP functions that operate on strings have an optional parameter letting you specify the character
encoding. You should always explicitly indicate UTF-8 when given the option. For example, `htmlentities()` has an
option for character encoding, and you should always specify UTF-8 if dealing with such strings. Note that as of PHP 5.4.0, UTF-8 is the default encoding for `htmlentities()` and `htmlspecialchars()`.

Finally, If you are building a distributed application and cannot be certain that the `mbstring` extension will be
enabled, then consider using the [patchwork/utf8] Composer package. This will use `mbstring` if it is available, and
fall back to non UTF-8 functions if not.

[Multibyte String Extension]: http://php.net/book.mbstring
[patchwork/utf8]: https://packagist.org/packages/patchwork/utf8

#### UTF-8 at the Database level

If your PHP script accesses MySQL, there's a chance your strings could be stored as non-UTF-8 strings in the database
even if you follow all of the precautions above.

To make sure your strings go from PHP to MySQL as UTF-8, make sure your database and tables are all set to the
`utf8mb4` character set and collation, and that you use the `utf8mb4` character set in the PDO connection string. See
example code below. This is _critically important_.

Note that you must use the `utf8mb4` character set for complete UTF-8 support, not the `utf8` character set! See
Further Reading for why.

#### UTF-8 at the browser level

Use the `mb_http_output()` function to ensure that your PHP script outputs UTF-8 strings to your browser.

The browser will then need to be told by the HTTP response that this page should be considered as UTF-8. The historic
approach to doing that was to include the [charset `<meta>` tag](http://htmlpurifier.org/docs/enduser-utf8.html) in
your page's `<head>` tag. This approach is perfectly valid, but setting the charset in the `Content-Type` header is
actually [much faster](https://developers.google.com/speed/docs/best-practices/rendering#SpecifyCharsetEarly).

```php
<?php
// Tell PHP that we're using UTF-8 strings until the end of the script
mb_internal_encoding('UTF-8');

// Tell PHP that we'll be outputting UTF-8 to the browser
mb_http_output('UTF-8');

// Our UTF-8 test string
$string = 'Êl síla erin lû e-govaned vîn.';

// Transform the string in some way with a multibyte function
// Note how we cut the string at a non-Ascii character for demonstration purposes
$string = mb_substr($string, 0, 15);

// Connect to a database to store the transformed string
// See the PDO example in this document for more information
// Note the `charset=utf8mb4` in the Data Source Name (DSN)
$link = new PDO(
    'mysql:host=your-hostname;dbname=your-db;charset=utf8mb4',
    'your-username',
    'your-password',
    array(
        PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
        PDO::ATTR_PERSISTENT => false
    )
);

// Store our transformed string as UTF-8 in our database
// Your DB and tables are in the utf8mb4 character set and collation, right?
$handle = $link->prepare('insert into ElvishSentences (Id, Body) values (?, ?)');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->bindValue(2, $string);
$handle->execute();

// Retrieve the string we just stored to prove it was stored correctly
$handle = $link->prepare('select * from ElvishSentences where Id = ?');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->execute();

// Store the result into an object that we'll output later in our HTML
$result = $handle->fetchAll(\PDO::FETCH_OBJ);

header('Content-Type: text/html; charset=UTF-8');
?><!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>UTF-8 test page</title>
    </head>
    <body>
        <?php
        foreach($result as $row){
            print($row->Body);  // This should correctly output our transformed UTF-8 string to the browser
        }
        ?>
    </body>
</html>
```

#### Further reading

* [PHP Manual: String Operations](http://php.net/language.operators.string)
* [PHP Manual: String Functions](http://php.net/ref.strings)
    * [`strpos()`](http://php.net/function.strpos)
    * [`strlen()`](http://php.net/function.strlen)
    * [`substr()`](http://php.net/function.substr)
* [PHP Manual: Multibyte String Functions](http://php.net/ref.mbstring)
    * [`mb_strpos()`](http://php.net/function.mb-strpos)
    * [`mb_strlen()`](http://php.net/function.mb-strlen)
    * [`mb_substr()`](http://php.net/function.mb-substr)
    * [`mb_internal_encoding()`](http://php.net/function.mb-internal-encoding)
    * [`mb_http_output()`](http://php.net/function.mb-http-output)
    * [`htmlentities()`](http://php.net/function.htmlentities)
    * [`htmlspecialchars()`](http://php.net/function.htmlspecialchars)
* [PHP UTF-8 Cheatsheet](http://blog.loftdigital.com/blog/php-utf-8-cheatsheet)
* [Handling UTF-8 with PHP](http://www.phpwact.org/php/i18n/utf-8)
* [Stack Overflow: What factors make PHP Unicode-incompatible?](http://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Stack Overflow: Best practices in PHP and MySQL with international strings](http://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [How to support full Unicode in MySQL databases](http://mathiasbynens.be/notes/mysql-utf8mb4)
* [Bringing Unicode to PHP with Portable UTF-8](http://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)
* [Stack Overflow: DOMDocument loadHTML does not encode UTF-8 correctly](http://stackoverflow.com/questions/8218230/php-domdocument-loadhtml-not-encoding-utf-8-correctly)


title:  Dependency Injection

## Dependency Injection

From [Wikipedia](http://en.wikipedia.org/wiki/Dependency_injection):

> Dependency injection is a software design pattern that allows the removal of hard-coded dependencies and makes it
> possible to change them, whether at run-time or compile-time.

This quote makes the concept sound much more complicated than it actually is. Dependency Injection is providing a
component with its dependencies either through constructor injection, method calls or the setting of properties. It is
that simple.



### Basic Concept

We can demonstrate the concept with a simple, yet naive example.

Here we have a `Database` class that requires an adapter to speak to the database. We instantiate the adapter in the
constructor and create a hard dependency. This makes testing difficult and means the `Database` class is very tightly
coupled to the adapter.

```php
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}
```

This code can be refactored to use Dependency Injection and therefore loosen the dependency.

```php
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}
```

Now we are giving the `Database` class its dependency rather than it creating it itself. We could even create a method
that would accept an argument of the dependency and set it that way, or if the `$adapter` property was `public` we
could set it directly.



### Complex Problem

If you have ever read about Dependency Injection then you have probably seen the terms *"Inversion of Control"* or
*"Dependency Inversion Principle"*. These are the complex problems that Dependency Injection solves.

#### Inversion of Control

Inversion of Control is as it says, "inverting the control" of a system by keeping organisational control entirely
separate from our objects. In terms of Dependency Injection, this means loosening our dependencies by controlling and
instantiating them elsewhere in the system.

For years, PHP frameworks have been achieving Inversion of Control, however, the question became, which part of control
are you inverting, and where to? For example, MVC frameworks would generally provide a super object or base controller
that other controllers must extend to gain access to its dependencies. This **is** Inversion of Control, however,
instead of loosening dependencies, this method simply moved them.

Dependency Injection allows us to more elegantly solve this problem by only injecting the dependencies we need, when we
need them, without the need for any hard coded dependencies at all.

#### Dependency Inversion Principle

Dependency Inversion Principle is the "D" in the S.O.L.I.D set of object oriented design principles that states one
should *"Depend on Abstractions. Do not depend on concretions."*. Put simply, this means our dependencies should be
interfaces/contracts or abstract classes rather than concrete implementations. We can easily refactor the above example
to follow this principle.

```php
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(AdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
}

interface AdapterInterface {}

class MysqlAdapter implements AdapterInterface {}
```

There are several benefits to the `Database` class now depending on an interface rather than a concretion.

Consider that you are working in a team and the adapter is being worked on by a colleague. In our first example, we
would have to wait for said colleague to finish the adapter before we could properly mock it for our unit tests. Now
that the dependency is an interface/contract we can happily mock that interface knowing that our colleague will build
the adapter based on that contract.

An even bigger benefit to this method is that our code is now much more scalable. If a year down the line we decide
that we want to migrate to a different type of database, we can write an adapter that implements the original interface
and inject that instead, no more refactoring would be required as we can ensure that the adapter follows the contract
set by the interface.



### Containers

The first thing you should understand about Dependency Injection Containers is that they are not the same thing as
Dependency Injection. A container is a convenience utility that helps us implement Dependency Injection, however, they
can be and often are misused to implement an anti-pattern, Service Location. Injecting a DI container as a Service
Locator in to your classes arguably creates a harder dependency on the container than the dependency you are replacing.
It also makes your code much less transparent and ultimately harder to test.

Most modern frameworks have their own Dependency Injection Container that allows you to wire your dependencies together
through configuration. What this means in practice is that you can write application code that is as clean and de-
coupled as the framework it is built on.



### Further Reading

* [Learning about Dependency Injection and PHP](http://ralphschindler.com/2011/05/18/learning-about-dependency-injection-and-php)
* [What is Dependency Injection?](http://fabien.potencier.org/article/11/what-is-dependency-injection)
* [Dependency Injection: An analogy](https://mwop.net/blog/260-Dependency-Injection-An-analogy.html)
* [Dependency Injection: Huh?](http://net.tutsplus.com/tutorials/php/dependency-injection-huh/)
* [Dependency Injection as a tool for testing](http://philipobenito.github.io/dependency-injection-as-a-tool-for-testing/)


title:  Databases

## Databases

Many times your PHP code will use a database to persist information. You have a few options to connect and interact
with your database. The recommended option **until PHP 5.1.0** was to use native drivers such as [mysqli], [pgsql],
[mssql], etc.

Native drivers are great if you are only using _one_ database in your application, but if, for example, you are using
MySQL and a little bit of MSSQL, or you need to connect to an Oracle database, then you will not be able to use the
same drivers. You'll need to learn a brand new API for each database &mdash; and that can get silly.


[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql



### MySQL Extension

The [mysql] extension for PHP is incredibly old and has superseded by two other extensions:

- [mysqli]
- [pdo]

Not only did development stop long ago on [mysql], but it was [deprecated as of PHP 5.5.0]
[mysql_deprecated], and **has been [officially removed in PHP 7.0][mysql_removed]**.

To save digging into your `php.ini` settings to see which module you are using, one option is to search for `mysql_*`
in your editor of choice. If any functions such as `mysql_connect()` and `mysql_query()` show up, then `mysql` is
in use.

Even if you are not using PHP 7.0 yet, failing to consider this upgrade as soon as possible will lead to greater
hardship when the PHP 7.0 upgrade does come about. The best option is to replace mysql usage with [mysqli] or [PDO] in
your applications within your own development schedules so you won't be rushed later on.

**If you are upgrading from [mysql] to [mysqli], beware lazy upgrade guides that suggest you can simply find and replace `mysql_*` with `mysqli_*`. Not only is that a gross oversimplification, it misses out on the advantages that mysqli provides, such as parameter binding, which is also offered in [PDO][pdo].**

* [PHP: Choosing an API for MySQL][mysql_api]
* [PDO Tutorial for MySQL Developers][pdo4mysql_devs]

[mysql]: http://php.net/mysql
[mysql_deprecated]: http://php.net/migration55.deprecated
[mysql_removed]: http://php.net/manual/en/migration70.removed-exts-sapis.php
[mysqli]: http://php.net/mysqli
[pdo]: http://php.net/pdo
[mysql_api]: http://php.net/mysqlinfo.api.choosing
[pdo4mysql_devs]: http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers



### PDO Extension

[PDO] is a database connection abstraction library &mdash; built into PHP since 5.1.0 &mdash; that provides a common
interface to talk with many different databases. For example, you can use basically identical code to interface with
MySQL or SQLite:

```php
<?php
// PDO + MySQL
$pdo = new PDO('mysql:host=example.com;dbname=database', 'user', 'password');
$statement = $pdo->query("SELECT some_field FROM some_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);

// PDO + SQLite
$pdo = new PDO('sqlite:/path/db/foo.sqlite');
$statement = $pdo->query("SELECT some_field FROM some_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);
```

PDO will not translate your SQL queries or emulate missing features; it is purely for connecting to multiple types of
database with the same API.

More importantly, `PDO` allows you to safely inject foreign input (e.g. IDs) into your SQL queries without worrying
about database SQL injection attacks.
This is possible using PDO statements and bound parameters.

Let's assume a PHP script receives a numeric ID as a query parameter. This ID should be used to fetch a user record
from a database. This is the `wrong` way to do this:

```php
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
```

This is terrible code. You are inserting a raw query parameter into a SQL query. This will get you hacked in a
heartbeat, using a practice called [SQL Injection]. Just imagine if a hacker passes in an inventive `id` parameter by
calling a URL like `http://domain.com/?id=1%3BDELETE+FROM+users`. This will set the `$_GET['id']` variable to `1;DELETE
FROM users` which will delete all of your users! Instead, you should sanitize the ID input using PDO bound parameters.

```php
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$id = filter_input(INPUT_GET, 'id', FILTER_SANITIZE_NUMBER_INT); // <-- filter your data first (see [Data Filtering](#data_filtering)), especially important for INSERT, UPDATE, etc.
$stmt->bindParam(':id', $id, PDO::PARAM_INT); // <-- Automatically sanitized for SQL by PDO
$stmt->execute();
```

This is correct code. It uses a bound parameter on a PDO statement. This escapes the foreign input ID before it is
introduced to the database preventing potential SQL injection attacks.

For writes, such as INSERT or UPDATE, it's especially critical to still [filter your data](#data_filtering) first and sanitize it for other things (removal of HTML tags, JavaScript, etc).  PDO will only sanitize it for SQL, not for your application.

* [Learn about PDO]

You should also be aware that database connections use up resources and it was not unheard-of to have resources
exhausted if connections were not implicitly closed, however this was more common in other languages. Using PDO you can
implicitly close the connection by destroying the object by ensuring all remaining references to it are deleted, i.e.
set to NULL. If you don't do this explicitly, PHP will automatically close the connection when your script ends -
unless of course you are using persistent connections.

* [Learn about PDO connections]


[pdo]: http://php.net/pdo
[SQL Injection]: http://wiki.hashphp.org/Validation
[Learn about PDO]: http://php.net/book.pdo
[Learn about PDO connections]: http://php.net/pdo.connections



### Interacting with Databases

When developers first start to learn PHP, they often end up mixing their database interaction up with their
presentation logic, using code that might look like this:

```php
<ul>
<?php
foreach ($db->query('SELECT * FROM table') as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>";
}
?>
</ul>
```

This is bad practice for all sorts of reasons, mainly that its hard to debug, hard to test, hard to read and it is
going to output a lot of fields if you don't put a limit on there.

While there are many other solutions to doing this - depending on if you prefer [OOP](/#object-oriented-programming) or
[functional programming](/#functional-programming) - there must be some element of separation.

Consider the most basic step:

```php
<?php
function getAllFoos($db) {
    return $db->query('SELECT * FROM table');
}

foreach (getAllFoos($db) as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>"; // BAD!!
}
```

That is a good start. Put those two items in two different files and you've got some clean separation.

Create a class to place that method in and you have a "Model". Create a simple `.php` file to put the presentation
logic in and you have a "View", which is very nearly [MVC] - a common OOP architecture for most
[frameworks](/#frameworks).

**foo.php**

```php
<?php
$db = new PDO('mysql:host=localhost;dbname=testdb;charset=utf8', 'username', 'password');

// Make your model available
include 'models/FooModel.php';

// Create an instance
$fooModel = new FooModel($db);
// Get the list of Foos
$fooList = $fooModel->getAllFoos();

// Show the view
include 'views/foo-list.php';
```


**models/FooModel.php**

```php
<?php
class FooModel
{
    protected $db;

    public function __construct(PDO $db)
    {
        $this->db = $db;
    }

    public function getAllFoos() {
        return $this->db->query('SELECT * FROM table');
    }
}
```

**views/foo-list.php**

```php
<?php foreach ($fooList as $row): ?>
    <?= $row['field1'] ?> - <?= $row['field1'] ?>
<?php endforeach ?>
```

This is essentially the same as what most modern frameworks are doing, albeit a little more manual. You might not
need to do all of that every time, but mixing together too much presentation logic and database interaction can be a
real problem if you ever want to [unit-test](/#unit-testing) your application.

[PHPBridge] has a great resource called [Creating a Data Class] which covers a very similar topic, and is great for
developers just getting used to the concept of interacting with databases.


[MVC]: http://code.tutsplus.com/tutorials/mvc-for-noobs--net-10488
[PHPBridge]: http://phpbridge.org/
[Creating a Data Class]: http://phpbridge.org/intro-to-php/creating_a_data_class



### Abstraction Layers

Many frameworks provide their own abstraction layer which may or may not sit on top of [PDO][1]. These will often
emulate features for one database system that is missing from another by wrapping your queries in PHP methods, giving
you actual database abstraction instead of just the connection abstraction that PDO provides. This will of course add a
little overhead, but if you are building a portable application that needs to work with MySQL, PostgreSQL and SQLite
then a little overhead will be worth it the sake of code cleanliness.

Some abstraction layers have been built using the [PSR-0][psr0] or [PSR-4][psr4] namespace standards so can be
installed in any application you like:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]


[1]: http://php.net/book.pdo
[2]: http://www.doctrine-project.org/projects/dbal.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md


title:  Templating

## Templating

Templates provide a convenient way of separating your controller and domain logic from your presentation logic.
Templates typically contain the HTML of your application, but may also be used for other formats, such as XML.
Templates are often referred to as "views", which make up **part of** the second component of the
[model–view–controller](/pages/Design-Patterns.html#model-view-controller) (MVC) software architecture pattern.



### Benefits

The main benefit to using templates is the clear separation they create between the presentation logic and the rest of
your application. Templates have the sole responsibility of displaying formatted content. They are not responsible for
data lookup, persistence or other more complex tasks. This leads to cleaner, more readable code which is especially
helpful in a team environment where developers work on the server-side code (controllers, models) and designers work on
the client-side code (markup).

Templates also improve the organization of presentation code. Templates are typically placed in a "views" folder, each
defined within a single file. This approach encourages code reuse where larger blocks of code are broken into smaller,
reusable pieces, often called partials. For example, your site header and footer can each be defined as templates,
which are then included before and after each page template.

Finally, depending on the library you use, templates can offer more security by automatically escaping user-generated
content. Some libraries even offer sand-boxing, where template designers are only given access to white-listed
variables and functions.



### Plain PHP Templates

Plain PHP templates are simply templates that use native PHP code. They are a natural choice since PHP is actually a
template language itself. That simply means that you can combine PHP code within other code, like HTML. This is
beneficial to PHP developers as there is no new syntax to learn, they know the functions available to them, and their
code editors already have PHP syntax highlighting and auto-completion built-in. Further, plain PHP templates tend to be
very fast as no compiling stage is required.

Every modern PHP framework employs some kind of template system, most of which use plain PHP by default. Outside of
frameworks, libraries like [Plates][plates] or [Aura.View][aura] make working with plain PHP templates easier by
offering modern template functionality such as inheritance, layouts and extensions.

#### Simple example of a plain PHP template

Using the [Plates][plates] library.

```php
<?php // user_profile.php ?>

<?php $this->insert('header', ['title' => 'User Profile']) ?>

<h1>User Profile</h1>
<p>Hello, <?=$this->escape($name)?></p>

<?php $this->insert('footer') ?>
```

#### Example of plain PHP templates using inheritance

Using the [Plates][plates] library.

```php
<?php // template.php ?>

<html>
<head>
    <title><?=$title?></title>
</head>
<body>

<main>
    <?=$this->section('content')?>
</main>

</body>
</html>
```

```php
<?php // user_profile.php ?>

<?php $this->layout('template', ['title' => 'User Profile']) ?>

<h1>User Profile</h1>
<p>Hello, <?=$this->escape($name)?></p>
```


[plates]: http://platesphp.com/
[aura]: https://github.com/auraphp/Aura.View



### Compiled Templates

While PHP has evolved into a mature, object oriented language, it [hasn't improved much][article_templating_engines] as
a templating language. Compiled templates, like [Twig], [Brainy], or [Smarty]*, fill this void by offering a new syntax that has
been geared specifically to templating. From automatic escaping, to inheritance and simplified control structures,
compiled templates are designed to be easier to write, cleaner to read and safer to use. Compiled templates can even be
shared across different languages, [Mustache] being a good example of this. Since these templates must be compiled
there is a slight performance hit, however this is very minimal when proper caching is used.

**While Smarty offers automatic escaping, this feature is NOT enabled by default.*

#### Simple example of a compiled template

Using the [Twig] library.

```html+jinja
{% raw %}
{% include 'header.html' with {'title': 'User Profile'} %}

<h1>User Profile</h1>
<p>Hello, {{ name }}</p>

{% include 'footer.html' %}
{% endraw %}
```

#### Example of compiled templates using inheritance

Using the [Twig] library.

```html+jinja
{% raw %}
// template.html

<html>
<head>
    <title>{% block title %}{% endblock %}</title>
</head>
<body>

<main>
    {% block content %}{% endblock %}
</main>

</body>
</html>
{% endraw %}
```

```html+jinja
{% raw %}
// user_profile.html

{% extends "template.html" %}

{% block title %}User Profile{% endblock %}
{% block content %}
    <h1>User Profile</h1>
    <p>Hello, {{ name }}</p>
{% endblock %}
{% endraw %}
```


[article_templating_engines]: http://fabien.potencier.org/article/34/templating-engines-in-php
[Twig]: http://twig.sensiolabs.org/
[Brainy]: https://github.com/box/brainy
[Smarty]: http://www.smarty.net/
[Mustache]: http://mustache.github.io/



### Further Reading

#### Articles & Tutorials

* [Templating Engines in PHP](http://fabien.potencier.org/article/34/templating-engines-in-php)
* [An Introduction to Views & Templating in CodeIgniter](http://code.tutsplus.com/tutorials/an-introduction-to-views-templating-in-codeigniter--net-25648)
* [Getting Started With PHP Templating](http://www.smashingmagazine.com/2011/10/17/getting-started-with-php-templating/)
* [Roll Your Own Templating System in PHP](http://code.tutsplus.com/tutorials/roll-your-own-templating-system-in-php--net-16596)
* [Master Pages](https://laracasts.com/series/laravel-from-scratch/episodes/7)
* [Working With Templates in Symfony 2](http://code.tutsplus.com/tutorials/working-with-templates-in-symfony-2--cms-21172)
* [Writing Safer Templates](https://github.com/box/brainy/wiki/Writing-Safe-Templates)

#### Libraries

* [Aura.View](https://github.com/auraphp/Aura.View) *(native)*
* [Blade](http://laravel.com/docs/blade) *(compiled, framework specific)*
* [Brainy](https://github.com/box/brainy) *(compiled)*
* [Dwoo](http://dwoo.org/) *(compiled)*
* [Latte](https://github.com/nette/latte) *(compiled)*
* [Mustache](https://github.com/bobthecow/mustache.php) *(compiled)*
* [PHPTAL](http://phptal.org/) *(compiled)*
* [Plates](http://platesphp.com/) *(native)*
* [Smarty](http://www.smarty.net/) *(compiled)*
* [Twig](http://twig.sensiolabs.org/) *(compiled)*
* [Zend\View](http://framework.zend.com/manual/2.3/en/modules/zend.view.quick-start.html) *(native, framework specific)*


title:  Errors and Exceptions

## Errors and Exceptions




### Errors

In many "exception-heavy" programming languages, whenever anything goes wrong an exception will be thrown. This is
certainly a viable way to do things, but PHP is an "exception-light" programming language. While it does have
exceptions and more of the core is starting to use them when working with objects, most of PHP itself will try to keep
processing regardless of what happens, unless a fatal error occurs.

For example:

```sh
$ php -a
php > echo $foo;
Notice: Undefined variable: foo in php shell code on line 1
```

This is only a notice error, and PHP will happily carry on. This can be confusing for those coming from
"exception-heavy" languages, because referencing a missing variable in Python for example will throw an exception:

```sh
$ python
>>> print foo
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'foo' is not defined
```

The only real difference is that Python will freak out over any small thing, so that developers can be super sure any
potential issue or edge-case is caught, whereas PHP will keep on processing unless something extreme happens, at which
point it will throw an error and report it.

#### Error Severity

PHP has several levels of error severity. The three most common types of messages are errors, notices and warnings.
These have different levels of severity; `E_ERROR`, `E_NOTICE`, and `E_WARNING`. Errors are fatal run-time errors and
are usually caused by faults in your code and need to be fixed as they'll cause PHP to stop executing. Notices are
advisory messages caused by code that may or may not cause problems during the execution of the script, execution is
not halted. Warnings are non-fatal errors, execution of the script will not be halted.

Another type of error message reported at compile time are `E_STRICT` messages. These messages are used to suggest
changes to your code to help ensure best interoperability and forward compatibility with upcoming versions of PHP.

#### Changing PHP's Error Reporting Behaviour

Error Reporting can be changed by using PHP settings and/or PHP function calls. Using the built in PHP function
`error_reporting()` you can set the level of errors for the duration of the script execution by passing one of the
predefined error level constants, meaning if you only want to see Warnings and Errors - but not Notices - then you can
configure that:

```php
<?php
error_reporting(E_ERROR | E_WARNING);
```

You can also control whether or not errors are displayed to the screen (good for development) or hidden, and logged
(good for production). For more information on this check out the [Error Reporting][errorreport] section.

#### Inline Error Suppression

You can also tell PHP to suppress specific errors with the Error Control Operator `@`. You put this operator at the
beginning of an expression, and any error that's a direct result of the expression is silenced.

```php
<?php
echo @$foo['bar'];
```

This will output `$foo['bar']` if it exists, but will simply return a null and print nothing if the variable `$foo` or
`'bar'` key does not exist. Without the error control operator, this expression could create a `PHP Notice: Undefined
variable: foo` or `PHP Notice: Undefined index: bar` error.

This might seem like a good idea, but there are a few undesirable tradeoffs. PHP handles expressions using an `@` in a
less performant way than expressions without an `@`. Premature optimization may be the root of all programming
arguments, but if performance is particularly important for your application/library it's important to understand the
error control operator's performance implications.

Secondly, the error control operator **completely** swallows the error. The error is not displayed, and the error is
not sent to the error log. Also, stock/production PHP systems have no way to turn off the error control operator. While
you may be correct that the error you're seeing is harmless, a different, less harmless error will be just as silent.

If there's a way to avoid the error suppression operator, you should consider it. For example, our code above could be
rewritten like this:

```php
<?php
echo isset($foo['bar']) ? $foo['bar'] : '';
```

One instance where error suppression might make sense is where `fopen()` fails to find a file to load. You could check
for the existence of the file before you try to load it, but if the file is deleted after the check and before the
`fopen()` (which might sound impossible, but it can happen) then `fopen()` will return false _and_ throw an error. This
is potentially something PHP should resolve, but is one case where error suppression might seem like the only valid
solution.

Earlier we mentioned there's no way in a stock PHP system to turn off the error control operator. However, [Xdebug] has
an `xdebug.scream` ini setting which will disable the error control operator. You can set this via your `php.ini` file
with the following.

{% highlight ini %}
xdebug.scream = On
```

You can also set this value at runtime with the `ini_set` function

```php
<?php
ini_set('xdebug.scream', '1')
```

The "[Scream]" PHP extension offers similar functionality to Xdebug's, although Scream's ini setting is named
`scream.enabled`.

This is most useful when you're debugging code and suspect an informative error is suppressed. Use scream with care,
and as a temporary debugging tool. There's lots of PHP library code that may not work with the error control operator
disabled.


* [Error Control Operators]
* [SitePoint]
* [Xdebug]
* [Scream]


#### ErrorException

PHP is perfectly capable of being an "exception-heavy" programming language, and only requires a few lines of code to
make the switch. Basically you can throw your "errors" as "exceptions" using the `ErrorException` class, which extends
the `Exception` class.

This is a common practice implemented by a large number of modern frameworks such as Symfony and Laravel. By default
Laravel will display all errors as exceptions using the [Whoops!] package if the `app.debug` switch is turned on, then
hide them if the switch is turned off.

By throwing errors as exceptions in development you can handle them better than the usual result, and if you see an
exception during development you can wrap it in a catch statement with specific instructions on how to handle the
situation. Each exception you catch instantly makes your application that little bit more robust.

More information on this and details on how to use `ErrorException` with error handling can be found at
[ErrorException Class][errorexception].

* [Error Control Operators]
* [Predefined Constants for Error Handling]
* [`error_reporting()`][error_reporting]
* [Reporting][errorreport]


[errorreport]: /#error_reporting
[Xdebug]: http://xdebug.org/docs/basic
[Scream]: http://php.net/book.scream
[Error Control Operators]: http://php.net/language.operators.errorcontrol
[SitePoint]: http://www.sitepoint.com/
[Whoops!]: http://filp.github.io/whoops/
[errorexception]: http://php.net/class.errorexception
[Predefined Constants for Error Handling]: http://php.net/errorfunc.constants
[error_reporting]: http://php.net/function.error-reporting



### Exceptions

Exceptions are a standard part of most popular programming languages, but they are often overlooked by PHP programmers.
Languages like Ruby are extremely Exception heavy, so whenever something goes wrong such as a HTTP request failing, or
a DB query goes wrong, or even if an image asset could not be found, Ruby (or the gems being used) will throw an
exception to the screen meaning you instantly know there is a mistake.

PHP itself is fairly lax with this, and a call to `file_get_contents()` will usually just get you a `FALSE` and a
warning.
Many older PHP frameworks like CodeIgniter will just return a false, log a message to their proprietary logs and maybe
let you use a method like `$this->upload->get_error()` to see what went wrong. The problem here is that you have to go
looking for a mistake and check the docs to see what the error method is for this class, instead of having it made
extremely obvious.

Another problem is when classes automatically throw an error to the screen and exit the process. When you do this you
stop another developer from being able to dynamically handle that error. Exceptions should be thrown to make a
developer aware of an error; they then can choose how to handle this. E.g.:

```php
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
finally
{
    // Executed regardless of whether an exception has been thrown, and before normal execution resumes
}
```

#### SPL Exceptions

The generic `Exception` class provides very little debugging context for the developer; however, to remedy this, it is
possible to create a specialized `Exception` type by sub-classing the generic `Exception` class:

```php
<?php
class ValidationException extends Exception {}
```

This means you can add multiple catch blocks and handle different Exceptions differently. This can lead to the
creation of a <em>lot</em> of custom Exceptions, some of which could have been avoided using the SPL Exceptions
provided in the [SPL extension][splext].

If for example you use the `__call()` Magic Method and an invalid method is requested then instead of throwing a
standard Exception which is vague, or creating a custom Exception just for that, you could just
`throw new BadMethodCallException;`.

* [Read about Exceptions][exceptions]
* [Read about SPL Exceptions][splexe]
* [Nesting Exceptions In PHP][nesting-exceptions-in-php]
* [Exception Best Practices in PHP 5.3][exception-best-practices53]


[splext]: /#standard_php_library
[exceptions]: http://php.net/language.exceptions
[splexe]: http://php.net/spl.exceptions
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3



## Security



### Web Application Security

There are bad people ready and willing to exploit your web application. It is important that you take necessary
precautions to harden your web application's security. Luckily, the fine folks at
[The Open Web Application Security Project][1] (OWASP) have compiled a comprehensive list of known security issues and
methods to protect yourself against them. This is a must read for the security-conscious developer. [Survive The Deep End: PHP Security][3] by Padraic Brady is also another good web application security guide for PHP.

* [Read the OWASP Security Guide][2]


[1]: https://www.owasp.org/
[2]: https://www.owasp.org/index.php/Guide_Table_of_Contents
[3]: http://phpsecurity.readthedocs.org/en/latest/index.html



### Password Hashing

Eventually everyone builds a PHP application that relies on user login. Usernames and passwords are stored in a
database and later used to authenticate users upon login.

It is important that you properly [_hash_][3] passwords before storing them. Password hashing is an irreversible, one
way function performed against the user's password. This produces a fixed-length string that cannot be feasibly
reversed. This means you can compare a hash against another to determine if they both came from the same source string,
but you cannot determine the original string. If passwords are not hashed and your database is accessed by an
unauthorized third-party, all user accounts are now compromised. Some users may (unfortunately) use the same password
for other services. Therefore, it is important to take security seriously.

**Hashing passwords with `password_hash`**

In PHP 5.5 `password_hash()` was introduced. At this time it is using BCrypt, the strongest algorithm currently
supported by PHP. It will be updated in the future to support more algorithms as needed though. The `password_compat`
library was created to provide forward compatibility for PHP >= 5.3.7.

Below we hash a string, and then check the hash against a new string. Because our two source strings are different
('secret-password' vs. 'bad-password') this login will fail.

```php
<?php
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    // Correct Password
} else {
    // Wrong password
}
```


* [Learn about `password_hash()`] [1]
* [`password_compat` for PHP >= 5.3.7 && < 5.5] [2]
* [Learn about hashing in regards to cryptography] [3]
* [PHP `password_hash()` RFC] [4]


[1]: http://php.net/function.password-hash
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash



### Data Filtering

Never ever (ever) trust foreign input introduced to your PHP code. Always sanitize and validate foreign input before
using it in code. The `filter_var()` and `filter_input()` functions can sanitize text and validate text formats (e.g.
email addresses).

Foreign input can be anything: `$_GET` and `$_POST` form input data, some values in the `$_SERVER` superglobal, and the
HTTP request body via `fopen('php://input', 'r')`. Remember, foreign input is not limited to form data submitted by the
user. Uploaded and downloaded files, session values, cookie data, and data from third-party web services are foreign
input, too.

While foreign data can be stored, combined, and accessed later, it is still foreign input. Every time you process,
output, concatenate, or include data in your code, ask yourself if the data is filtered properly and can it be trusted.

Data may be _filtered_ differently based on its purpose. For example, when unfiltered foreign input is passed into HTML
page output, it can execute HTML and JavaScript on your site! This is known as Cross-Site Scripting (XSS) and can be a
very dangerous attack. One way to avoid XSS is to sanitize all user-generated data before outputting it to your page by
removing HTML tags with the `strip_tags()` function or escaping characters with special meaning into their respective
HTML entities with the `htmlentities()` or `htmlspecialchars()` functions.

Another example is passing options to be executed on the command line. This can be extremely dangerous (and is usually
a bad idea), but you can use the built-in `escapeshellarg()` function to sanitize the executed command's arguments.

One last example is accepting foreign input to determine a file to load from the filesystem. This can be exploited by
changing the filename to a file path. You need to remove `"/"`, `"../"`, [null bytes][6], or other characters from the
file path so it can't load hidden, non-public, or sensitive files.

* [Learn about data filtering][1]
* [Learn about `filter_var`][4]
* [Learn about `filter_input`][5]
* [Learn about handling null bytes][6]

#### Sanitization

Sanitization removes (or escapes) illegal or unsafe characters from foreign input.

For example, you should sanitize foreign input before including the input in HTML or inserting it into a raw SQL query.
When you use bound parameters with [PDO](#databases), it will sanitize the input for you.

Sometimes it is required to allow some safe HTML tags in the input when including it in the HTML page. This is very
hard to do and many avoid it by using other more restricted formatting like Markdown or BBCode, although whitelisting
libraries like [HTML Purifier][html-purifier] exists for this reason.

[See Sanitization Filters][2]

#### Unserialization

It is dangerous to `unserialize()` data from users or other untrusted sources.  Doing so can allow malicious users to instantiate objects (with user-defined properties) whose destructors will be executed, **even if the objects themselves aren't used**.  You should therefore avoid unserializing untrusted data.

If you absolutely must unserialize data from untrusted sources, use PHP 7's [`allowed_classes`][unserialize] option to restrict which object types are allowed to be unserialized.

#### Validation

Validation ensures that foreign input is what you expect. For example, you may want to validate an email address, a
phone number, or age when processing a registration submission.

[See Validation Filters][3]


[1]: http://php.net/book.filter
[2]: http://php.net/filter.filters.sanitize
[3]: http://php.net/filter.filters.validate
[4]: http://php.net/function.filter-var
[5]: http://php.net/function.filter-input
[6]: http://php.net/security.filesystem.nullbytes
[html-purifier]: http://htmlpurifier.org/
[unserialize]: https://secure.php.net/manual/en/function.unserialize.php



### Configuration Files

When creating configuration files for your applications, best practices recommend that one of the following methods be
followed:

- It is recommended that you store your configuration information where it cannot be accessed directly and pulled in
via the file system.
- If you must store your configuration files in the document root, name the files with a `.php` extension. This ensures
that, even if the script is accessed directly, it will not be output as plain text.
- Information in configuration files should be protected accordingly, either through encryption or group/user file
system permissions



### Register Globals

**NOTE:** As of PHP 5.4.0 the `register_globals` setting has been removed and can no longer be used. This is only
included as a warning for anyone in the process of upgrading a legacy application.

When enabled, the `register_globals` configuration setting that makes several types of variables (including ones from
`$_POST`, `$_GET` and `$_REQUEST`) available in the global scope of your application. This can easily lead to security
issues as your application cannot effectively tell where the data is coming from.

For example: `$_GET['foo']` would be available via `$foo`, which can override variables that have not been declared.
If you are using PHP < 5.4.0 __make sure__ that `register_globals` is __off__.

* [Register_globals in the PHP manual](http://php.net/security.globals)



### Error Reporting

Error logging can be useful in finding the problem spots in your application, but it can also expose information about
the structure of your application to the outside world. To effectively protect your application from issues that could
be caused by the output of these messages, you need to configure your server differently in development versus
production (live).

#### Development

To show every possible error during **development**, configure the following settings in your `php.ini`:

{% highlight ini %}
display_errors = On
display_startup_errors = On
error_reporting = -1
log_errors = On
```

> Passing in the value `-1` will show every possible error, even when new levels and constants are added in future PHP
> versions. The `E_ALL` constant also behaves this way as of PHP 5.4. -
> [php.net](http://php.net/function.error-reporting)

The `E_STRICT` error level constant was introduced in 5.3.0 and is not part of `E_ALL`, however it became part of
`E_ALL` in 5.4.0. What does this mean? In terms of reporting every possible error in version 5.3 it means you must
use either `-1` or `E_ALL | E_STRICT`.

**Reporting every possible error by PHP version**

* &lt; 5.3 `-1` or `E_ALL`
* &nbsp; 5.3 `-1` or `E_ALL | E_STRICT`
* &gt; 5.3 `-1` or `E_ALL`

#### Production

To hide errors on your **production** environment, configure your `php.ini` as:

{% highlight ini %}
display_errors = Off
display_startup_errors = Off
error_reporting = E_ALL
log_errors = On
```

With these settings in production, errors will still be logged to the error logs for the web server, but will not be
shown to the user. For more information on these settings, see the PHP manual:

* [error_reporting](http://php.net/errorfunc.configuration#ini.error-reporting)
* [display_errors](http://php.net/errorfunc.configuration#ini.display-errors)
* [display_startup_errors](http://php.net/errorfunc.configuration#ini.display-startup-errors)
* [log_errors](http://php.net/errorfunc.configuration#ini.log-errors)



## Testing

Writing automated tests for your PHP code is considered a best practice and can lead to well-built applications.
Automated tests are a great tool for making sure your application does not break when you are making changes or adding
new functionality and should not be ignored.

There are several different types of testing tools (or frameworks) available for PHP, which use different approaches -
all of which are trying to avoid manual testing and the need for large Quality Assurance teams, just to make sure
recent changes didn't break existing functionality.



### Test Driven Development

From [Wikipedia](http://en.wikipedia.org/wiki/Test-driven_development):

> Test-driven development (TDD) is a software development process that relies on the repetition of a very short
> development cycle: first the developer writes a failing automated test case that defines a desired improvement or new
> function, then produces code to pass that test and finally refactors the new code to acceptable standards. Kent Beck,
> who is credited with having developed or 'rediscovered' the technique, stated in 2003 that TDD encourages simple
> designs and inspires confidence.

There are several different types of testing that you can do for your application:

#### Unit Testing

Unit Testing is a programming approach to ensure functions, classes and methods are working as expected, from the point
you build them all the way through the development cycle. By checking values going in and out of various functions and
methods, you can make sure the internal logic is working correctly. By using Dependency Injection and building "mock"
classes and stubs you can verify that dependencies are correctly used for even better test coverage.

When you create a class or function you should create a unit test for each behavior it must have. At a very basic level
you should make sure it errors if you send it bad arguments and make sure it works if you send it valid arguments. This
will help ensure that when you make changes to this class or function later on in the development cycle that the old
functionality continues to work as expected. The only alternative to this would be `var_dump()` in a test.php, which is
no way to build an application - large or small.

The other use for unit tests is contributing to open source. If you can write a test that shows broken functionality
(i.e. fails), then fix it, and show the test passing, patches are much more likely to be accepted. If you run a project
which accepts pull requests then you should suggest this as a requirement.

[PHPUnit](http://phpunit.de) is the de-facto testing framework for writing unit tests for PHP applications, but there
are several alternatives

* [atoum](https://github.com/atoum/atoum)
* [Kahlan](https://github.com/crysalead/kahlan)
* [Peridot](http://peridot-php.github.io/)
* [SimpleTest](http://simpletest.org)

#### Integration Testing

From [Wikipedia](http://en.wikipedia.org/wiki/Integration_testing):

> Integration testing (sometimes called Integration and Testing, abbreviated "I&T") is the phase in software testing in
> which individual software modules are combined and tested as a group. It occurs after unit testing and before
> validation testing. Integration testing takes as its input modules that have been unit tested, groups them in larger
> aggregates, applies tests defined in an integration test plan to those aggregates, and delivers as its output the
> integrated system ready for system testing.

Many of the same tools that can be used for unit testing can be used for integration testing as many of the same
principles are used.

#### Functional Testing

Sometimes also known as acceptance testing, functional testing consists of using tools to create automated tests that
actually use your application instead of just verifying that individual units of code are behaving correctly and that
individual units can speak to each other correctly. These tools typically work using real data and simulating actual
users of the application.

##### Functional Testing Tools

* [Selenium](http://seleniumhq.com)
* [Mink](http://mink.behat.org)
* [Codeception](http://codeception.com) is a full-stack testing framework that includes acceptance testing tools
* [Storyplayer](http://datasift.github.io/storyplayer) is a full-stack testing framework that includes support for creating and destroying test environments on demand



### Behavior Driven Development

There are two different types of Behavior-Driven Development (BDD): SpecBDD and StoryBDD. SpecBDD focuses on technical
behavior of code, while StoryBDD focuses on business or feature behaviors or interactions. PHP has frameworks for both
types of BDD.

With StoryBDD, you write human-readable stories that describe the behavior of your application. These stories can then
be run as actual tests against your application. The framework used in PHP applications for StoryBDD is [Behat], which
is inspired by Ruby's [Cucumber] project and implements the Gherkin DSL for describing feature behavior.

With SpecBDD, you write specifications that describe how your actual code should behave. Instead of testing a function
or method, you are describing how that function or method should behave. PHP offers the [PHPSpec] framework for this
purpose. This framework is inspired by the [RSpec project][Rspec] for Ruby.

#### BDD Links

* [Behat], the StoryBDD framework for PHP, inspired by Ruby's [Cucumber] project;
* [PHPSpec], the SpecBDD framework for PHP, inspired by Ruby's [RSpec] project;
* [Codeception] is a full-stack testing framework that uses BDD principles.


[Behat]: http://behat.org/
[Cucumber]: http://cukes.info/
[PHPSpec]: http://www.phpspec.net/
[RSpec]: http://rspec.info/
[Codeception]: http://codeception.com/



### Complementary Testing Tools

Besides individual testing and behavior driven frameworks, there are also a number of generic frameworks and helper
libraries useful for any preferred approach taken.

#### Tool Links

* [Selenium] is a browser automation tool which can be [integrated with PHPUnit]
* [Mockery] is a Mock Object Framework which can be integrated with [PHPUnit] or [PHPSpec]
* [Prophecy] is a highly opinionated yet very powerful and flexible PHP object mocking framework. It's integrated with
[PHPSpec] and can be used with [PHPUnit].


[Selenium]: http://seleniumhq.org/
[integrated with PHPUnit]: https://github.com/giorgiosironi/phpunit-selenium/
[Mockery]: https://github.com/padraic/mockery
[PHPUnit]: http://phpunit.de/
[PHPSpec]: http://www.phpspec.net/
[Prophecy]: https://github.com/phpspec/prophecy



## Servers and Deployment

PHP applications can be deployed and run on production web servers in a number of ways.



### Platform as a Service (PaaS)

PaaS provides the system and network architecture necessary to run PHP applications on the web. This means little to no
configuration for launching PHP applications or PHP frameworks.

Recently PaaS has become a popular method for deploying, hosting, and scaling PHP applications of all sizes. You can
find a list of [PHP PaaS "Platform as a Service" providers](#php_paas_providers) in our [resources section](#resources).



### Virtual or Dedicated Servers

If you are comfortable with systems administration, or are interested in learning it, virtual or dedicated servers give
you complete control of your application's production environment.

#### nginx and PHP-FPM

PHP, via PHP's built-in FastCGI Process Manager (FPM), pairs really nicely with [nginx], which is a lightweight,
high-performance web server. It uses less memory than Apache and can better handle more concurrent requests. This is
especially important on virtual servers that don't have much memory to spare.

* [Read more on nginx][nginx]
* [Read more on PHP-FPM][phpfpm]
* [Read more on setting up nginx and PHP-FPM securely][secure-nginx-phpfpm]

#### Apache and PHP

PHP and Apache have a long history together. Apache is wildly configurable and has many available
[modules][apache-modules] to extend functionality. It is a popular choice for shared servers and an easy setup for PHP
frameworks and open source apps like WordPress. Unfortunately, Apache uses more resources than nginx by default and
cannot handle as many visitors at the same time.

Apache has several possible configurations for running PHP. The most common and easiest to setup is the [prefork MPM]
with mod_php5. While it isn't the most memory efficient, it is the simplest to get working and to use. This is probably
the best choice if you don't want to dig too deeply into the server administration aspects. Note that if you use
mod_php5 you MUST use the prefork MPM.

Alternatively, if you want to squeeze more performance and stability out of Apache then you can take advantage of the
same FPM system as nginx and run the [worker MPM] or [event MPM] with mod_fastcgi or mod_fcgid. This configuration will
be significantly more memory efficient and much faster but it is more work to set up.

* [Read more on Apache][apache]
* [Read more on Multi-Processing Modules][apache-MPM]
* [Read more on mod_fastcgi][mod_fastcgi]
* [Read more on mod_fcgid][mod_fcgid]


[nginx]: http://nginx.org/
[phpfpm]: http://php.net/install.fpm
[secure-nginx-phpfpm]: https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/
[apache-modules]: http://httpd.apache.org/docs/2.4/mod/
[prefork MPM]: http://httpd.apache.org/docs/2.4/mod/prefork.html
[worker MPM]: http://httpd.apache.org/docs/2.4/mod/worker.html
[event MPM]: http://httpd.apache.org/docs/2.4/mod/event.html
[apache]: http://httpd.apache.org/
[apache-MPM]: http://httpd.apache.org/docs/2.4/mod/mpm_common.html
[mod_fastcgi]: http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html
[mod_fcgid]: http://httpd.apache.org/mod_fcgid/



### Shared Servers

PHP has shared servers to thank for its popularity. It is hard to find a host without PHP installed, but be sure it's
the latest version. Shared servers allow you and other developers to deploy websites to a single machine. The upside to
this is that it has become a cheap commodity. The downside is that you never know what kind of a ruckus your
neighboring tenants are going to create; loading down the server or opening up security holes are the main concerns. If
your project's budget can afford to avoid shared servers you should.



### Building and Deploying your Application

If you find yourself doing manual database schema changes or running your tests manually before updating your files
(manually), think twice! With every additional manual task needed to deploy a new version of your app, the chances for
potentially fatal mistakes increase. Whether you're dealing with a simple update, a comprehensive build process or even
a continuous integration strategy, [build automation][buildautomation] is your friend.

Among the tasks you might want to automate are:

* Dependency management
* Compilation, minification of your assets
* Running tests
* Creation of documentation
* Packaging
* Deployment


#### Build Automation Tools

Build tools can be described as a collection of scripts that handle common tasks of software deployment. The build tool
is not a part of your software, it acts on your software from 'outside'.

There are many open source tools available to help you with build automation, some are written in PHP others aren't.
This shouldn't hold you back from using them, if they're better suited for the specific job. Here are a few examples:

[Phing] is the easiest way to get started with automated deployment in the PHP world. With Phing you can control your
packaging, deployment or testing process from within a simple XML build file. Phing (which is based on [Apache Ant])
provides a rich set of tasks usually needed to install or update a web app and can be extended with additional custom
tasks, written in PHP.

[Capistrano] is a system for *intermediate-to-advanced programmers* to execute commands in a structured, repeatable way
on one or more remote machines. It is pre-configured for deploying Ruby on Rails applications, however people are **successfully deploying PHP systems** with it. Successful use of Capistrano depends on a working knowledge of Ruby and
Rake.

Dave Gardner's blog post [PHP Deployment with Capistrano][phpdeploy_capistrano] is a good starting point for PHP
developers interested in Capistrano.

[Chef] is more than a deployment framework, it is a very powerful Ruby based system integration framework that doesn't
just deploy your app but can build your whole server environment or virtual boxes.

[Deployer] is a deployment tool written in PHP, it's simple and functional. Runs tasks in parallel, atomic deployment, keeps consistency between servers. Recipes of common tasks for Symfony, Laravel, Zend Framework and Yii.

##### Chef resources for PHP developers:

* [Three part blog series about deploying a LAMP application with Chef, Vagrant, and EC2][chef_vagrant_and_ec2]
* [Chef Cookbook which installs and configures PHP and the PEAR package management system][Chef_cookbook]
* [Chef video tutorial series][Chef_tutorial]

##### Further reading:

* [Automate your project with Apache Ant][apache_ant_tutorial]

#### Continuous Integration

> Continuous Integration is a software development practice where members of a team integrate their work frequently,
> usually each person integrates at least daily — leading to multiple integrations per day. Many teams find that this
> approach leads to significantly reduced integration problems and allows a team to develop cohesive software more
> rapidly.

*-- Martin Fowler*

There are different ways to implement continuous integration for PHP. Recently [Travis CI] has done a great job of
making continuous integration a reality even for small projects. Travis CI is a hosted continuous integration service
for the open source community. It is integrated with GitHub and offers first class support for many languages including
PHP.

##### Further reading:

* [Continuous Integration with Jenkins][Jenkins]
* [Continuous Integration with PHPCI][PHPCI]
* [Continuous Integration with Teamcity][Teamcity]


[buildautomation]: http://en.wikipedia.org/wiki/Build_automation
[Phing]: http://www.phing.info/
[Apache Ant]: http://ant.apache.org/
[Capistrano]: https://github.com/capistrano/capistrano/wiki
[phpdeploy_capistrano]: http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/
[Chef]: https://www.chef.io/
[chef_vagrant_and_ec2]: http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/
[Chef_cookbook]: https://github.com/chef-cookbooks/php
[Chef_tutorial]: https://www.youtube.com/playlist?list=PL11cZfNdwNyPnZA9D1MbVqldGuOWqbumZ
[apache_ant_tutorial]: http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/
[Travis CI]: https://travis-ci.org/
[Jenkins]: http://jenkins-ci.org/
[PHPCI]: http://www.phptesting.org/
[Teamcity]: http://www.jetbrains.com/teamcity/
[Deployer]: https://github.com/deployphp/deployer



## Virtualization

Running your application on different environments in development and production can lead to strange bugs popping up
when you go live. It's also tricky to keep different development environments up to date with the same version for all
libraries used when working with a team of developers.

If you are developing on Windows and deploying to Linux (or anything non-Windows) or are developing in a team, you
should consider using a virtual machine. This sounds tricky, but besides the widely known virtualization environments
like VMware or VirtualBox, there are additional tools that may help you setting up a virtual environment in a few easy
steps.



### Vagrant

[Vagrant] helps you build your virtual boxes on top of the known virtual environments and will configure these
environments based on a single configuration file. These boxes can be set up manually, or you can use "provisioning"
software such as [Puppet] or [Chef] to do this for you. Provisioning the base box is a great way to ensure that
multiple boxes are set up in an identical fashion and removes the need for you to maintain complicated "set up"
command lists. You can also "destroy" your base box and recreate it without many manual steps, making it easy to create
a "fresh" installation.

Vagrant creates folders for sharing your code between your host and your virtual machine, which means that you can
create and edit your files on your host machine and then run the code inside your virtual machine.

#### A little help

If you need a little help to start using Vagrant there are some services that might be useful:

- [Rove][Rove]: service that allows you to pre-generate typical Vagrant builds, PHP among the options. The provisioning is
made with Chef.
- [Puphpet][Puphpet]: simple GUI to set up virtual machines for PHP development. **Heavily focused in PHP**. Besides local VMs,
it can be used to deploy to cloud services as well. The provisioning is made with Puppet.
- [Protobox][Protobox]: is a layer on top of vagrant and a web GUI to setup virtual machines for web development. A single YAML
document controls everything that is installed on the virtual machine.
- [Phansible][Phansible]: provides an easy to use interface that helps you generate Ansible Playbooks for PHP based projects.


[Vagrant]: http://vagrantup.com/
[Puppet]: http://www.puppetlabs.com/
[Chef]: https://www.chef.io/
[Rove]: http://rove.io/
[Puphpet]: https://puphpet.com/
[Protobox]: http://getprotobox.com/
[Phansible]: http://phansible.com/



### Docker

Beside using Vagrant, another easy way to get a virtual development or production environment up and running is [Docker].
Docker helps you to provide Linux containers for all kind of applications.
There are many helpful docker images which could provide you with other great services without the need to install
these services on your local machine, e.g. MySQL or PostgreSQL and a lot more. Have a look at the [Docker Hub Registry]
[docker-hub] to search a list of available pre-built containers, which you can then run and use in very few steps.

#### Example: Running your PHP Applications in Docker

After you [installed docker][docker-install] on your machine, you can start an Apache with PHP support in one step.
The following command will download a fully functional Apache installation with the latest PHP version and provide the
directory `/path/to/your/php/files` at `http://localhost:8080`:

```sh
docker run -d --name my-php-webserver -p 8080:80 -v /path/to/your/php/files:/var/www/html/ php:apache
```

After running `docker run` your container is initialized and running.
If you would like to stop or start your container again, you can use the provided name attribute and simply run
`docker stop my-php-webserver` and `docker start my-php-webserver` without providing the above mentioned parameters
again.

#### Learn more about Docker

The commands mentioned above only show a quick way to run an Apache web server with PHP support but there are a lot
more things that you can do with Docker. One of the most important things for PHP developers will be linking your
web server to a database instance, for example. How this could be done is well described within the [Docker User Guide]
[docker-doc].

* [Docker Website][Docker]
* [Docker Installation][docker-install]
* [Docker Images at the Docker Hub Registry][docker-hub]
* [Docker User Guide][docker-doc]


[Docker]: http://docker.com/
[docker-hub]: https://hub.docker.com/
[docker-install]: https://docs.docker.com/installation/
[docker-doc]: https://docs.docker.com/userguide/



## Caching

PHP is pretty quick by itself, but bottlenecks can arise when you make remote connections, load files, etc.
Thankfully, there are various tools available to speed up certain parts of your application, or reduce the number of times these various time-consuming tasks need to run.



### Opcode Cache

When a PHP file is executed, under the hood it is first compiled to opcodes and, only then, the opcodes are executed.
If a PHP file is not modified, the opcodes will always be the same. This means that the compilation step is a waste of
CPU resources.

This is where opcode caches come in. They prevent redundant compilation by storing opcodes in memory and reusing it on
successive calls. Setting up an opcode cache takes a matter of minutes, and your application will speed up
significantly. There's really no reason not to use it.

As of PHP 5.5, there is a built-in opcode cache called [OPcache][opcache-book]. It is also available for earlier
versions.

Read more about opcode caches:

* [OPcache][opcache-book] (built-in since PHP 5.5)
* [APC] (PHP 5.4 and earlier)
* [XCache]
* [Zend Optimizer+] (part of Zend Server package)
* [WinCache] (extension for MS Windows Server)
* [list of PHP accelerators on Wikipedia][PHP_accelerators]


[opcache-book]: http://php.net/book.opcache
[APC]: http://php.net/book.apc
[XCache]: http://xcache.lighttpd.net/
[Zend Optimizer+]: http://www.zend.com/en/products/zend_server
[WinCache]: http://www.iis.net/download/wincacheforphp
[PHP_accelerators]: http://en.wikipedia.org/wiki/List_of_PHP_accelerators



### Object Caching

There are times when it can be beneficial to cache individual objects in your code, such as with data that is expensive
to get or database calls where the result is unlikely to change. You can use object caching software to hold these
pieces of data in memory for extremely fast access later on. If you save these items to a data store after you retrieve
them, then pull them directly from the cache for following requests, you can gain a significant improvement in
performance as well as reduce the load on your database servers.

Many of the popular bytecode caching solutions let you cache custom data as well, so there's even more reason to take
advantage of them. APCu, XCache, and WinCache all provide APIs to save data from your PHP code to their memory cache.

The most commonly used memory object caching systems are APCu and memcached. APCu is an excellent choice for object
caching, it includes a simple API for adding your own data to its memory cache and is very easy to setup and use. The
one real limitation of APCu is that it is tied to the server it's installed on. Memcached on the other hand is
installed as a separate service and can be accessed across the network, meaning that you can store objects in a
hyper-fast data store in a central location and many different systems can pull from it.

Note that when running PHP as a (Fast-)CGI application inside your webserver, every PHP process will have its own cache,
i.e. APCu data is not shared between your worker processes. In these cases, you might want to consider using memcached
instead, as it's not tied to the PHP processes.

In a networked configuration APCu will usually outperform memcached in terms of access speed, but memcached will be
able to scale up faster and further. If you do not expect to have multiple servers running your application, or do not
need the extra features that memcached offers then APCu is probably your best choice for object caching.

Example logic using APCu:

```php
<?php
// check if there is data saved as 'expensive_data' in cache
$data = apc_fetch('expensive_data');
if ($data === false) {
    // data is not in cache; save result of expensive call for later use
    apc_add('expensive_data', $data = get_expensive_data());
}

print_r($data);
```

Note that prior to PHP 5.5, APC provides both an object cache and a bytecode cache. APCu is a project to bring APC's
object cache to PHP 5.5+, since PHP now has a built-in bytecode cache (OPcache).

#### Learn more about popular object caching systems:

* [APCu](https://github.com/krakjoe/apcu)
* [APC Functions](http://php.net/ref.apc)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache APIs](http://xcache.lighttpd.net/wiki/XcacheApi)
* [WinCache Functions](http://php.net/ref.wincache)


title:  Documenting your Code

## Documenting your Code



### PHPDoc

PHPDoc is an informal standard for commenting PHP code. There are a *lot* of different [tags] available. The full list
of tags and examples can be found at the [PHPDoc manual].

Below is an example of how you might document a class with a few methods;

```php
<?php
/**
 * @author A Name <a.name@example.com>
 * @link http://www.phpdoc.org/docs/latest/index.html
 */
class DateTimeHelper
{
    /**
     * @param mixed $anything Anything that we can convert to a \DateTime object
     *
     * @throws \InvalidArgumentException
     *
     * @return \DateTime
     */
    public function dateTimeFromAnything($anything)
    {
        $type = gettype($anything);

        switch ($type) {
            // Some code that tries to return a \DateTime object
        }

        throw new \InvalidArgumentException(
            "Failed Converting param of type '{$type}' to DateTime object"
        );
    }

    /**
     * @param mixed $date Anything that we can convert to a \DateTime object
     *
     * @return void
     */
    public function printISO8601Date($date)
    {
        echo $this->dateTimeFromAnything($date)->format('c');
    }

    /**
     * @param mixed $date Anything that we can convert to a \DateTime object
     */
    public function printRFC2822Date($date)
    {
        echo $this->dateTimeFromAnything($date)->format('r');
    }
}
```

The documentation for the class as a whole has the [@author] tag and a [@link] tag. The [@author] tag is used to
document the author of the code and can be repeated for documenting several authors. The [@link] tag is used to link to a website indicating a relationship between the website and the code.

Inside the class, the first method has a [@param] tag documenting the type, name and description of the parameter
being passed to the method. Additionally it has the [@return] and [@throws] tags for documenting the return type, and any exceptions that could be thrown respectively.

The second and third methods are very similar and have a single [@param] tag as did the first method. The important
difference between the second and third methods' doc block is the inclusion/exclusion of the [@return] tag.
`@return void` explicitly informs us that there is no return; historically omitting the `@return void` statement also results in the same (no return) action.


[tags]: http://www.phpdoc.org/docs/latest/references/phpdoc/tags/index.html
[PHPDoc manual]: http://www.phpdoc.org/docs/latest/index.html
[@author]: http://www.phpdoc.org/docs/latest/references/phpdoc/tags/author.html
[@link]: http://www.phpdoc.org/docs/latest/references/phpdoc/tags/link.html
[@param]: http://www.phpdoc.org/docs/latest/references/phpdoc/tags/param.html
[@return]: http://www.phpdoc.org/docs/latest/references/phpdoc/tags/return.html
[@throws]: http://www.phpdoc.org/docs/latest/references/phpdoc/tags/throws.html



## Resources



### From the Source

* [PHP Website](http://php.net/)
* [PHP Documentation](http://php.net/docs.php)



### People to Follow

It's difficult to find interesting and knowledgable PHP
community members when you are first starting out. You can
find a comprehensive list of PHP community members and their
Twitter handles at:

<http://followphpdevs.com/>



### Mentoring

* [phpmentoring.org](http://phpmentoring.org/) - Formal, peer to peer mentoring in the PHP community.



### PHP PaaS Providers

* [PagodaBox](https://pagodabox.com/)
* [AppFog](https://www.ctl.io/appfog/)
* [Heroku](https://devcenter.heroku.com/categories/php)
* [fortrabbit](http://fortrabbit.com/)
* [Engine Yard Cloud](https://www.engineyard.com/products/cloud)
* [Red Hat OpenShift Platform](http://openshift.com)
* [dotCloud](https://www.dotcloud.com/dev-center/platform-documentation)
* [AWS Elastic Beanstalk](http://aws.amazon.com/elasticbeanstalk/)
* [cloudControl](https://www.cloudcontrol.com/)
* [Windows Azure](http://www.windowsazure.com/)
* [Google App Engine](https://developers.google.com/appengine/docs/php/gettingstarted/)
* [Jelastic](http://jelastic.com/)



### Frameworks

Rather than re-invent the wheel, many PHP developers use frameworks to build out web applications. Frameworks abstract
away many of the low-level concerns and provide helpful, easy-to-use interfaces to complete common tasks.

You do not need to use a framework for every project. Sometimes plain PHP is the right way to go, but if you do need a
framework then there are three main types available:

* Micro Frameworks
* Full-Stack Frameworks
* Component Frameworks

Micro-frameworks are essentially a wrapper to route a HTTP request to a callback, controller, method, etc as quickly as
possible, and sometimes come with a few extra libraries to assist development such as basic database wrappers and the
like. They are prominently used to build remote HTTP services.

Many frameworks add a considerable number of features on top of what is available in a micro-framework and these are
known Full-Stack Frameworks. These often come bundled with ORMs, Authentication packages, etc.

Component-based frameworks are collections of specialized and single-purpose libraries. Disparate component-based
frameworks can be used together to make a micro- or full-stack framework.

* [Popular PHP Frameworks](https://github.com/codeguy/php-the-right-way/wiki/Frameworks)



### Components

As mentioned above "Components" are another approach to the common goal of creating, distributing and implementing
shared code. Various component repositories exist, the main two of which are:

* [Packagist]
* [PEAR]

Both of these repositories have command line tools associated with them to help the installation and upgrade processes,
and have been explained in more detail in the [Dependency Management] section.

There are also component-based frameworks and component-vendors that offer no framework at all. These projects provide
another source of packages which ideally have little to no dependencies on other packages, or specific frameworks.

For example, you can use the [FuelPHP Validation package], without needing to use the FuelPHP framework itself.

* [Aura]
* [FuelPHP]
* [Hoa Project]
* [Orno]
* [Symfony Components]
* [The League of Extraordinary Packages]
* Laravel's Illuminate Components
    * [IoC Container]
    * [Eloquent ORM]
    * [Queue]

_Laravel's [Illuminate components] will become better decoupled from the Laravel framework. For now, only the
components best decoupled from the Laravel framework are listed above._


[Packagist]: /#composer_and_packagist
[PEAR]: /#pear
[Dependency Management]: /#dependency_management
[FuelPHP Validation package]: https://github.com/fuelphp/validation
[Aura]: http://auraphp.com/framework/2.x/en/
[FuelPHP]: https://github.com/fuelphp
[Hoa Project]: https://github.com/hoaproject
[Orno]: https://github.com/orno
[Symfony Components]: http://symfony.com/doc/current/components/index.html
[The League of Extraordinary Packages]: http://thephpleague.com/
[IoC Container]: https://github.com/illuminate/container
[Eloquent ORM]: https://github.com/illuminate/database
[Queue]: https://github.com/illuminate/queue
[Illuminate components]: https://github.com/illuminate


### Other Useful Resources

#### Cheatsheets

* [PHP Cheatsheets](http://phpcheatsheets.com/) - for variable comparisons, arithmetics and variable testing in various
PHP versions
* [PHP Security Cheatsheet](https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet)

#### More best practices

* [PHP Best Practices](https://phpbestpractices.org/)
* [Best practices for Modern PHP Development](https://www.airpair.com/php/posts/best-practices-for-modern-php-development)

#### PHP universe

* [PHP Developer blog](http://blog.phpdeveloper.org/)



### Video Tutorials

#### Youtube Channels
* [PHP Academy](https://www.youtube.com/user/phpacademy)
* [The New Boston](https://www.youtube.com/user/thenewboston)
* [Sherif Ramadan](https://www.youtube.com/user/businessgeek)
* [Level Up Tuts](https://www.youtube.com/user/LevelUpTuts)

#### Paid Videos

* [Standards and Best practices](http://teamtreehouse.com/library/standards-and-best-practices)
* [PHP Training on Pluralsight](http://www.pluralsight.com/search/?searchTerm=php)
* [PHP Training on Lynda.com](http://www.lynda.com/search?q=php)
* [PHP Training on Tutsplus](http://code.tutsplus.com/categories/php/courses)
* [Laracasts](https://laracasts.com/)



### Books

There are a lot of books around for PHP but some are sadly now quite old and no longer contain accurate information.
There are even books published for "PHP 6" which does not exist, and will not now ever exist. The next major version of
PHP will be named "PHP 7" because of those books.

This section aims to be a living document for recommended books on PHP development in general. If you would like your
book to be added, send a PR and it will be reviewed for relevancy.

#### Free Books

* [PHP Pandas](http://daylerees.com/php-pandas/) - Aims to teach everyone how to be a web developer.
* [PHP The Right Way](https://leanpub.com/phptherightway/) - This website is available as a book completely for free.
* [Using Libsodium in PHP Projects](https://paragonie.com/book/pecl-libsodium) - Guide to using Libsodium PHP extension
for modern, secure, and fast cryptography.

#### Paid Books

* [Build APIs You Won't Hate](https://leanpub.com/build-apis-you-wont-hate) - Everyone and their dog wants an API,
so you should probably learn how to build them.
* [Building Secure PHP Apps](https://leanpub.com/buildingsecurephpapps) - Learn the security basics that a senior
developer usually acquires over years of experience, all condensed down into one quick and easy handbook
* [Modernizing Legacy Applications In PHP](https://leanpub.com/mlaphp) - Get your code under control in a series of
small, specific steps
* [Securing PHP: Core Concepts](https://leanpub.com/securingphp-coreconcepts) - A guide to some of the most common
security terms and provides some examples of them in every day PHP
* [Scaling PHP]( https://leanpub.com/scalingphp) - Stop playing sysadmin and get back to coding
* [Signaling PHP]( https://leanpub.com/signalingphp) - PCNLT signals are a great help when writing PHP scripts that
run from the command line.
* [The Grumpy Programmer's Guide To Building Testable PHP Applications](https://leanpub.com/grumpy-testing) - Learning
to write testable code doesn't have to suck



## Community

The PHP community is as diverse as it is large, and its members are ready and willing to support new PHP programmers.
Consider joining your local PHP user group (PUG) or attending larger PHP conferences to learn more about the best
practices shown here. You can hang out on IRC in the #phpc channel on [irc.freenode.com][php-irc] and follow the
[@phpc][phpc-twitter] twitter account. Get out there, meet new developers, learn new topics, and above all, make new
friends! Other community resources include the Google+ PHP [Programmer community][php-programmers-gplus] and
[StackOverflow][php-so].

[Read the Official PHP Events Calendar][php-calendar]


[php-irc]: http://webchat.freenode.net/?channels=phpc
[phpc-twitter]: https://twitter.com/phpc
[php-programmers-gplus]: https://plus.google.com/u/0/communities/104245651975268426012
[php-so]: http://stackoverflow.com/questions/tagged/php
[php-calendar]: http://php.net/cal.php



### PHP User Groups

If you live in a larger city, odds are there's a PHP user group nearby. You can easily find your local PUG at
the [usergroup-list at php.net][php-uglist] which is based upon [PHP.ug][php-ug]. Alternate sources might be
[Meetup.com][meetup] or a search for ```php user group near me``` using your favourite search engine
(i.e. [Google][google]). If you live in a smaller town, there may not be a local PUG; if that's the case, start one!

Special mention should be made of two global user groups: [NomadPHP] and [PHPWomen]. [NomadPHP] offers twice monthly
online user group meetings with presentations by some of the top speakers in the PHP community.
[PHPWomen] is a non-exclusive user group originally targeted towards the women in the PHP world. Membership is open to
everyone who supports a more diverse community. PHPWomen provide a network for support, mentorship and education, and
generally promote the creating of a "female friendly" and professional atmosphere.

[Read about User Groups on the PHP Wiki][php-wiki]

[google]: https://www.google.com/search?q=php+user+group+near+me
[meetup]: http://www.meetup.com/find/
[php-ug]: http://php.ug/
[NomadPHP]: https://nomadphp.com/
[PHPWomen]: http://phpwomen.org/
[php-wiki]: https://wiki.php.net/usergroups
[php-uglist]: http://php.net/ug.php



### PHP Conferences

The PHP community also hosts larger regional and national conferences in many countries around the world. Well-known
members of the PHP community usually speak at these larger events, so it's a great opportunity to learn directly from
industry leaders.

[Find a PHP Conference][php-conf]


[php-conf]: http://php.net/conferences/index.php


### ElePHPants

[ElePHPant][elephpant] is that beautiful mascot of the PHP project with elephant in their design. It was originally designed for the PHP project in 1998 by [Vincent Pontier][vincent-pontier] - spiritual father of thousands of elePHPants around the world and 10 years later adorable plush elephant toy came to birth as well. Now elePHPants are present at many PHP conferences and with many PHP developers at their computers for fun and inspiration.

[Interview with Vincent Pontier][vincent-pontier-interview]


[elephpant]: http://php.net/elephpant.php
[vincent-pontier-interview]: http://7php.com/elephpant/
[vincent-pontier]: http://www.elroubio.net/
