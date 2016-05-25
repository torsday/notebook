# Composer

An application-level package manager for the PHP programming language that provides a standard format for managing dependencies of PHP software and required libraries.

```sh
composer install

composer update cpt/rch-php

composer require "cpt/rch-php=0.73.*"
```

---

Creating a composer package is as simple as creating a file named `composer.json` with the basic outline:

```json
{
  "name": "touchlab/burger-queen-php",
  "description": "A Touch Lab abstraction of Google's Big Query API Client Library.",
  "type": "library",
  "license": "proprietary",
  "require-dev": {
    "phpunit/phpunit": "~4.8",
    "php": ">=5.5.0",
    "phpmd/phpmd": "~2.2",
    "phing/phing": "~2.11",
    "fabpot/php-cs-fixer": "1.*"
  },
  "autoload-dev": {
    "psr-4": {
      "TouchLab\\": "tests/TouchLab"
    }
  },
  "autoload": {
    "psr-4": {
      "TouchLab\\": "src/TouchLab"
    }
  },
  "authors": [
    {
      "name": "The PB SCRUM Team",
      "email": "pb@touchlab.com"
    }
  ]
}
