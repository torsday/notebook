# Arrays in PHP

```php
$myArray = array(1, 2, 3, 4, 5);

unset($myArray[0]) => [ 2, 3, 4, 5]

array_push($myArray, 6);

count($myArray);

sort($myArray);

join(", ", $myArray);
```

---

## CRUD

### Push

```php
$myArray[] = $var;
```

```php
array_push($stack, "apple", "raspberry");
```

<http://php.net/manual/en/function.array-push.php>

---

## Associative Arrays

```php
$associative = array('key' => 'value');
```

In PHP, associative arrays are implemented as hash tables, with a bit of extra functionality.

However technically speaking, an associative array is not identical to a hashtable - it's simply _implemented_ in part with a hashtable behind-the-scenes. Because most of its implementation is a hashtable, it can do everything a hashtable can - but it can do more, too.

For example, you can loop through an associative array using a for loop, which you can't do with a hashtable.

So while they're similar, an associative array can actually do a **superset** of what a hashtable can do - so they're not exactly the same thing. Think of it as hashtables plus extra functionality.

Code examples:

**Using an associative array as a hashtable**:

```php
$favoriteColor = array();
$favoriteColor['bob']='blue';
$favoriteColor['Peter']='red';
$favoriteColor['Sally']='pink';
echo 'bob likes: '.$favoriteColor['bob']."\n";
echo 'Sally likes: '.$favoriteColor['Sally']."\n";
//output: bob likes blue
//        Sally likes pink
```

**Looping through an associative array**:

```php
$idTable=array();
$idTable['Tyler']=1;
$idTable['Bill']=20;
$idTable['Marc']=4;
//up until here, we're using the array as a hashtable.

//now we loop through the array - you can't do this with a hashtable:
foreach($idTable as $person=>$id)
    echo 'id: '.$id.' | person: '.$person."\n";

//output: id: 1 | person: Tyler
//        id: 20 | person: Bill
//        id: 4 | person: Marc
```

Note especially how in the second example, the order of each element is maintained (Tyler, Bill Marc) based on the order in which they were entered into the array. This is a major difference between associative arrays and hashtables. A hashtable maintains no connection between the items it holds, whereas a PHP associative array does (you can even sort a PHP associative array).

---

## References

-   [StackOverflow: Hash tables VS associative arrays](http://stackoverflow.com/questions/3134296/hash-tables-vs-associative-arrays)
