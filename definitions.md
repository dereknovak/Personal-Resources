# Personal Definitions

Included are my personal definitions and examples of basic Ruby concepts used to help prepare me for the Ruby written and aural assessments.

## Navigation

1. [CONCEPTS](#concepts)
    - [Call Stack](#call-stack)
    - [Method Definition](#method-definition)
    - [Method Invocation](#method-invocation)
    - [Order of Precedence](#order-of-precedence)
    - [Parallel Assignment](#parallel-assignment)
    - [Pass-by-Reference](#pass-by-reference)
    - [Pass-by-Value](#pass-by-value)
    - [Short Circuting](#short-circuiting)
    - [Variables as Pointers](#variables-as-pointers)
    - [Variable Scope](#variable-scope)
    - [Variable Shadowing](#variable-shadowing)
2. [OPERATIONS](#operations)
    - [Blocks](#blocks)
    - [Conditional Statement](#conditional-statement)
    - [Ternary Operator](#ternary-operator)
    - [Explicit Returns](#explicit-returns)
3. [METHODS](#methods)
    - [Numeric Operators](#numeric-operators)
    - [String Operators](#string-operators)
    - [Printing](#printing)
    - [Conversion Methods](#conversion-methods)
    - [#times](#integertimes)
4. [GENERAL LANGUAGE](#general-language)
    - [Variable Assignment](#variable-assignment)
    - [Method Calling](#method-calling)
    - [Method Variables](#method-variables)
    - [Method Defining](#method-defining)
    - [Parameter Binding](#parameter-binding)

## CONCEPTS

### Array

  An array is a data structure made up of an ordered collection of elements. Arrays can exist within other arrays, creating a *nested array*.

  ```ruby
  my_array = ['string', true, 2, 2.5, :symbol, nil]

  nested_arr = [['string', true], ['string', false]]
  ```

### Block

  A block is a section of code delmited by either `do...end` or `{...}` that can be passed as an arugment to a method invocation. A block can include parameters, indicated by variables enclosed within `||`, allowing the method's caller to be used within the block.

  ```ruby
  a.some_method do |parameter|
    "Some code..."
  end

  a.some_method { |parameter|  "Some code..." }
  ```

### Call Stack

  Ruby utilizes a **call stack** to manage the order in which method invocation takes place, adding and removing operations from the top of the stack until the program concludes.

### Frozen Object

  A frozen object cannot be modified. While immutable objects are always frozen, mutable objects can become frozen using the `freeze` method. It's important to note that only the frozen object is frozen; if the collection references other objects, they will not be frozen and can still be modified.

  ```ruby
  arr = ['a', 'b', 'c'].freeze
  arr << 'd'  # => FrozenError: Can't modify a frozen array

  arr[2] << 'd'
  arr  # => ["a", "b", "cd"]
  ```

### Hash

  A hash is a data structure made up of a collection of key-value pairs.

  ```ruby
  my_hash = { :key => 'value',
						  :key2 => 'value2' }

  my_hash = { key: 'value',
						  key2: 'value2' }
  ```

### Method Argument vs Parameter

  Method arguments are objects that get passed into a method invocation. These objects are then bound to the method's parameters, which are defined variables that act as placeholders of variables used within the method. Both are assigned within parentheses; however, arguments exist at the method invocation while parameters exist at the method definition.

  ```ruby
  def my_method(parameter)
    # Some code...
  end

  my_method(argument)
  ```

### Method Chaining

  Method chaining allows a method to be called on the *return value* of a previous method call while on the same line of code. It's important to note that this does not mean that muliple methods are being called on the same object; it's simply a chain of method invocation.

  ```ruby
  a.method1.method2

  str = 'hello'
  str.capitalize.reverse  # => "olleH"
  ```

### Method Definition

  A method definition is created using the `def` keyword, followed by a series of code, then ending with `end`. A defined method can include parameters, indicated by variables enclosed within parentheses next to the method name, allowing outside information to be used within the method.

  ```ruby
  def my_method(parameter)
    # Some code...
  end
  ```

### Method Invocation

  A method, whether defined or included within the Ruby library, can be invoked on an object, performing some kind of action on it. When a method is invoked, it can be passed an argument, if the definition allows, which may affect what gets returned from the method invocation. While most arguments will exist within parentheses at the method's invocation, Ruby's syntactical sugar allows some method arguments to be displayed without them.

### Nested Collection

  A nested collection exists when a collection appears as an element within another collection. Any collection can contain another--an array can contain a hash and vice versa.

  Array
  ```ruby
  arr = [[1, 2], ['a', 'b'], [true, false]]
  arr[1][0]  # => "a"
  ```

  Hash
  ```ruby
  hsh = { a: { a: 1, b: 2}, b: { c: 3, d: 4 } }
  hsh[:b][:d]  # => 4
  ```

  Both
  ```ruby
  arr = [[1, 2], { a: 1, b: 2 }]
  hsh = { a: [1, 2], b: { a: 1, b: 2 } }
  ```

### Order of Precedence

  As illustrated from the example, Ruby follows an **order of precedence** when executing multiple operators within a single line of code. The order is as followed, from highest to lowest precedent:

  1. Parentheses
  2. Exponentiation
  3. Unary + and -
  4. Multiplication *, Division /, and Modulus %
  5. Addition + and Subtraction -
  6. Comparison operators: <, >, <=, >=, ==, !=
  7. Logical AND &&
  8. Logical OR ||
  9. Ternary operator ? :
  10. Assignment operators: =, +=, -=...

  In general, it's best to use parentheses to avoid confusion, as someone reading your code, including yourself, may not have a strong understanding of the order.

### Parallel Assignment

  This example demonstrates Ruby's ability to employ **parallel assignment**, allowing the program to assign values to multiple variables on a single line of code.

  Example
  ```Ruby
  greeting, farewell = 'hello', 'goodbye'

  puts greeting   # => hello
  puts farewell   # => goodbye
  ```

### Pass-by-Reference

  As illustrated from this example, Ruby appears to exhibit a **pass-by-reference** object passing strategy when passing mutable objects to destructive methods. This behavior suggests that the method uses a *reference* to the original object, allowing the original object to be mutated.

  Example
  ```Ruby
  def scream(string)    # `cat` is bound to `string`
    string.upcase!      # `upcase!` called on `string`, mutating caller
  end

  cat = 'meow'          # `cat` initialized
  scream(cat)           # `scream` method invocation
  puts cat              # Value of `cat` mutated, so outputs `MEOW`
  ```

### Pass-by-Value

  As illustrated from this example, Ruby appears to exhibit a **pass-by-value** object passing strategy when passing mutable objects to non-destructive methods. This behavior suggests that the method uses a *copy* of the original object, preventing the original object from being mutated.

  Example
  ```Ruby
  def say(string)       # `cat` is bound to `string`
    string.upcase       # `upcase` called on `string`, only affects method variable
  end

  cat = 'meow'          # `cat` initialized
  say(cat)              # `say` method invocation
  puts cat              # Value of `cat` unchanged, so outputs `meow`
  ```

### PEDAC

  An approach used to solve complex programming problems efficiently.
  
  **P** - [Understand the] Problem

  **E** - Examples/Test Cases

  **D** - Data Structure

  **A** - Algorithm

  **C** - Code

### Selection vs Transformation

  When iterating over a collection, a selective or transformative approach may be used. Transformation returns an altered version of all current elements, while Selection only returns the specific ones.

### Shallow Copy

  A shallow copy, formed by calling the `dup` or `clone` methods on an object, is a duplicate object that is separate from the original; however, any existing nested objects will be shared between both. As a result, changes made to the duplicate object will not affect the original, but ones made to the nested objects will.

  Example
  ```ruby
  arr1 = ['a', 'b', 'c']
  arr2 = arr1.dup
  arr3 = arr1.dup

  arr2.map!(&:upcase)
  p arr1  # => ['a', 'b', 'c']

  arr3.each(&:upcase!)
  p arr1  # => ['A', 'B', 'C']
  ```

### Short Circuiting

  As illustrated from this example, **Short circuiting** occurs when a logical operator’s condition is met after the evaluation of its left operand, preventing its right operand from executing.

  Example
  ```Ruby
  puts('This will output') && puts('This will not output')
  # `puts` returns `nil`, which is falsy
  # Because `&&` requires both operands to be truthy, it short-circuits. 
  ```

### Side Effects

  Methods are said to have **side effects** when more operations are performed than the original intent of the method invocation. While side effects can be helpful, it's best to avoid them to minimize the function that a method serves.

  Example
  ```Ruby
  def get_number
    puts "Enter a number:"    # Printing message to console is a side effect
    number = gets.chomp       # Main purpose is to get a number from user
  ```

### Truthiness

  This example illustrates how every expression in Ruby evaluates as true, except for the boolean object `false` and `nil`.

  Example
  ```Ruby
  if 'false'                  # This alone evaluates as `true`
    puts `This is truthy!`    # Therefore, this branch will always be executed
  else
    puts `This is falsy.`
  end
  ```

### Variables as Pointers

  This example illustrates how Ruby employs its **variables as pointers** to an address space in memory, rather than containing object values within themselves.

  Example
  ```Ruby
  a = 'hello'
  b = a
  a = 'goodbye'

  puts b    # => hello
  # `b` is still 'pointing to' the object `hello`; only `a` was reassigned.
  ```

### Variable Scope

- Blocks

  This example illustrates how Ruby approaches **variable scope** in regards to blocks. A block establishes its own scope that can access local variables initialized outside of it, but not the other way around.

  Example (block)
  ```Ruby
  a = 1

  loop do
    a = 2
    b = 10
  end

  puts a    # => 2
  puts b    # => NameError
  # Block inner-scope can access outer-scope, therefore `a` was reassigned.
  # Block outer-scope cannot access inner-scope, therefore `NameError`.
  ```

- Methods

  This example demonstrates how Ruby approaches **variable scope** in regards to methods. A method establishes its own, self-contained scope, therefore it cannot access local variables initialized outside of its scope, nor the other way around.

  Example
  ```Ruby
  a = 'hello'

  def say
    a = 'goodbye'
  end

  puts a    # => hello
  # Methods have their own, self-contained scope, therefore `a` was not reassigned.
  ```

### Variable Shadowing

  This example illustrates how **variable shadowing** can prevent access to a local variable outside the scope of a block due to using that same variable name as its parameter. When searching for a local variable from within a block, Ruby first looks within its scope, then moves outward, returning the first reference it finds.

  Example

  ```Ruby
  string = 'Hello'      # local variable `string` is initialized

  1.times do |string|   # block parameter `string` is initialized
    puts string         # `string` references the parameter first, therefore `0` is output
  end  
  ```

## OPERATIONS

### Blocks

  ...passed a `do...end`/`{...}` block as an argument. Upon each iteration of the block within method invocation, block parameter `____` is bound to the value of the current element in the calling ____.

### Conditional Statement ***

  Lines ________ employ a conditional `if..else..end` structure.

  ...`if`/`elsif`/`else` branch

### Ternary operator

  A ternary operator is employed that checks whether ________. If evaluated as `true`, ________; otherwise, ________.

  Example
  ```Ruby
  # Returning the negative version of a number
  num < 0 ? num : -num
  ```

### Explicit returns

  When an explicit `return` command is utilized, Ruby will immediately *return* its evaluated argument and *terminate* the method, preventing any further expressions from processing.

  ```Ruby
  def best_meal
    return 'Breakfast'  # Terminates the method
    'Lunch'             # Not evaluated
    'Dinner'            # Not evaluated
  end
  ```

## METHODS

### Iterative Methods

- `each`

  The `each` method iterates through a collection, returning the calling collection after iteration is complete.

  ```ruby
  [1, 2, 3].each do |num|
    num + 2
  end  
  ```

  The `each` method is called on `[1, 2, 3]` and gets passed a `do...end` block as an argument, binding each element to the block's parameter `num` throughout iteration. `each` will always return the calling object, so although code is executed within the block, `each` will return `[1, 2, 3]` regardless.

- `map` / `map!`

  The `map` method iterates through a collection, returning a new array that contains transformed elements from the calling collection based upon the return value of the last line in its block.

  ```ruby
  [1, 2, 3].map do |num|
    num + 2
  end
  ```

  The `map` method is called on `[1, 2, 3]` and gets passed a `do...end` block as an argument, binding each element to the block's parameter `num` throughout iteration. Upon each iteration of the block, the sum of the current value of `num` and `2` is returned, transforming each element to 2 more than its current value. As a result, the new array `[3, 4, 5]` is returned from `map`.

- `select` / `select!`

  The `select` method iterates through a collection, returning a new collection that contains only the elements from the calling collection that evaluate as true based upon the return value of the last line of its block.

  ```ruby
  [1, 2, 3].select do |num|
    num > 1
  end
  ```

  The `select` method is called on `[1, 2, 3]` and gets passed a `do...end` block as an argument, binding each element to the block's parameter `num` throughout iteration. Upon each iteration of the block, a boolean is returned on whether or not the current value of `num` is greater than `1`. Because `2` and `3` both return `true`, and `select` returns a new array containing only the truthy elements, `[2, 3]` is returned from `select`.

- `all?`

  The `all?` method iterates through a collection, only returning `true` if all elements evaluate as true based upon the return value of the last line of its block; otherwise, `all?` returns `false`.

  ```ruby
  [1, 2, 3].all? do |num|
    num > 1
  end
  ```

  The `all?` method is called on `[1, 2, 3]` and gets passed a `do...end` block as an argument, binding each element to the block's parameter `num` throughout iteration. Upon each iteration of the block, a boolean is returned on whether the current value of `num` is greater than `1`. Because `1` returns `false`, and `all?` only returns `true` if all elements return a truthy value, `false` is returned from `all?`.

- `any?`

  The `any?` method iterates through a collection, returning `true` if any of the elements evaluate as true based upon the return value of the last line of its block. Once a truthy return is evaluated, the iteration will short-circuit, stopping any further block iterations from executing.

- `include?`

  The `include?` method iterates through a collection, returning `true` if its argument value is present within the collection and `false` otherwise.

### String Methods

- `chars`

  The `chars` method returns an array object that contains characters within the string represented as individual elements.

  ```ruby
  'abc'.chars
  ```

  The `chars` method is called on `'abc'`, returning an array with each character as a string object element.
  
  The `chars` method is called on `'abc'`, returning the array `["a", "b", "c"]`.

- `concat`

  The `concat` method destructively appends its argument object onto the calling object.

  ```ruby
  'hello'.concat(' world!')
  ```

  The destructive `concat` method is called on `'hello'`, appending `' world!'` onto it and returning the mutated object `'hello world!'`.

- `downcase` / `downcase!`

  ```ruby
  'HELLO'.downcase
  ```

  The `downcase` method is called on `'HELLO'`, returning a new string `'hello'` by switching all characters to lowercase.

- `freeze`

  ```ruby
  [1, 2, 3].freeze
  ```

  The `freeze` method is called on `[1, 2, 3]`, preventing the array object from begin mutated.

- `replace`

  The `replace` method destructively replaces elements within the calling object with the argumented elements.

  ```ruby
  [1, 2, 3].replace([4, 5])
  ```

  The `replace` method is called on `[1, 2, 3]`, replacing the elements with elements from the argumented array `[4, 5]`.


- `reverse` / `reverse!`

  ```ruby
  [1, 2, 3].reverse
  ```

  The `reverse` method is called on `[1, 2, 3]`, reversing the elements and returning the new array `[3, 2, 1]`.

- `size`

  ```ruby
  [1, 2, 3].size
  ```

  The `size` method is called on `[1, 2, 3]`, returning an integer representing the size of the array, which contains `3` elements.

- `slice` / `slice!`

- `split`

- `strip` / `strip!`

  The `strip` method returns a new string with all leading and trailing whitespace removed.

- `upcase` / `upcase!`

### Array Methods

- `each_with_index`

  The `each_with_index` method iterates through a collection, passing both the element and its corresponding index value into the block using the block's parameters.

- `each_with_object`

  The `each_with_object` method iterates through a collection, returning its argument object with elements pushed inside throughout iteration of its block.

- `fetch`

  The `fetch` method returns an element at the index location of its argument, throwing an exception if that index value is outside of the range of the calling collection.

- `first`

  The `first` method returns the number of elements from the beginning of an array, specified by its argument.

- `join`

  The `join` method returns a string with elements of the calling array concatenated together.

- `last`

  The `last` method returns the number of elements from the end of an array, specified by its argument.

- `partition`

  The `partition` method iterates through a collection, returning a nested array with truthy and falsy elements divided based upon the return value of the last line of its block.

- `pop`

  The `pop` method destructively removes and returns the last element of an array.

- `push`

  The `push` method destructively appends its argument value to the calling array.

- `reverse` / `reverse!`

  The `reverse` method returns a new collection with elements sorted in reverse order.

- `shift`

  The `shift` method destructively removes and returns the first element of an array.

- `slice` / `slice!`

  The `slice` method returns a range of elements based upon its argument value.

- `sort` / `sort!`

  The `sort` method returns a new array with elements sorted from smallest to largest value.

- `unshift`

  The `unshift` method destructively prepends its argument value onto the calling array.

### Hash Methods

- `each_key`

  The `each_key` method iterates through the caller's keys and returns the calling hash.

- `each_value`

  The `each_value` method iterates through the caller's values and returns the calling hash.

- `empty?`

  The `empty?` method returns `true` if the calling object contains no characters or elements.

- `key`

  The `key` method returns the first-found key that is associated with the argument value.

- `key?`

  The `key?` method iterates through a hash, returning a boolean on whether or not the calling hash includes the argument key.

- `keys`

  The `keys` method returns an array containing all keys of the calling hash indicated as elements.

- `value?`

  The `value?` method iterates through a hash, returning a boolean on whether or not the calling hash includes the argument value.

- `values`

  The `values` method returns an array containing all values of the calling hash, indicated as elements.

### Numeric Operators

- Sum

  ```Ruby
  9 + 3
  ```

  The `+` numeric operator is called on integers `9` and `3`, returning the sum value `12`.

- Difference

  ```Ruby
  9 - 3
  ```

  The `-` numeric operator is called on integers `9` and `3`, returning the difference value `6`.

- Product

  ```Ruby
  9 * 3
  ```

  The `*` numeric operator is called on integers `9` and `3`, returning the product value `27`.

- Quotient

  ```Ruby
  9 / 3
  ```

  The `/` numeric operator is called on integers `9` and `3`, returning the quotient value `3`.

- Modulo

  ```Ruby
  9 % 3
  ```

  The `%` numeric operator is called on integers `9` and `3`, returning the modulus (remainder) value `0`.

- Squared

  ```Ruby
  9**3
  ```

  The `**` numeric operator is called on the integers `9` and `3`, returning the squared value `729`.

- Divmod

  ```Ruby
  9.divmod(3)
  ```

  The `divmod` method is called on the integer `9` and gets passed `3` as an argument, returning the quotient and modulus values `[3, 0]` as an array.

### String Operators

- Concatenation +

  ```Ruby
  greeting = 'hello'
  greeting += '!'
  ```

  The `+` string operator is called on local variable `greeting` and string object `'!'`, concatenating the values and reassigning its return value `'hello!'` to `greeting`.

- The Shovel <<

  ```Ruby
  greeting = 'hello'
  greeting << '!'
  ```

  The `<<` operator is called on local variable `greeting` and is passed the string object `'!'` as an argument. `'!'` is destructively concatenated onto the value of `greeting`, which mutates the object to `'hello!'`.

- Times *

  ```Ruby
  greeting = 'hello'
  greeting *= 5
  ```

  The `*` string operator is called on local variable `greeting` and integer `5`, returning '`hellohellohellohellohello'` as a new string and reassigning it to `greeting`.

### Printing

- #puts

  ```Ruby
  puts 'Hello World'
  ```

  The `puts` method is invoked and is passed a string object with the value `'Hello World'` as an argument, which outputs `Hello World` and returns `nil`.

- #p

  ```Ruby
  a = `Hello World`
  p a
  ```

  The `p` method is invoked and is passed the value of local variable `a` as an argument, which outputs and returns `'Hello World'`.

### Conversion Methods

- #to_s

  ```Ruby
  num = 42
  num.to_s
  ```

  The `to_s` method is called on local variable `num`, converting its value to a string object, which returns `'42'`.

- #to_i

  ```Ruby
  str = '42'
  str.to_i
  ```

  The `to_i` method is called on local variable `str`, converting its value to an integer, which returns `42`.

- #to_f

  ```Ruby
  pi = '3.14'
  pi.to_f
  ```

  The `to_f` method is called on local variable `pi`, converting its value to a float, which returns `3.14`.

- #to_sym

  ```Ruby
  animal = `dog`
  animal.to_sym
  ```

  The `to_sym` method is called on local variable `animal`, converting its value to a symbol, which returns `:dog`

- #to_a

- #to_h


### Integer#times

  ... the iteration number (0..-1)



## GENERAL LANGUAGE

### Variable Assignment

- String

   ```Ruby
  str = 'Hello'
  ```

  Local variable `str` is initialized and references a string object with the value `'Hello'`.


- Integer

  ```Ruby
  num = 5
  ```

  Local variable `num` is initialized and references an integer object with the value `5`.

- Float

  ```Ruby
  num = 5.0
  ```

  Local variable `num` is initialized and references a float object with the value `5.0`.

- Boolean

  ```Ruby
  answer = true
  ```

  Local variable `answer` is initialized and references a boolean object with the value `true`.

- Array

  ```Ruby
  numbers = [1, 2, 3]
  ```

  Local variable `numbers` is initialized and references an array of integers. The array contains 3 elements that reference the values `1`, `2`, and `3`.

  Local variable `numbers` is initialized and references an array of integers with the value `[1, 2, 3]`

- Hash

  ```Ruby
  animal_sounds = { cat: 'meow',
                    dog: 'woof' }
  ```
  
  Local variable `animal_sounds` is initialized and references a hash of key-value pairs. The symbol object `cat` is paired to a string object with the value `'meow'` and the symbol object `dog` is paired to a string object with the value `'woof'`.

### Method Calling

```Ruby
x.method(y)
```

  The `____` method is called on `____` and gets passed `____` as an argument.

### Method Variables

```Ruby
def a_method(x)
  x.some_method <=
end
```

  The `____` method is called on method local variable `____`.

### Method Defining

```Ruby
def a_method(x)
  "Something happens"
end
```

  From lines __ - __, the `____` method is defined with ____ parameter: `____`.

### Parameter Binding

  The value of `____` is then bound to the method's parameter, `____`.





