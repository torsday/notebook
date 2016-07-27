# Regex

---

## Examples

### PHP

```php
<?php

$value = 'SELECT 1 as dwnumericid, 1 as shardid';

$lowerCaseQuery = strtolower($value);

$pattern = '/^(?=.*dwnumericid)(?=.*shardid)/';

$results = preg_match($pattern, $value);

if ($results) {
	var_dump('yep!');
	var_dump($results);
} else {
	var_dump('nope :(');
	var_dump($results);
}
```
