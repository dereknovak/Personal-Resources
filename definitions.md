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

### Call Stack

  Ruby utilizes a **call stack** to manage the order in which method invocation takes place, adding and removing operations from the top of the stack until the program concludes.

### Method Definition

  A method definition is created using the `def` keyword, followed by a series of code, then ending with `end`. A defined method can include parameters, indicated by variables enclosed within parentheses next to the method name, allowing outside information to be used within the method.

### Method Invocation

  A method, whether defined or included within the Ruby library, can be invoked on an object, performing some kind of action on it. When a method is invoked, it can be passed an argument, if the definition allows, which may affect what gets returned from the method invocation. While most arguments will exist within parentheses at the method's invocation, Ruby's syntactical sugar allows some method arguments to be displayed without them.

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

### Short Circuiting

  As illustrated from this example, **Short circuiting** occurs when a logical operator’s condition is met after the evaluation of its left operand, preventing its right operand from executing.

  Example
  ```Ruby
  puts('This string will output') && puts('This string will not output')
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

  This example illustrates how every expression in Ruby evaluates as true, except for `false` and `nil`.

  Example
  ```Ruby
  if 5                        # This alone evaluates as `true`
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
  a = 'hello'

  1.times do
    a = 'goodbye'
  end

  puts a    # => goodbye
  # Block inner-scope can access outer-scope, therefore `a` was reassigned.
  ```

- Methods

  This example demonstrates how Ruby approaches **variable scope** in regards to methods. A method has its own, self-contained scope, therefore it cannot access local variables initialized outside of its scope, nor the other way around.

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





