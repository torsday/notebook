# `exec()`

```php
string exec ( string $command [, array &$output [, int &$return_var ]] )
```

```php
$deactivationScript = $root . "my_script.php";
$scriptOptions      = "-l lorem -o ipsum -dolor sunt";
$cmd                = "php $deactivationScript $scriptOptions";
exec($cmd, $output, $return);
```

## Parameters

### `command`

The command that will be executed.

### `output`

If the output argument is present, then the specified array will be filled with every line of output from the command. Trailing whitespace, such as \n, is not included in this array. Note that if the array already contains some elements, `exec()` will append to the end of the array. If you do not want the function to append elements, call `unset()` on the array before passing it to `exec()`.

### `return_var`

If the `return_var` argument is present along with the output argument, then the return status of the executed command will be written to this variable.

## Return Values

The last line from the result of the command. If you need to execute a command and have all the data from the command passed directly back without any interference, use the `passthru()` function.

To get the output of the executed command, be sure to set and use the output parameter.

---

## References

-   [PHP.net: `exec()`](http://php.net/manual/en/function.exec.php)
