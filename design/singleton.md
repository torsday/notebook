# Singleton

-   Object Creational Pattern

## GoF definition (p. 127):

> "Ensure a class only has one instance, and provide a global point of access to it."

Sometimes a design calls for only one instance of a class. Rather than pollute the namespace with a globally scoped instance, use the singleton pattern to enforce single instance requirement.

---

## Examples

### Ruby

```ruby
require 'singleton'

class Logger
  include Singleton # ruby includes a library for this pattern
  attr_reader :logs

  def initialize
    @logs = {}
  end

  def log(message)
    @logs[Time.now] = message
  end
end
```

#### Implimentation

```ruby
my_logger = Logger.new # throws error

my_logger = Logger.instance # This returns the single instance

my_logger.log("Hello, world")
p my_logger.logs
```

# PHP

```php
<?php
class Singleton
{
    /**
     * @var Singleton The reference to *Singleton* instance of this class
     */
    private static $instance;

    /**
     * Returns the *Singleton* instance of this class.
     *
     * @return Singleton The *Singleton* instance.
     */
    public static function getInstance()
    {
        if (null === static::$instance) {
            static::$instance = new static();
        }

        return static::$instance;
    }

    /**
     * Protected constructor to prevent creating a new instance of the
     * *Singleton* via the `new` operator from outside of this class.
     */
    protected function __construct()
    {
    }

    /**
     * Private clone method to prevent cloning of the instance of the
     * *Singleton* instance.
     *
     * @return void
     */
    private function __clone()
    {
    }

    /**
     * Private unserialize method to prevent unserializing of the *Singleton*
     * instance.
     *
     * @return void
     */
    private function __wakeup()
    {
    }
}

class SingletonChild extends Singleton
{
}

$obj = Singleton::getInstance();
var_dump($obj === Singleton::getInstance());             // bool(true)

$anotherObj = SingletonChild::getInstance();
var_dump($anotherObj === Singleton::getInstance());      // bool(false)

var_dump($anotherObj === SingletonChild::getInstance()); // bool(true)
```

> The code above implements the singleton pattern using a static variable and the static creation method getInstance(). Note the following:

> The constructor __construct() is declared as protected to prevent creating a new instance outside of the class via the new operator.
The magic method __clone() is declared as private to prevent cloning of an instance of the class via the clone operator.
The magic method __wakeup() is declared as private to prevent unserializing of an instance of the class via the global function unserialize() .
A new instance is created via late static binding in the static creation method getInstance() with the keyword static. This allows the subclassing of the class Singleton in the example.
The singleton pattern is useful when we need to make sure we only have a single instance of a class for the entire request lifecycle in a web application. This typically occurs when we have global objects (such as a Configuration class) or a shared resource (such as an event queue).

> You should be wary when using the singleton pattern, as by its very nature it introduces global state into your application, reducing testability. In most cases, dependency injection can (and should) be used in place of a singleton class. Using dependency injection means that we do not introduce unnecessary coupling into the design of our application, as the object using the shared or global resource requires no knowledge of a concretely defined class.

---

## References

-   [PHP the Right Way: Design-Patterns](http://www.phptherightway.com/pages/Design-Patterns.html)
