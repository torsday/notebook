# php-cs-fixer

## [installation](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

### the composer way

```
$ composer global require fabpot/php-cs-fixer
```

### the homebrew way

```
$ brew install homebrew/php/php-cs-fixer
```

## Setup

### shell script

#### ```psr-fixer.sh```

```bash
php-cs-fixer fix $1 --verbose --level=psr2 --fixers=align_equals,align_double_arrow,whitespacy_lines,short_array_syntax,double_arrow_multiline_whitespaces,duplicate_semicolon,extra_empty_lines,multiline_array_trailing_comma,new_with_braces,phpdoc_params,remove_leading_slash_use,remove_lines_between_uses,return,single_array_no_trailing_comma,unused_use,concat_with_spaces
```

same thing, with line breaks

```bash
php-cs-fixer fix $1 --verbose --level=psr2 --fixers=\
align_equals,\
align_double_arrow,\
whitespacy_lines,\
short_array_syntax,\
double_arrow_multiline_whitespaces,\
duplicate_semicolon,\
extra_empty_lines,\
multiline_array_trailing_comma,\
new_with_braces,\
phpdoc_params,\
remove_leading_slash_use,\
remove_lines_between_uses,\
return,\
single_array_no_trailing_comma,\
unused_use,\
concat_with_spaces
```

### permissions

```bash
$ chmod -x psr-fixer.sh
```

make sure it's in your path

### alias

```bash
psr='~/scripts/psr-fixer.sh'
```

or wherever you store it.

### usage

```
$ psr {dir/file}
```

## atom integration

You can also implement it directly in Atom. [Here's the plugin](https://atom.io/packages/php-cs-fixer), ask me if you have any questions on setting it up.
