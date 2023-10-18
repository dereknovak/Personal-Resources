# 🙋 Sentences

## 1. Numbers and Letters
### Integer
```ruby
integer = 1
```
The variable `integer` is initialized to reference an Integer object with value `1`.
### Float
```ruby
float = 1.0
```
The variable `float` is initialized to reference a Float object with value `1.0`.
### String
```ruby
a = "string"
```
The variable `a` is initialized and to reference a String object with value `"string"`.

## 2. String Manipulation
### Interpolation
```ruby
b = "#{a}!"
```
The variable `b` is initialized. The value of `a` (which is `"string"`) is interpolated into the string `"#{a}!"`, resulting in the string `"string!"` being assigned to the variable `b`.
### Non-mutating Concatenation
```ruby
b += "!"
```
The string `"!"` is concatenated to the string held by `b`. The `+=` operator creates a new string with the concatenated value, reassigning `b` to point to a new string object with value `"string!!"`.
### Mutating Concatenation
```ruby
b << "!"
```
The string `"!"` is concatenated to the string held by `b`. The shovel operator `<<` mutates the original string object that `b` references, modifying its value to `"string!!!"`.
## 3. Boolean Logic and Values
### Boolean value
```ruby
boolean = true
```
The local variable `boolean` is initialized and assigned the boolean `true`.
### Truthiness
```ruby
if integer
	puts "string"
end
```
The conditional statement `if` evaluates if `a` is truthy. As everything in Ruby is truthy except `false` and `nil`, the `if` branch is executed.
### nil
```ruby
nil == false
```
`nil == false` comparison expression evaluates whether the value of `nil` is equal to the value of boolean `false`. It returns `false`, indicating that `false` and `nil` are not equal.

## 4. Collections
### Array
```ruby
array = ["element1", "element2"]
```
The local variable `array` is assigned to reference an Array object with value `["element1", "element2"]`

#### `#[]`
```ruby
array[0]
```
The `#[]` method is called with Integer `0` passed to it as an argument. It returns the value of the element in `array` at index `0`, which is `"element1"`

#### `#[]=`
```ruby
array[0] = "element0"
```
The `#[]=` method is called with Integer `0` and String `"element0"` passed to it as arguments. It reassigns the value of the element in `array` at index `0` to the string `"element0"`. It returns the second argument, which is `"element0"`.
### Hash
```ruby
hash = { key1: "value1", :key2 => "value2"}
```
The local variable `hash` is assigned to reference a Hash object with value `{ key1: "value1", :key2 => "value2"}`

#### `#[]`
```ruby
hash[:key1]
```
The `#[]` method is called with Symbol `:key1` passed to it as an argument. It returns the value of the `:key1` key in `hash`, which is `"value1"`

#### `#[]=`
```ruby
hash[:key1] = "value2"
```

The `#[]=` method is called with Symbol `:key1` and String `"value2"` passed to it as arguments. It reassigns the value of the `:key1` key in `hash` to the string `"value2"`. It returns the second argument, which is `"value2"`.

### Common Methods

#### `#size`/`#length`
```ruby
array.size
```
The `size` method is called on `array`. It returns the number of elements in `array`, which is `2`. 

#### `#push` / `<<`
```ruby
array.push("element3")
```
The mutating `push` method is called on `array`. It appends the string `"element3"` to the original array object `array` is pointing to. It returns the value of `array`, which is `["element0", "element2", "element3"]`.

