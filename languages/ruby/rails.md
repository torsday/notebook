# Rails

*From: [Wikipedia](https://en.wikipedia.org/wiki/Ruby_on_Rails)*

> Ruby on Rails, or simply Rails, is a web application framework written in Ruby under the MIT License. Rails is a model–view–controller (MVC) framework, providing default structures for a database, a web service, and web pages.

---

## Setup

### Full App

```bash
rails new <app_name> -d postgresql -T

# -d sets the type of database. sqlite by default
# -T prevents default test install
```

### API App

```sh
rails new <app_name) --api
```

### database

```bash
rake db:create
rake db:migrate
rake -T
```

### Install `rspec`

Update `Gemfile`

```rb
group :development, :test do
  gem 'rspec-rails'
end
```

Generate

```sh
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
