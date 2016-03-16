# PHP Snippets

---

## Parse a csv file in PHP (from [php.net](http://php.net/manual/en/function.str-getcsv.php))

```php
$csv = array_map('str_getcsv', file('data.csv'));
```

---

## Grabbing command line arguments from a PHP script

-   `getopt` *([php.net](http://php.net/manual/en/function.getopt.php))*

```php
$shortopts  = "";
$shortopts .= "f:";  // Required value
$shortopts .= "v::"; // Optional value
$shortopts .= "abc"; // These options do not accept values

$longopts  = array(
    "required:",     // Required value
    "optional::",    // Optional value
    "option",        // No value
    "opt",           // No value
);
$options = getopt($shortopts, $longopts);
```

```sh
php example.php -f "value for f" -v -a --required value --optional="optional value" --option
```

```php
array(6) {
  ["f"]=>
  string(11) "value for f"
  ["v"]=>
  bool(false)
  ["a"]=>
  bool(false)
  ["required"]=>
  string(5) "value"
  ["optional"]=>
  string(14) "optional value"
  ["option"]=>
  bool(false)
}
```
