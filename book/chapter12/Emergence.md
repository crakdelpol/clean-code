# Emergence

Following the practice of simple design can and does encourage and enable developers to adhere to good principles and patterns that otherwise take years to learn.

Design is "simple" if it follows these rules:

- Runs all tests
- Contains no duplications
- Expresses the intent of the programmer
- Minimizes the number of the classes and methods

### Runs all tests
The systems that aren't testable are not verifiable. Consequently, a system cannot be verified should never be deployed.
Making your system testable pushed you to design class small and simple.
Is easier to test a class that respects SRP. So making your system fully testable help us to create a better design.
Classes with low cohesion and high coupling are hard to tests. So more tests we write the more we will use principles like DIP, interfaces and abstraction to minimize coupling.
Writing tests lead to better design.

### Refactoring 
Once we have tests, we are empowered to keep our code and classes clean.
We do this by incrementally refactoring the code.
The fact that we have these tests eliminates the fear that cleaning up the code will break it.
During refactoring apply there three final rules:
- Eliminate duplication
- Ensure expressiveness
- Minimize the number of classes and method

### No duplication
Duplication is the primary enemy of well-designed system.
Duplication manifest itself in many forms.
- Line of code that are similar.
- Duplication of implementation

Example:
```
int size();
boolean isEmpty();
```

### Expressive
The majority of the cost of a software project is in long-term maintenance.

As systems become more complex, they take more and more time for a developer to understand, and there is an ever greater opportunity for a misunderstanding.

You can express yourself by choosing good names. We want to be able to hear a class or function name and not be surprised when we discover its responsibilities.
You can also express yourself by keeping your functions and classes small. Small classes and functions are usually easy to name, easy to write, and easy to understand.
You can also express yourself by using standard nomenclature. Design patterns, for example, are largely about communication and expressiveness. By using the standard pattern names, such as COMMAND or VISITOR, in the names of the classes that implement those patterns, you can succinctly describe your design to other developers.

Remember, the most likely next person to read the code will be you.

### Minimal classes and methods

Our goal is to keep our overall system small while we are also keeping our functions and classes small. Remember, however, that this rule is the lowest priority of the four rules of Simple Design. So, although it’s important to keep class and function count low, it’s more important to have tests, eliminate duplication, and express yourself.