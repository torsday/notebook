# Building a command-line app in PHP

Create `composer.json`

```json
{
  "require": {
    "symfony/console": "~3.0"
  }
}
```

run `composer install`

Create php script

```php
#! /usr/bin/env php

<?php

use Symfony\Component\Console\Application;
use Symfony\Component\Console\Input\InputInterface;
use Symfony\Component\Console\Output\OutputInterface;

require 'vendor/autoload.php';

$app = new Application();

$app->register('sayHelloTo')
    ->addArgument('name')
    ->setCode(function(InputInterface $input, OutputInterface $output)
    {
      $output->writeln('Hello World');
    });

$app->run();
```

Change mode of script to executable

```sh
chmod +x my_script.php
```

Execute script

```sh
./my_script.php
```

---

## References

-   [Laracasts: How to Build Command-Line Apps](https://laracasts.com/series/how-to-build-command-line-apps-in-php/episodes/2)
