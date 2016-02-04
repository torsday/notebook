# Ruby

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [String Methods](#string-methods)
- [Number Methods](#number-methods)
- [Misc](#misc)
- [Comparison Operators](#comparison-operators)
- [Boolean Operators](#boolean-operators)
- [Operators](#operators)
- [Combined Comparison Operator](#combined-comparison-operator)
- [Arrays](#arrays)
- [Loops](#loops)
- [One Line Ifs & Ternary Conditional Expressions & Case Statements](#one-line-ifs-ternary-conditional-expressions-case-statements)
- [Methods that Take Blocks](#methods-that-take-blocks)
	- [Yield](#yield)
- [Times Iterator](#times-iterator)
- [Loop Iterator](#loop-iterator)
- [Each Iterator](#each-iterator)
- [Map](#map)
- [Select](#select)
- [```.upto```, ```.downto```](#upto-downto)
- [Hashes](#hashes)
	- [```.new``` notation](#new-notation)
	- [Some Hash Methods](#some-hash-methods)
- [Methods](#methods)
- [Splat Arguments](#splat-arguments)
- [Procs](#procs)
- [Lamdas](#lamdas)
- [Scope Prefixes](#scope-prefixes)
- [Classes](#classes)
- [Modules](#modules)

<!-- /TOC -->

## String Methods

```ruby
.length
.reverse
.upcase
.downcase
.capitalize  # capitalizes the first letter
.include? "x"   # tests if string contains "x"
.match   # works like .include?
.start_with?("x")
.end_with?("x")

“a”.next  => “b”

"#{}"  string interpolation - "My name is #{name}"
```

Returns a copy of str with the all occurrences of pattern substituted.
Pattern is typically a regex.

```ruby
.gsub(pattern, replacement)
```

Iterates through the string, returns an array of all results matching the pattern

```ruby
.scan(pattern)

.insert(index, “something”)
```


## Number Methods

```ruby
.abs      absolute value
.ceil     rounds float up
.floor    rounds float down
.eql?(n)  is the object equal to n?
```


## Misc

```ruby
gets   raw input from user (get string)
gets.chomp  raw input from user w/o extra line
.is_a? Integer  tests whether == given data type

rand   generates random float between 0 and 1
rand(n)   generates random integer between 0 and n, exclusive

.sort   sorts numerically or alphabetically. For a reverse sort, include    the following block as a parameter: array.sort! { |first, second| second <=> first }  # or  array.sort.reverse!

.to_s   converts a variable to a string
.to_i   converts to integer
.to_f   converts to float
.to_sym #or .intern converts a string to a symbol

object.replace(object.method) replaces object with the output of method (liked .method!)
```


## Comparison Operators

```ruby
>
<
>=
==
!=
```


## Boolean Operators

```ruby
&&
||   or
!   not
```


## Operators

```ruby
+=
-=
*=
/=

||=   conditional assignment operator - only assigns a value to a     variable if the current value of the variable is nil.
```


## Combined Comparison Operator

```
<=>
```

Returns 0 if the first operand (item to be compared) equals the second, 1 if first operand is greater than the second, and -1 if the first operand is less than the second.


## Arrays

```ruby
array = [1, 2, 3]
array[0]   fetch item at given index
array[0][0]  fetch item at given index (2D array or beyond)
array[0] = 1  set item at given index
array << 23  add item to end of array ("concatenation operation")

array.push(element) << is a shortcut for this
array.pop(element)

array.unshift(element) like push but it adds to beginning of array
array.shift(element)  like pop but it removes from beginning of array

array.first  returns first element
array.length  returns # of elements
array.empty?
array.include?(x)
array.index(x) What index is the given element at?

array.join(x)  returns elements as string separated by x
string.split(x)  turns a string into an array with x as separator
```



## Loops

while
until   opposite of while (stops when false)
for x in 1...10  Up to 10, exclusive (9 times), e.g.: for num in 1...10   puts num  end

for x in 1..10  Up to 10, inclusive (10 times)



## One Line Ifs & Ternary Conditional Expressions & Case Statements

```ruby
puts "It's true" if true

puts 0 < 1 ? "0 is less than one" : "0 is greater than 1"

case which_is_greater
when x > y then puts "x is greater."
when x < y then  puts "y is greater."
when x == y then puts "x and y are equal."
else puts "I am confused."
end
```

Or

```ruby
case which_is_greater
when x > y
    puts "x is greater."
when x < y
    puts "y is greater."
when x == y
    puts "x and y are equal."
else
    puts "I am confused."
end
```


## Methods that Take Blocks


### Yield

You can make your own methods that take blocks with yield.

```ruby
def method(n)
  yield n   Passes "n" to the block. yield can also be standalone.
end

def double(num)
    yield num
end

double(3) { |x| x*2 }
```



## Times Iterator

Technically a method using the block ({}) as an argument.

```ruby
30.times {
  print "Ruby!"
}
```

You can keep track of the index if you like.

```ruby
30.times { |index|
  print index
}
```

## Loop Iterator

```ruby
n = 1

loop {
    n += 1
    print "Ruby!"
    break if n > 30
}
```

## Each Iterator

Technically a method that uses the block ({}) as an argument.

```ruby
array = [1, 2, 3]

array.each { |x|
    puts x
}

hash.each { |key, value| puts "#{key} is #{value}"}
hash.each_key { |key| #do something}
hash.each_value { |value| #do something}
```

## Map

A lot like .each, except .map returns an array composed of the block results while each returns the original array. .map is a good choice if you actually want to change the elements in your array: array = array.map(some_block)

```ruby
doubled_array = array.map { |num| num*2 }

array.map(&:to_s)  #Converts all elements to a string. .to_s is passed like a block.
array.map(&:reverse)
```

## Select

Returns values that matches the conditions defined in the block.

```ruby
array.select { |x| x > 3}
```

## ```.upto```, ```.downto```

```ruby
1.upto(5) { |number| puts number}  1 2 3 4 5
"L".upto("O") { |letter| puts letter}  L M N O
5.downto(1) { |number| puts number}  5 4 3 2 1

array.reduce(:+) Returns sum of values in array. + is passed like a block.
array.inject(:+) Works similarly.
```

## Hashes

Literal Notation

```ruby
my_hash = {
  "name"    => "Eric",
  "age"     => 26,
  "hungry?" => true
}
```

It's often faster to use symbols (:symbol) as keys. In Ruby 1.9 onward you can use this notation:

```ruby
my_hash = {
   name: "Eric",
   age: 26,
   hungry: true
}
```

### ```.new``` notation

```ruby
my_hash = Hash.new

my_hash["name"] = "Eric"  Adds (or changes) key-value pair.
my_hash = Hash.new("derp")  creates a hash with "derp" as the default nil       (that is, the value of an undefined key)
my_hash.select { |k, v| v > 3}  returns values greater than 3 (an example).
```


### Some Hash Methods

```ruby
.keys   returns list of keys as an array
.values   returns list of keys as an array
.has_key?(key)
.has_value?(value)
.merge(another_hash) combines 2 hashes, values of another_hash trump the other if there    are matching keys
```


## Methods

```ruby
def say_hello(parameter)
  puts "Hello there, #{parameter}!"
end
```



## Splat Arguments

*parameter  a "splat argument" – can accept an indefinite # of arguments.  splat arguments are stored as an an array. def what_up(greeting, *bros)  bros.each { |bro| puts "#{greeting}, #{bro}!" }  end


## Procs

A closure or a "saved block”. Kind of like a method, but it can be used like a block and passed to methods that take blocks as parameters. & is used to convert a proc into a block.

```ruby
cube = Proc.new { |x| x ** 3 }

[1, 2, 3].collect!(&cube)  & is used to convert a proc into a block.

cube.call(2)    .call calls procs directly.
```

Methods can be treated like blocks, too!:

```ruby
strings_array = numbers_array.collect(&:to_s)
```


## Lamdas

A closure. More or less identical to PROCS, with a key difference: when a lambda returns, it passes control back to the calling method; when a proc returns, it does so immediately, without finishing the calling method.

```ruby
cube = lambda { |x| x ** 3 }

[1, 2, 3].collect!(&cube)

cube.call(2)
```


## Scope Prefixes

Prefixed to variables to specify their scope.

* **Global Variable**: available everywhere
* **Local Variable**: available only within a method
* **Class Variable**: available to a common class (all instances share it)
* **Instance Variable**: available only to a particular instance of a class

```ruby
$ # global variable (variables are global by default unless inside a    method or class, use this prefix if you want to make an exception    for a variable within a method or class).

@ # instance variable (specific to a single instance of a class).
@@ # class variable
```


## Classes

```ruby
class NameOfClass
  def initialize(x)
    @x = x
  end
end

class Class < SuperClass
  #this is the syntax for class inheritance.
end

class Name
  #public methods here
  private
  #private methods here
end

attr_reader :variable  # allows you to read "variable" without an extra method
attr_writer :variable  # allows you to edit "variable"
attr_accessor :variable  # allows you to both read and edit "variable"
```


## Modules

"Toolkits" for the interpreter; like a class but it doesn't have instances.

```ruby
module Circle

  #capitalized variables are "constants" and are not supposed to change.
  PI = 3.141592653589793

  def Circle.area(radius)  #the Module must be called explicitly in each method.
    PI * radius**2
  end

  def Circle.circumference(radius)
    2 * PI * radius
  end

end


puts Circle::PI   scope resolution operator ("get this from the module")

require 'circle'  imports a given module into the environment

include Circle   when placed in a class, this allows an instance of the      class to use the module's methods as if they were its own.     This is called a "mixin," and allows Ruby to mimic      multiple class inheritance, which it can't normally do –     it CAN "inherit" multiple modules.

require_relative ‘something.rb’ allows you to access the data found in another file in the   same directory.
```
