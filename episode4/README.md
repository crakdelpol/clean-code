#Functions structure.

##Arguments

what is the correct number of arguments?
Zero is the best,
one is ok,
Two is ok.
Three arguments is the max number.

If you need too much of three arguments create an Object.

No boolean arguments, never do it, create instead 2 function, one call when the argument is true and one when argument is false.
Don't use Output arguments.

Don't pass null value. (same of boolean).

Defense programming is a smells.

### Stepdown rule
Public methods must stay at the top, private stay at the bottom. 

### Switches and cases

It’s hard to make a small switch statement.
Even a switch statement with only two cases is larger than I’d like a single block or function to be.
It’s also hard to make a switch statement that does one thing. 
By their nature, switch statements always do N things. 
Unfortunately we can’t always avoid switch statements, but we can make sure that each switch statement is buried in a low-level class and is never repeated. 
We do this, of course, with polymorphism.

## Functional programming
you call one function with input transform it and return the output

### side effects

Your function promises to do one thing, but it also does other hidden things. 
Sometimes it will make unexpected changes to the variables of its own class. 
Sometimes it will make them to the parameters passed into the function or to system globals. 
In either case they are devious and damaging mistruths that often result in strange temporal couplings and order dependencies.

Temporal couplings are confusing, especially when hidden as a side effect. If you must have a temporal coupling, you should make it clear in the name of the function. In this case we might rename the function checkPasswordAndInitializeSession, though that certainly violates “Do one thing.”

### Command query separation
Functions should either do something or answer something, but not both. Doing both often leads to confusion.

### Tell don't ask

Tell to an object what to do and don't ask any information. 


### structured programming
Every function and every block within a function, should have one entry and one exit.
Following these rules means that there should only be one return statement in a func- tion, no break or continue statements in a loop, and never, ever, any goto statements.

So if you keep your functions small, then the occasional multiple return, break, or continue statement does no harm and can sometimes even be more expressive than the single-entry, single-exit rule. 
On the other hand, goto only makes sense in large functions, so it should be avoided.

#Error handling 

## Error first

## Prefer exception

## Use unchecked exception

The price of checked exceptions is an Open/Closed Principle violation.
If you throw a checked exception from a method in your code and the catch is three levels above, you must declare that exception in the signature of each method between you and the catch.
This means that a change at a low level of the software can force signature changes on many higher levels. 
The changed modules must be rebuilt and redeployed, even though nothing they care about changed.

null is not an error

null is a value


