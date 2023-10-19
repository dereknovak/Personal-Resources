### Numbers

### Integers

  ```Ruby
  num = 5
  ```

  Local variable `num` is initialized and references an integer object with the value `5`.

### Floats

  ```Ruby
  num = 5.0
  ```

  Local variable `num` is initialized and references a float object with the value `5.0`

### Strings

  ```Ruby
  str = 'Hello'
  ```

  Local variable `str` is initialized and references a string object with the value `Hello`.

### Interpolation of Strings

  ```Ruby
  str = 'string'
  puts "This is #{str} interpolation!"
  ```

  The value of local variable `str` is interpolated into the string object `"This is #{str} interpolation."`, which is passed as an argument to the `puts` method invocation, outputting `This is string interpolation.`

### Truthiness

  ```Ruby
  if 5
    puts 'This is truthy!'
  else
    puts 'This is falsy.'
  end
  ```

  On line 1, an `if...else...end` conditional sequence is employed, which checks whether the integer `5` is considered 'truthy'. Because Ruby evalutates everything except `nil` and `false` as `true`, the `if` branch on line 2 will always be executed, passing `'This is truthy!'` as an argument to the `puts` method, and outputting `This is truthy!`.

# Falsiness

  ```Ruby
  x = 5

  if x < 0
    puts 'This is truthy!'
  else
    puts 'This is falsy.'
  end
  ```

  On line 1, local variable `x` is initialized and references an integer objects with the value `5`.
  From lines 3 - 7, the conditional `if...else...end` sequence is employed, which checks whether the value of `x` is less than the integer `0`. Because `5` is _not_ less than `0`, it's evaluated as `false` and follows the `else` branch. Here, the string object `'This is falsy.'` is passed an an argument to the `puts` method, which outputs `This is falsy.`

### Nil

### Arrays

- Initialization
  ```Ruby
  numbers = [1, 2, 3]
  ```

  Local variable `numbers` is initialized and references an array of integers with the value `[1, 2, 3]`

- Common calls
  ```Ruby
  second_index = numbers[1]
  ```

  The `[]` method is called on local variable `numbers` and is passed the integer `1` as an argument. This returns the _second_ index value within its referenced array--the integer `2`, and assigns its value to local variable `second_index`.

### Hashes

- Inititalization
  ```Ruby
  animal_sounds = { cat: 'meow',
                    dog: 'woof' }
  ```

  Local variable `animal_sounds` is initialized and references a hash of key-value pairs. The symbol object `cat` is pair to a string object with the value `'meow'` and the symbol object `dog` is paired to a string object with the value `'woof'`.

- Common calls
  ```Ruby
  
  ```

### Array#size



### Array#push

### Array#pop

### Numeric Operators (+ - * / % divmod **)

### String Operators (+ *)

### Conditional Operators (== != < > <= >= ternary)

### Logical Operators (! && ||)

### Operator precedence


### Mutability

### Immutability

### Constants

### Local variables and Constant Names

### Initialization and Reassignment

### Variable Scope (methods)

### Variable Scope (blocks)

### Variables as Pointers

### Variable Shadowing

### loop do

### While loop

### Until loop

### For i in loop

### puts

### Method Definition

### Method Invocation

### Default Parameters

### Implicit Return value

### Explicit return value

### Parameter

### Arguments

### Output vs Return

### Side Effects

### Pass-by-Reference

### Pass-by-Value

### Call Stack

### Expression and Return