```ruby
array << "element3"
```
The mutating `<<` shovel operator is used to append the string `"element3"` to the original array object `array` is pointing to. It returns the value of `array`, which is `["element0", "element2", "element3"]`.
#### `#concat`
```ruby
array.concat(["element4"], ["element5", "element6"])
```
The `concat` method is called on `array` with array `["element4"]` and array `["element5", "element6"]` passed to it as arguments. It appends the strings `"element4"`, `"element5"` and `"element6"` to the original array object `array` is pointing to. It returns the value of `array`, , which is `["element0", "element2", "element3", "element4", "element5", "element6"]`.
#### `#unshift`
```ruby
array.unshift("element-1")
```
The `unshift` method is called on `array` with `"element-1"` passed to it as an argument. It prepends `"element-1"` to the original array object  `array` is pointing to. It returns the value of `array`, which is `["element-1", "element0", "element2", "element3", "element4", "element5", "element6"]`.
#### `#pop`
```ruby
array.pop
```
The `pop` method is called on `array`. It removes the trailing element `"element6"` from the original array object `array` is pointing to. It returns the deleted element `"element6"`.

#### `#shift`
```ruby
array.shift
```
The `shift` method is called on `array`. It deletes the leading element `"element-1"` from the original array object `array` is pointing to. It returns the deleted element `"element-1"`.

#### `#delete`
```ruby
array.delete("element5")
```
The `delete` method is called on `array` with `"element5"` passed to it as an argument. It deletes `"element5"` from `array`. It returns the deleted element `"element5"`.

#### `#flatten`
```ruby
array.flatten
```
The `flatten` method is called on `array`. It replaces each nested array inside `array` to its individual elements. It returns the value of `array`, which is `["element0", "element2", "element3", "element4"]`.

#### `#join`
```ruby
array.join
```
The `join` method is called on `array`. It returns a string with value `"element0element2element3element4"` formed by combining every element in `array`. 

#### `#sort`
```ruby
array.sort
```
The `sort` method is called on `array`. It sorts a copy of the array object pointed by `array` in ascending lexicographic/numeric order. It returns this copied and sorted version of `array`, which is `["element0", "element2", "element3", "element4"]`.

#### `#include?`
```ruby
array.include?("element3")
```
The `include?` method is called on `array` with string `"element3"` passed to it as an argument. It returns a boolean indicating if any element in `array` is equal to `"element3"`, which is `true`.

#### `#count`
```ruby
array.count("element3")
```
The `count` method is called on `array`. It returns the count of elements in `array` that equals to string `"element3"`, which is `1`.

## 5. Operators

### Numeric operators

#### `+`
```ruby
3 + 2
```
The `+` operator is used to return the result of `3` plus `2`, which is `5`.
#### `-`
```ruby
3 - 2
```
The `-` operator is used to return the result of `3` minus `2`, which is `1`.
#### `*`
```ruby
3 * 2
```
The `*` operator is used to return the result of `3` multiplied by `2`, which is `6`.
#### `/`
```ruby
3 / 2
```
The `/` operator is used to return the quotient from the division of `3` by `2`, which is `1`.
#### `%`
```ruby
3 % 2
```
The `%` operator is used to return the modulus from the division of `3` by `2`, which is `1`.
#### `divmod`
```ruby
3.divmod(2)
```
The `divmod` method is called on `3`, with `2` passed to it as an argument. It returns an array containing the quotient and the modulus of `3` divided by `2`, which is `[1, 1]`.
#### `**`
```ruby
3 ** 2
```
The `**` operator is used to return the result from `3` raised to the power of `2`, which is `9`.
### String operators
#### `+`
```ruby
"hello" + " world
```
The `+` operator is used to concatenate the string `" world"` to the string `"hello"`. It returns `"hello world"`.
#### `*`
```ruby
"hello " * 3
```
The `*` operator is used to repeat the string `"hello"` three times. It returns `"hello hello hello"`.

### Conditional Operators

#### `==`
```ruby
3 == 2
```
The `==` operator returns `false` when evaluating `3` as equal to `2`.

#### `!=`
```ruby
3 != 2
```
The `!=` operator returns `true` when evaluating `3` as not equal to `2`.

#### `>`
```ruby
3 > 2
```
The `>` operator returns `true` when evaluating `3` as greater than `2`.

