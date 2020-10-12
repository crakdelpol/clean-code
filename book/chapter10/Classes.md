# Classes

### The "stepdown" rule
A class should begin with a list of variables. Public static constant should come first, then private static variables, followed by private instance variables.
Public functions should follow the list of variables. The lasts are private functions.

The first rule of classes is that they should be small.
With functions, we measured size by counting physical size. With classes, we use a different measure: we count responsibilities.

### The single responsibility principle

The SRP states that a class or module should have one, and only one, reason to change.

We want our systems to be composed of many small classes, not a few large ones. Each small class encapsulates a single responsi- bility, has a single reason to change, and collaborates with a few others to achieve the desired system behaviors.

### Cohesion

Classes should have a small number of instance variables. Each of the methods of a class should manipulate one or more of those variables. In general the more variables a method manipulates the more cohesive that method is to its class. A class in which each variable is used by each method is maximally cohesive.

### Organizing for Change
For most systems, change is continual. Every change subjects us to the risk that the remainder of the system no longer works as intended. In a clean system we organize our classes so as to reduce the risk of change.