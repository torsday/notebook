# Rails

*From: [Wikipedia](https://en.wikipedia.org/wiki/Ruby_on_Rails)*

> Ruby on Rails, or simply Rails, is a web application framework written in Ruby under the MIT License. Rails is a model–view–controller (MVC) framework, providing default structures for a database, a web service, and web pages.

---

## Setup

using ```postgres``` instead of ```sqlite``` without tests

```bash
rails new <app_name> -d postgresql -T

# -d sets the type of database
# -T prevents default test install
```

create database

```bash
rake db:create
```

add rspec

```bash
rails generate rspec:install
```

---

## Notable Gems

-   [activerecord]()
-   [activesupport]()
-   [bcrypt-ruby]()
-   [better_errors](https://github.com/charliesome/better_errors)
-   [devise](https://github.com/plataformatec/devise)
-   [haml]()
-   [pg]()
-   [rspec-rails]()
-   [sextant](https://github.com/schneems/sextant)
-   [xray-rails](https://github.com/brentd/xray-rails)
