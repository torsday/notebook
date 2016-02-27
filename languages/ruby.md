# Ruby

<!--lint disable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---

**Table of Contents**

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Good to Know](#good-to-know)
- [[Strings]((http://ruby-doc.org/core/String.html)](#stringshttpruby-docorgcorestringhtml)
- [Number Methods](#number-methods)
- [Misc](#misc)
- [Comparison Operators](#comparison-operators)
- [Boolean Operators](#boolean-operators)
- [Operators](#operators)
- [Combined Comparison Operator](#combined-comparison-operator)
- [[Arrays](http://ruby-doc.org/core/Array.html)](#arrayshttpruby-docorgcorearrayhtml)
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
  - [calling a parent method in ruby:](#calling-a-parent-method-in-ruby)
- [Modules](#modules)
- [Getting all but the first element from Ruby array](#getting-all-but-the-first-element-from-ruby-array)
  - [Shift](#shift)
  - [Slice](#slice)
  - [Drop](#drop)
- [Returning a fixed number of items from the tail of a list](#returning-a-fixed-number-of-items-from-the-tail-of-a-list)
- [Basic Object](#basic-object)
- [Currying in Ruby](#currying-in-ruby)
- [Inject vs each_with_object](#inject-vs-eachwithobject)
  - [Inject](#inject)
  - [each_with_object](#eachwithobject)
- [Using pry and ncurses together](#using-pry-and-ncurses-together)
- [Parallel assignment](#parallel-assignment)
  - [Empty arrays](#empty-arrays)
- [Regex Literals and URLs](#regex-literals-and-urls)
- [Spliting a string into a maximum number of segments](#spliting-a-string-into-a-maximum-number-of-segments)
- [The `DATA` constant](#the-data-constant)
- [References](#references)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---

## Good to Know

1.  Everything is an object

    -   Uniform access principle

1.  Classes

1.  Blocks (closures or anonymous functions)

1.  Hashes

## [Strings](http://ruby-doc.org/core/String.html)

```ruby
.length
.reverse
.upcase
.downcase
.capitalize    # capitalizes the first letter
.include? "x"  # tests if string contains "x"
.match         # works like .include?
.start_with?("x")
.end_with?("x")

“a”.next  => “b”

"#{}"  # string interpolation - "My name is #{name}"
```

Returns a copy of str with the all occurrences of pattern substituted. Pattern is typically a regex.

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
.abs      # absolute value
.ceil     # rounds float up
.floor    # rounds float down
.eql?(n)  # is the object equal to n?
```

## Misc

```ruby
gets            # raw input from user (get string)
gets.chomp      # raw input from user w/o extra line
.is_a? Integer  # tests whether == given data type

rand     # generates random float between 0 and 1
rand(n)  # generates random integer between 0 and n, exclusive

.sort    # sorts numerically or alphabetically.
# For a reverse sort, include the following block as a parameter:
array.sort! { |first, second| second <=> first }
# or
array.sort.reverse!

.to_s   # converts a variable to a string
.to_i   # converts to integer
.to_f   # converts to float
.to_sym # or .intern converts a string to a symbol

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
&&  # and
||  # or
!   # not
```

## Operators

```ruby
+=
-=
*=
/=

||=  # conditional assignment operator - only assigns a value to a variable if the current value of the variable is nil.
```

## Combined Comparison Operator

```sh
<=>
```

Returns `0` if the first operand (item to be compared) equals the second, `1` if first operand is greater than the second, and `-1` if the first operand is less than the second.

## [Arrays](http://ruby-doc.org/core/Array.html)

```ruby
array = [1, 2, 3]
array[0]      # fetch item at given index
array[0][0]   # fetch item at given index (2D array or beyond)
array[0] = 1  # set item at given index
array << 23   # add item to end of array ("concatenation operation")

array.push(element) << is a shortcut for this
array.pop(element)

array.unshift(element) # like push but it adds to beginning of array
array.shift(element)   # like pop but it removes from beginning of array

array.first   # returns first element
array.length  # returns # of elements
array.empty?
array.include?(x)
array.index(x)  # What index is the given element at?

array.join(x)    # returns elements as string separated by x
string.split(x)  # turns a string into an array with x as separator
```

get where two arrays match in ruby: use [Intersection, or `&`](http://ruby-doc.org/core-2.3.0/Array.html#method-i-26)

```ruby
x = [1, 2, 4]
y = [5, 2, 4]
x & y # => [2, 4]
```

## Loops

```ruby
while
until            # opposite of while (stops when false)
for x in 1...10  # Up to 10, exclusive (9 times), e.g.: for num in 1...10   puts num  end
for x in 1..10   # Up to 10, inclusive (10 times)
```

## One Line Ifs

```ruby
puts "It's true" if true
```

## Ternary Conditional Expressions

```ruby
puts 0 < 1 ? "0 is less than one" : "0 is greater than 1"
```

## Case Statements

```ruby
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
  yield n   # Passes "n" to the block. yield can also be standalone.
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

array.reduce(:+) # Returns sum of values in array. + is passed like a block.
array.inject(:+) # Works similarly.
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

my_hash["name"] = "Eric"             # Adds (or changes) key-value pair.
my_hash         = Hash.new("derp")   # creates a hash with "derp" as the default nil (that is, the value of an undefined key)
my_hash.select { |k, v| v > 3}       # returns values greater than 3 (an example).
```

### Some Hash Methods

```ruby
.keys     # returns list of keys as an array
.values   # returns list of keys as an array
.has_key?(key)
.has_value?(value)
.merge(another_hash) # combines 2 hashes, values of another_hash trump the other if there are matching keys
```

## Methods

```ruby
def say_hello(parameter)
  puts "Hello there, #{parameter}!"
end
```

## Splat Arguments

A "splat argument" – can accept an indefinite # of arguments, stored as an an array.

```ruby
def what_up(greeting, *bros)
  bros.each { |bro| puts "#{greeting}, #{bro}!" }
end
```

## Procs

A closure or a "saved block”. Kind of like a method, but it can be used like a block and passed to methods that take blocks as parameters. & is used to convert a proc into a block.

```ruby
cube = Proc.new { |x| x ** 3 }

[1, 2, 3].collect!(&cube) # & is used to convert a proc into a block.

cube.call(2)    # .call calls procs directly.
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

-   **Global Variable**: available everywhere
-   **Local Variable**: available only within a method
-   **Class Variable**: available to a common class (all instances share it)
-   **Instance Variable**: available only to a particular instance of a class

```ruby
$  # global variable (variables are global by default unless inside a    method or class, use this prefix if you want to make an exception    for a variable within a method or class).
@  # instance variable (specific to a single instance of a class).
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

attr_reader :variable    # allows you to read "variable" without an extra method
attr_writer :variable    # allows you to edit "variable"
attr_accessor :variable  # allows you to both read and edit "variable"
```

### calling a parent method in ruby:

*From: [StackOverflow](https://stackoverflow.com/questions/18448831/calling-method-in-parent-class-from-subclass-methods-in-ruby)*

> If the method is the same name, i.e. you're overriding a method you can simply use super. Otherwise you can use an alias_method or a binding.

```ruby
class Parent
    def method
    end
end

class Child < Parent
    alias_method :parent_method, :method
    def method
        super
    end

    def other_method
        parent_method
        #OR
        Parent.instance_method(:method).bind(self).call
    end
end
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

include Circle   # when placed in a class, this allows an instance of the class to use the module's methods as if they were its own.     This is called a "mixin," and allows Ruby to mimic multiple class inheritance, which it can't normally do – it CAN "inherit" multiple modules.

require_relative ‘something.rb’ # allows you to access the data found in another file in the   same directory.
```

---

## Getting all but the first element from Ruby array

When getting all but the first element from an array in Ruby, we have a few
options.

Given the following list:

```ruby
list = [1,2,3,4]
```

### Shift

We could use [`shift`][shift docs], however it mutates the array. It also
doesn't return the list so we need two lines to write this code:

```ruby
list.shift # => 1
rest_of_list = list # => [2,3,4]
```

### Slice

In the past I've used [`slice`][slice docs], but specifying indices or passing
the length of an array is ugly and low-level:

```ruby
rest_of_list = list[1..-1] # => [2,3,4]
rest_of_list = list.slice(1, list.length) # => [2,3,4]

list # is not modified # => [1,2,3,4]
```

### Drop

My new favorite is [`drop`][drop docs] which does not mutate and does not
require ugly, low-level code:

```ruby
list.drop(1) # => [2,3,4]

list # is not modified # => [1,2,3,4]
```

An added benefit of`drop` is that it will always return an array, while `slice`
will sometimes return `nil`

```ruby
[].slice(1..-1) # => nil

[].drop(1) # => []
```

---

## Returning a fixed number of items from the tail of a list

[`Array#last`][last docs] takes an argument to limit the number of items to return
from the tail of a list.

```ruby
> [1,2,3,4,5].last(2) # => [4, 5]
```

---

## Basic Object

Ruby has a `BasicObject` class which doesn't include Kernel methods and acts as
the parent for all `Object`s. You can see the ancestry in practice via:

```ruby
Object.ancestors      # => [Object, Kernel, BasicObject]
BasicObject.ancestors # => [BasicObject]
```

`BasicObject` thus has very few instance methods which would be inherited by a
subclass:

```ruby
BasicObject.instance_methods   # => [:==, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]
Object.instance_methods.length # => 55
```

This is useful for delegators which would otherwise not delegate methods such as
\#to_s.

Example:

```ruby
class ListDelegator
  def initialize(*list)
    @list = list
  end

  def method_missing(method, *args, &block)
    @list.map do |item|
      item.__send__(method, *args, &block)
    end
  end
end

class ListDelegatorBasic < BasicObject
  def initialize(*list)
    @list = list
  end

  def method_missing(method, *args, &block)
    @list.map do |item|
      item.__send__(method, *args, &block)
    end
  end
end

class Out
  def to_s
    "Out"
  end
end

ListDelegator.new(Out.new).to_s      # => "#<ListDelegator2:0x007fcab400d148>"
ListDelegatorBasic.new(Out.new).to_s # => ["Out"]
```

---

## Currying in Ruby

Ruby defines `curry` for `Method` and `Proc`, allowing procs to return partially
applied procs when they get called with fewer than the required number of
arguments. For example:

```ruby
multiply = -> x,y { x * y }.curry # => #<Proc:0x007fed33851510 (lambda)>
multiply[2,3] # => 6
double = multiply[2] # => #<Proc:0x007fed35892888 (lambda)>
double[3] # => 6
```

**Note:** While `Proc#curry` has been around since Ruby 1.9, `Method#curry` was
only added in Ruby 2.2.0. For versions before 2.2.0, you will first need to
convert your method object to a proc via `Method#to_proc`.

Check out the [ruby docs][] for more details.

---

## Inject vs each_with_object

### Inject

Inject takes the value of the block and passes it along.
This causes a lot of errors like.

```ruby
inject_array = ['A', 'B', 'C', 'D']

inject_array.inject({}) do |accumulator, value|
  accumulator[value] = value.downcase
end

# 'IndexError: string not matched'
```

The above code causes `IndexError: string not matched error`.

What you really wanted.

```ruby
inject_array = ['A', 'B', 'C', 'D']

inject_array.inject({}) do |accumulator, value|
  accumulator[value] = value.downcase
  accumulator
end

# Output: => {"A"=>"a", "B"=>"b", "C"=>"c", "D"=>"d"}
```

### each_with_object

`each_with_object` ignores the return value of the block and passes the initial object along.

```ruby
array = ['A', 'B', 'C', 'D']

array.each_with_object({}) do |value, accumulator|
  accumulator[value] = value.downcase
end

# Output: => {"A"=>"a", "B"=>"b", "C"=>"c", "D"=>"d"}
```

One more thing which you can notice is the order of arguments to the block for each of the functions.

Inject takes the result/accumulator and then the iteratable value, whereas `each_with_object` takes the value followed by the result/accumulator.

---

## Using pry and ncurses together

Because of ncurse's visual mode you will not be able to use pry normally.
The easiest way to get pry working is to do the following:

```ruby
close_screen
binding.pry
refresh
```

[`close_screen`][close_screen docs] restores the non-visual mode which allows you to see the
output of pry correctly. When you `exit` from pry, `refresh` will resume
ncurse's visual mode.

---

## Parallel assignment

Ruby allows us to assign multiple variables on the same line. This is also
called parallel assignment.

```ruby
a, b = 1, 2 # => [1, 2]
a           # => 1
b           # => 2
```

We can also use parallel assignment and the splat operator in combination to
split the array into the head and tail. This is in particular useful if we want
to [get all but the first element from an array](all-but-the-first-element-from-array.md).

```ruby
list = [1,2,3,4]   # => [1,2,3,4]
head, *tail = list # => [1,2,3,4]
head               # => 1
tail               # => [2,3,4]

list # is not modified # => [1,2,3,4]
```

### Empty arrays

When using parallel assignment on an empty array, the tail will always return an
array while the head will be `nil`.

```ruby
head, *tail = [] # => []
head             # => nil
tail             # => []
```

---

## Regex Literals and URLs

Regular expressions in Ruby are typically delineated by the `/` character.
However, this forces you to escape `/` in your expression.

I was recently using a regex to match certain URLs

```ruby
/http:\/\/sub\.domain\.com\/path/
```

A colleague pointed out that I could use the `%r{...}` notation and avoid
escaping all those slashes.

```ruby
%r{http://sub\.domain\.com/path}
```

Much cleaner!

---

## Spliting a string into a maximum number of segments

[`String#split`][split docs] takes an argument to limit the number of returned
matches. Once the limit is reached, the rest of the string is returned as one
match even if it contains more delimiters.

For example, say we are parsing a string whose first two lines are always
headers and the rest is the body:

```ruby
text = <<-TEXT
header1 = value
header2 = value
the body
keeps going
on over
multiple lines
TEXT
```

A simple `split` on newlines would create an array with each line as an
individual element:

```ruby
text.split("\n")
# => ["header1 = value",
#     "header2 = value",
#     "the body",
#     "keeps going",
#     "on over",
#     "multiple lines"]
```

Since we know there are two headers and a body, we can tell `split` to stop splitting once we have three segments:

```ruby
text.split("\n", 3)
# => ["header1 = value",
#     "header2 = value",
#     "the body\nkeeps going\non over\nmultiple lines"]
```

---

## The `DATA` constant

 The `DATA` constant in Ruby allows us to access the text at the end of our file listed after the `__END__` block. This can be surprisingly useful, for instance if we need to extract information from a rather large data blob.

Imagine a scenario where we need to extract the user names from a SQL statement.

```ruby
puts DATA.read.gsub("ALTER USER ", "").gsub(/IDENTIFIED BY.+/, "")

__END__
ALTER USER Annette IDENTIFIED BY 'Annette';
ALTER USER Warren IDENTIFIED BY 'Warren';
ALTER USER Anthony IDENTIFIED BY 'Anthony ';
ALTER USER Preston IDENTIFIED BY 'Preston';
ALTER USER Kelly IDENTIFIED BY 'Kelly ';
ALTER USER Taylor IDENTIFIED BY 'Taylor';
ALTER USER Stiller IDENTIFIED BY 'Stiller';
ALTER USER Dennis IDENTIFIED BY 'Dennis';
ALTER USER Schwart IDENTIFIED BY 'Schwart';
```

Executing the file will print this:

```txt
Annette
Warren
Anthony
Preston
Kelly
Taylor
Stiller
Dennis
Schwart
```

Since `DATA` is simply just a virtual `File` object within our file, we can also pass the `DATA` variable (without `#read`) to methods that accept a `File`.

```ruby
require "json"

puts JSON.load(DATA)

__END__
{
  "records": [
    {
      "artist":"Iggy Pop",
      "title":"Lust for Life"
    },
    {
      "artist":"Television",
      "title":"Marquee Moon"
    },
    {
      "artist":"Talking Heads",
      "title":"Talking Heads: 77"
    }
  ]
}
```

## `Dir`

### Change dir

```ruby
Dir.chdr(dir)
```

### Elements in dir

```ruby
def elements_in_dir(dir)
  Dir.chdir(dir)
  Dir.glob('*')
end
```

### Dirs in dir

```ruby
def dirs_in_dir(dir)
  original_dir = Dir.pwd
  Dir.chdir(dir)
  dirs = Dir.glob('*').select {|f| File.directory? f}
  Dir.chdir(original_dir)
  dirs
end
```

## `File`

### Rename file/dir

```ruby
File.rename "original_path", "new_path"
```

## References

-   [Ruby Docs: Array](http://ruby-doc.org/core/Array.html)
-   [Ruby Docs: Enumerable](http://ruby-doc.org/core/Enumerable.html)
-   [Ruby Docs: String](http://ruby-doc.org/core/String.html)

[close_screen docs]: http://ruby-doc.org/stdlib-2.0/libdoc/curses/rdoc/Curses.html#method-c-close_screen
[drop docs]: http://www.ruby-doc.org/core-2.2.0/Array.html#method-i-drop
[last docs]: http://www.ruby-doc.org/core-2.2.0/Array.html#method-i-last
[ruby docs]: http://ruby-doc.org/core-2.2.0/Proc.html#method-i-curry
[shift docs]: http://www.ruby-doc.org/core-2.2.0/Array.html#method-i-shift
[slice docs]: http://www.ruby-doc.org/core-2.2.0/Array.html#method-i-slice
[split docs]: http://www.ruby-doc.org/core-2.2.0/String.html#method-i-split