#### `<`
```ruby
3 < 2
```
The `<` operator returns `false` when evaluating `3` as less than `2`.

#### `>=`
```ruby
3 >= 2
```
The `>=` operator returns `true` when evaluating `3` as greater than or equal to `2`.

#### `<=`
```ruby
3 <= 2
```
The `<=` operator returns `false` when evaluating `3` as less than or equal to `2`.



#### `ternary`
```ruby
x = 5
result = x > 3 ? "x is greater than 3" : "x is not greater than 3"
```
The ternary operator is used to evaluate the condition `x > 3`. If it's truthy, it returns `"x is greater than 3"`. If it's falsy, it returns `"x is not greater than 3"`.
### Logical Operators & Short-Circuit Evaluation

#### `&&`
```ruby
true && false
```
The `&&` operator returns `false` when performing a logical AND operation between `true` and `false`.

##### Short-circuit: 
If the left operand is `false`, the right operand is not evaluated.
🔗⬅️❌⛔

#### `||`
```ruby
true || false
```
The `||` operator returns `true` when performing a logical OR operation between `true` and `false`.

##### Short-circuit: 
If the left operand is `true`, the right operand is not evaluated. 
🔀⬅️✔️⛔

#### `!`
```ruby
!true
```
The `!` operator returns `false` when negating the boolean value of `true`.

### Operator precedence
#### PEUMACAOTA
**P**eter, **E**very **U**nicorn **M**ust **A**lways **C**rave **A**pples **O**r **T**aste **A**pricots.
10. Parentheses `()` - <mark class="hltr-red">Highest precedence</mark>  
9. Exponentiation `**`  
8. Unary plus `+` and minus `-` (also used for negation)  
7. Multiplication `*`, Division `/`, and Modulus `%`  
6. Addition `+` and Subtraction `-`  
5. Comparison operators: `<`, `>`, `<=`, `>=`, `==`, `!=`  
4. Logical AND `&&`  
3. Logical OR `||`  
2. Ternary operator `? :`  
1. Assignment operators: `=`, `+=`, `-=`, `*=`, `/=`, `%=`, etc. - <mark class="hltr-blue">Lowest precedence</mark>

## 6. Type Conversion

### `to_s` 
```ruby
number = 42
number.to_s
```
The `to_s` method is called on `number`. It returns the result value of the conversion of the integer `42` to the string `"42"`.

### `to_i`
```ruby
string_number = "42"
string_number.to_i
```
The `to_i` method is used is called on `string_number`. It returns the result value of the conversion of the string `"42"` to the integer `42`.

### `to_f`
```ruby
string_float = "3.14"
string_float.to_f
```
The `to_f` method is called on `string_float`. It returns the result value of the conversion of the string `"3.14"` to the float `3.14`.

### `to_a`
```ruby
string = "hello"
string.to_a
```
The `to_a` method is called on `string`. It returns the result value of the conversion of the string `"hello"` to the array `["hello"]`.

### `to_h` 
```ruby
array_of_pairs = [[:key1, "value1"], [:key2, "value2"]]
hash_from_array = array_of_pairs.to_h
```
The `to_h` method is called on `array_of_pairs`. It returns the result value of the conversion of the array `[[:key1, "value1"], [:key2, "value2"]]` to the hash `{:key1=>"value1", :key2=>"value2"}`.

## 8. Variables

