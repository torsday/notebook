# Autoloader

```php
<?php

/**
 * Class Autoloader for the classes found in `/cpt-integration`.
 */
class CptIntegrationAutoloader
{
    /**
     * @param string $class
     */
    public function loadClass($class)
    {
        $root = __DIR__;
        $ds   = '/';
        $ns   = '\\';

        $filename = $root . $ds . str_replace($ns, $ds, $class) . '.php';

        if (!file_exists($filename)) {
            return false;
        }

            require $filename;
    }

    /**
     * Register the Autoloader.
     */
    public function register() {
        spl_autoload_register(array($this, 'loadClass'));
    }
}
```
