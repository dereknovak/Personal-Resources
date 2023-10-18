**************************** CONCEPTS ****************************

>Call Stack

>Parallel Assignment

  This example demonstrates Ruby's ability to employ _parallel assignment_, allowing the program to assign values to multiple variables on a single line of code.

>Pass-by-Reference

  This example demonstrates how Ruby appears to handle mutative objects as _pass-by-reference_ when a destructive method is called on them, as it seems that a _reference_ to the original object is used and therefore it _can_ be mutated.  

>Pass-by-Value

  This example demonstrates how Ruby appears to handle mutative objects as _pass-by-value_ when a non-destructive method is called on them, as it seems that a _copy_ of the original object is used and therefore it _cannot_ be mutated.

>Short Circuiting

>Variables as Pointers ***

  This example demonstrates how Ruby employs its variables as _pointers_ to objects in memory.

>Variable Scope

  This example demonstrates how Ruby approaches _variable scope_. 
  ... because a method contains its own, self-contained scope.
  ... A block establishes its own scope that can access local variables initialized outside of it, but not the other way around.
  ... 

>Variable Shadowing

  This example demonstrates how _variable shadowing_ can prevent access to the outer scope of a ____ due to using the same variable names throughout a codebase.



*************************** OPERATIONS ****************************

>Blocks

  ...passed a `do...end`/`{...}` block as an argument. Upon each iteration of the block within method invocation, block parameter `____` is bound to the value of the current element in the calling ____.

>Conditional Statement ***

  A ____- way conditional `if` statement is employed
  Lines ________ employ a conditional `if..else..end` structure.
  ...branch

>Ternary operator

  A ternary operator is employed that checks whether ________. If evaluated as true, ________; otherwise, ________.




**************************** METHODS ****************************

>Integer + - * /

  The ____ method is called on ____ and passed ____ as an argument, returning the sum/difference/product/quotient value ____.

>Kernel#puts

  The `puts` method is invoked and passed the value of ____ as an argument, which outputs ____ and returns nil.

>Integer#times

  ... the iteration number (0..-1)



*************************** GENERAL LANGUAGE ****************************

>Method Invocation

x = object

  On line ____, local variable `x` is initialized and references the ____ object with the value _____.

>Method Calling

x.method(y)

  The ____ method is called on ____ and is passed ____ as an argument.

>Method Variables

def a_method(x)
  x.some_method <=
end

  The ____ method is called on method local variable ____.

>Method Defining

def a_method(x)
  "Something happens"
end

  From lines __ - __, the `____` method is defined with ____ parameter: `____`.

>Parameter Binding