### Types of variables
```ruby
$global_variable = "Hey"
local_variable = "Hey"
@@class_variable = "Hey"
@instance_variable = "Hey"
CONSTANT = "Hey"
```
### Reassignement
```ruby
a = 1
a = 2
```
`a` is reassigned to reference the Integer object with value `2`.
### Method Scope
```ruby
var = 0

def method
	var = 1
end

method
puts var
```
On line 1, the local variable `var` is initialized to reference the integer object with value `0`.
On line 7, the `method` method is called.
On line 3, the `method` method is defined with no parameters.
Inside the method's body, on line 4, the local variable `var` is initialized to reference the integer object with value `1`. As methods have their own self contained scope, the `var` variable initialized inside the method is a different variable from the `var` variable initialized outside the method on line 1. 
On line 8, the value of local variable `var` is passed as an argument to the `puts` method and outputs `0`.
### Block Scope
```ruby
var = 0

loop do
	var = 1
	break
end

puts var
```
On line 1, the local variable `var` is initialized to reference the Integer object with value `0`.
On line 3, the `loop` method is called and a block delimited by `do..end` is passed to it as an argument.
Inside the block, on line 2, `var` is reassigned to reference the Integer object with value `1`.
On line 4, the value of `var` is passed as an argument to the `puts` method. 

## 9. Conditionals and Loops

### `loop do`
```ruby
i = 10

loop do
	i -= 1
	break if i == 0
end
```
On line 1, the local variable `i` is initialized to reference the Integer object with value `10`.
On line 3, the `loop` method is called and a block delimited by `do..end` is passed to it as an argument.
Inside the block, on line 4, `i` is decremented by `1`. 
On line 5, the keyword `break` is used to break out of the loop, if the value of `i` is equal to `0`. According to the condition, the loop executes 10 times.
After loop complete exectuin, `i` now holds the value `0`

### `while` Loop
```ruby
counter = 0

while counter < 5 do
	counter += 1
end 
```
On line 1, the local variable `counter` is initialized to reference the Integer object with value `0`.
On line 3, the `while` keyword initiates a loop. The loop continues executing while the condition `counter < 5` evaluates as true.
Inside the loop, on line 4, `counter` is incremented by `1`. According to the condition, the loop executes 5 times. 
After loop complete execution, `counter` now holds the value `5`.

### `until` Loop
```ruby
counter = 0

until counter >= 5 do
	counter += 1
end 
```
On line 1, the local variable `counter` is initialized to reference the Integer object with value `0`.
On line 3, the `until` keyword initiates a loop. The loop continues executing until the condition `counter >= 5` evaluates as true.
Inside the loop, on line 4, `counter` is incremented by `1`. According to the condition, the loop executes 5 times. 
After loop complete execution, `counter` now holds the value `5`.

### `for` Loop
```ruby
for num in 1..3 do
	puts num
end
```
On line 1, the `for` keyword initiates an iteration through the range `1..3`, assigning each value of `1..3` to the variable `num`.
Inside the loop, on line 2, the `puts` method is called with the current value of `num` passed to it as an argument. It outputs
```
1
2
3
```
### `times` method

```ruby
3.times do |index|
	puts "Hello!"	
end
```
On line 1, the `times` method is called on the Integer `3`. A block delimited by `do..end` is passed to it as an argument. `times` loops `3` times, assigning the current zero-indexed iteration number to block variable `index`.
Inside the block, on line 2, the `puts` method is called with string `"Hello!"` passed to it as an argument.
It will output `"Hello!"` 3 times. 
`times` returns the number of iterations completed.s

### `each` Iterator
```ruby
fruits = ["apple", "banana", "orange"]

fruits.each do |fruit|
	puts fruit
end
```
On line 3, the `each` method is called on the `fruits` array. 
A block delimited by `do..end` is passed to it as an argument. 
`each` iterates through each element of `fruits`, assigning the current element to the block variable `fruit`. 
Inside the block, on line 4, the `puts` method is called with the value of `fruit` passed to it as an argument. 
It will output the value of `fruit` for each element in `fruits`.
`each` returns the original array it has been called on, which is `["apple", "banana", "orange"]`



### `map` Iterator
```ruby
fruits = ["apple", "banana", "orange"]

fruits.map do |fruit|
	fruit + " is good"
end
```
On line 3, the `map` method is called on the `fruits` array. 
A block delimited by `do..end` is passed to it as an argument. 
`map` iterates through each element of `fruits`, assigning the current element to the block variable `fruit`. 
Inside the block, on line 4, the `+` operator is used to concatenate the string `" is good"` to the string referenced by `fruit`. 
The result of this expression is then returned by the block to the `map` method. 
`map` returns an array with each returned value from the block, which is `["apple is good", "banana is good", "orange is good"]`.

