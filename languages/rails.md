# Rails

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
