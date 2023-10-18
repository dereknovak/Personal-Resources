# Personal Definitions

Navigation

1. [CONCEPTS](#concepts)
    - [Call Stack](#call-stack)
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
3. [METHODS](#methods)
    - [+ - * /](#integer)
    - [#puts](#kernelputs)
    - [#times](#integertimes)
4. [GENERAL LANGUAGE](#general-language)
    - [Variable Assignment](#variable-assignment)
    - [Method Calling](#method-calling)
    - [Method Variables](#method-variables)
    - [Method Defining](#method-defining)
    - [Parameter Binding](#parameter-binding)

## CONCEPTS

### Call Stack

  Ruby utilizes a 'call stack' to manage the order in which method invocation takes place, adding and removing operations from the top of the stack until the program concludes.

### Parallel Assignment

  This example demonstrates Ruby's ability to employ _parallel assignment_, allowing the program to assign values to multiple variables on a single line of code.

  Example
  ```Ruby
  greeting, farewell = 'hello', 'goodbye'

  puts greeting   # => hello
  puts farewell   # => goodbye
  ```

### Pass-by-Reference

  This example demonstrates how Ruby appears to handle mutative objects as _pass-by-reference_ when a destructive method is called on them, as it seems that a _reference_ to the original object is used and therefore it _can_ be mutated.

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

  This example demonstrates how Ruby appears to handle mutative objects as _pass-by-value_ when a non-destructive method is called on them, as it seems that a _copy_ of the original object is used and therefore it _cannot_ be mutated.

  Example
  ```Ruby
  def say(string)       # `cat` is bound to `string`
    string.upcase       # `upcase` called on `string`, only affects method variable
  end

  cat = 'meow'          # `cat` initialized
  say(cat)              # `say` method invocation
  puts cat              # Value of `cat` unchanged, so outputs `meow`
  ```

### Short Circuiting

  This example demonstrates how conditional statements in Ruby will _short-circuit_ once a condition is met, exiting the statement before all code can be executed.

  Example
  ```Ruby
  is_ok = true || some_method
  # If `is_ok` is evaluated `true`, `some_method` will not be invoked.
  ```

### Side Effects

  Methods are said to have _side effects_ when more operations are performed than the original intent of the method invocation. While side effects can be helpful, it's best to avoid them to minimize the function that a method serves.

  Example
  ```Ruby
  def get_number
    puts "Enter a number:"    # Printing message to console is a side effect
    number = gets.chomp       # Main purpose is to get a number from user
  ```

### Variables as Pointers ***

  This example demonstrates how Ruby employs its variables as _pointers_ to an address space in memory, rather than containing object values within themselves.

  Example
  ```Ruby
  a = 'hello'
  b = a
  a = 'goodbye'

  puts b    # => hello
  # `b` is still 'pointing to' the object `hello`; only `a` was reassigned.
  ```

### Variable Scope

  This example demonstrates how Ruby approaches _variable scope_ in regards to ____. (blocks/methods/etc)

  ... because a method contains its own, self-contained scope.

  ... A block establishes its own scope that can access local variables initialized outside of it, but not the other way around.

  Example (method)
  ```Ruby
  a = 'hello'

  def say
    a = 'goodbye'
  end

  puts a    # => hello
  # Methods have their own, self-contained scope, therefore `a` was not reassigned.
  ```

  Example (block)
  ```Ruby
  a = 'hello'

  1.times do
    a = 'goodbye'
  end

  puts a    # => goodbye
  # Block inner-scope can access outer-scope, therefore `a` was reassigned.
  ```


### Variable Shadowing

  This example demonstrates how _variable shadowing_ can prevent access to the outer scope of a block due to using the same variable names throughout a codebase. When searching for a local variable, Ruby looks within the block's scope first, then moves outward, returning the first reference it finds.

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

## METHODS

### Integer + - * /

  The `____` method is called on `____` and passed `____` as an argument, returning the sum/difference/product/quotient value `____`.

### Kernel#puts

  The `puts` method is invoked and passed the value of `____` as an argument, which outputs `____` and returns nil.

### Integer#times

  ... the iteration number (0..-1)



## GENERAL LANGUAGE

### Variable Assignment

```Ruby
x = object
```

  On line ____, local variable `____` is initialized and references the ____ object with the value `_____`.

### Method Calling

```Ruby
x.method(y)
```

  The `____` method is called on `____` and is passed `____` as an argument.

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