### `break` Statement
```ruby
loop do
	break
end
```
The `break` statement is used to exit the loop prematurely.

### `next` Statement
```ruby
var = 0

loop do
	var += 1
	next if var == 1
	break if var == 2
end
```
On line 5, the `next` statement is used to skip the current iteration of the loop and execute the next one if `var` equals `1`.

### `if` Statement
```ruby
age = 18

if age >= 18
	puts "You are an adult."
else
	puts "You are a minor."
end
```
On line 3, the `if` statement checks if `age` is greater than or equal to `18`.
The condition evaluates as true, so the body of `if` is executed.
On line 4, the `puts` method is called and the string `"You are an adult"` is passed to it as an argument.
### `case` Statement
```ruby
day = "Wednesday"

case day
when "Monday"
	puts "Start of the workweek."
when "Wednesday"
	puts "Midweek!"
else
	puts "Another day."
end
```
The `case` statement compares the value of `day` against multiple `when` conditions.
As `day` value is `"Wednesday"`, the body corresponding to the `"Wednesday"` `when` condition is executed.

### `unless` Statement
```ruby
rainy_day = true

unless rainy_day
	puts "It's a sunny day!"
else
	puts "Don't forget your umbrella."
end
```
The `unless` statement checks if `rainy_day` is falsy.
If the condition evaluates as false, the body of `unless` is executed; otherwise, the code in the `else` body is executed.

### Ternary Operator
```ruby
x = 5
x > 3 ? "x is greater than 3" : "x is not greater than 3"
```
The ternary operator is used to evaluate the condition `x > 3`.
If the condition evaluates as true, it returns `"x is greater than 3"`; otherwise, it returns `"x is not greater than 3"`.


## 10. Output, Return & Expressions
### Output
```ruby
puts "hello"
```
The string `"hello"` is passed as an argument to the `puts` method call. It will output `"hello"` and return `nil`.
### Return
```ruby
return "hello"
```
The `return` keyword is used to return the string `"hello"`.

## 11. Methods
### Method definition
```ruby
def foo end
```
The `foo` method is defined.

### Method call
```ruby
foo
```
The `foo` method is called.

### Default parameters
```ruby
def foo(bar = true)
	bar
end
```
The `foo` method is defined with parameter `bar` holding the default value `true`.
### Parameters
```ruby
def foo(bar)
	bar
end
```
The `foo` method is defined with 1 parameter named `bar`.

### Arguments
```ruby
foo("bar")
```
The string `"bar"` is passed as an argument to the `foo` method call.

### Implicit return value
```ruby
def foo(bar)
	bar
end
```
On line 2, the value of the `bar` variable is implicitly returned because it is the last expression evaluated in the method.

### Explicit return value
```ruby
def foo(bar)
	return bar
end
```
On line 2, the value of the `bar` variable is explicitly returned with the use of the `return` keyword.

## 12. Concepts

- Errors being raised
- Code is expected to perform in a certain way VS actually performed

### Local Variable Scope
#### Blocks
This code demonstrates the concept of Local Variable Scope within blocks. When a block is defined, the local variables from the outer scope are accessible within the block. However, variables initialized within the block are confined to that block's scope and cannot be accessed outside of it.
#### Methods
This code demonstrates the concept of Local Variable Scope within methods. When a method is defined, the local variables from the outer scope are not accessible within the method. Additionnally, variables initialized within the method are confined to that method's scope and cannot be accessed outside of it. However, we can pass the value of a variable as an argument to a method, thus binding it to a method's parameter. It makes an outer scope variable now accessible inside the method.
#### Both
This code demonstrates the concept of Local Variable Scope. When a method is defined, the local variables from the outer scope are not accessible within the method. Additionnally, variables initialized within the method are confined to that method's scope and cannot be accessed outside of it. However, we can pass the value of a variable as an argument to a method, thus binding it to a method's parameter. It makes an outer scope variable now accessible inside the method. Furthermore, in a block, things are a bit different. We can access outer scope variables, but any variable initialized inside the block can't be accessed outside of it.
### Variable Shadowing
This code demonstrates the concept of Variable Shadowing. It happens when a variable declared within a block scope has the same name as a variable in an outer scope. The inner variable then shadows the outer variable. Meaning, the outer variable is inaccessible within the block. 
### Variables as Pointers
This code demonstrates the concept of Variables as Pointers. In Ruby, variables don't directly hold values. They act as pointers (or references to memory locations) where values are stored. When variables are assigned, they point to these memory locations. If another variable is assigned the same value, both variables point to the same memory location, effectively sharing the same value.
### Object Mutability
This code demonstrates the concept of Object Mutability. It refers to whether an object's internal state can be changed after it's created. Mutable objects can have their state modified, while immutable objects cannot. Strings, arrays and hashes in Ruby are mutable, meaning their content can be changed without creating a new object. Float, integers, ranges, symbols, booleans and nil, on the other hand, are immutable, so any operation that appears to modify them actually creates a new object.
### Pass by Reference/Pass by Value
This code demonstrates the concept of Pass by Reference/Pass by Value. In Ruby, variables act as pointers, so when they are passed to methods they are actually passing a reference to the object. Changes to those objects with the use of mutating methods within the method will affect their original value. However, Ruby also uses a strategy called 'pass-by-value'. If a new object is assigned within the method, it won't change the original object. This latter strategy is always used for immutable objects (integers, floats, ranges, symbols, booleans, nil).
### Truthiness
This code demonstrates the concept of Truthiness. In Ruby, all values evaluate as true in a boolean context except for `false` and `nil`. Because of this, we can use any type of value in a condition such as the one found in an `if` statement. For example, in Ruby, if we write `if 0` or `if []` the condition evaluates as `true`.

### Output vs Return Values
This code demonstrates the concept of Output vs Return Values. Output is what your program writes to the terminal using methods like `puts` or `print`. Return value, on the other hand, is the value that a method leaves behind, which can then be used in another context. In Ruby, if no return value is explicitly indicated with the `return` keyword, the method will automatically return the result of the last line of code executed within it.
### Side Effects
This code demonstrates the concept of Side Effects. In Ruby, a function has a side effect if it changes the state of something outside its own scope. This could be modifying an external variable, writing to the console, or changing the content of a file.
### Implicit/Explicit Return Value
This code demonstrates the concept of Implicit/Explicit Return Value. In Ruby, a method will automatically return the value of the last line of code executed. This is called an implicit return. If you want to return an earlier value, or make it more clear what a method's return is, you can use the `return` keyword followed by the value you want to return. This is called an explicit return.
### Operator Precedence
This code demonstrates the concept of Operator Precedence. In Ruby, different operators have different precedence. This means that in expressions where multiple operators are present, certain operations will be performed before others. From highest precedence to lowest: Parentheses, Exponentiation, Unary minus and plus, Multiplication Division and Modulus, Addition and Substraction, Comparison operators, Logical AND, Logical OR, Ternary operator and finally Assignement operators.
### Collection Methods
This code demonstrates the concept of Collection Methods. Collections, such as arrays or hashes, have methods (functions pre-built into Ruby) that can operate on them to manipulate data. 
### Call Stack
This code demonstrates the concept of a Call Stack. As a Ruby program runs, it keeps track of what functions are being called in a structure known as a call stack. Each time a method is called, a new frame is pushed onto the stack which contains the function's local variables. When the function exits, its frame is popped from the stack.