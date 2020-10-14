# Smells and Heuristics

### Comments

#### Inappropriate information
It is inappropriate for a comment to hold information better held in a different kind of system.
Comments should be reserved for a technical notes about the code and design.

#### Obsolete comment
It is best not to write a comment that will become obsolete.

#### Redundant comment 
A comment is redundant if it describes something that adequately describes itself.
```
i++; // increment i
``` 

#### Poorly written comment
If you are going to write a comment take the time to make sure it is the best comment you can write.

#### Commented-out code
Who knows how old it is? When you se Commented-out code, delete it!

### Environment

#### Build requires more than one step
Building a project should be a single trivial operation.
You should be able to check out the system with one simple command and then issue one other simple command to build it.

#### Tests require more than one step
You should be able to run all the unit tests with one single command.

### Functions

#### Too many arguments
Functions should have a few arguments. No arguments is best, follow by one, two, three. More than three should be avoided.

#### Output arguments
Output arguments are counterintuitive. Readers expect arguments to be inputs, not outputs.

#### Flag arguments
Boolean arguments loudly declare that the function does more than one thing. 

#### Dead functions
Methods that are never called should be discarded.

### General
#### Multiple languages in one source files
The ideal id for a source file to contain one, and only one, language. Realistically, we will probably have to use more than one. But we should take pains to minimize both the number and extent of extra languages in our source files.

#### Obvious behavior is unimplemented
Any function or class should implement the behaviors that another programmer could reasonably expect("The principle of Least Surprise").

#### Incorrect behavior at the boundaries

Every boundary condition, every corner case, every quirk and exception represents something that can confound an elegant and intuitive algorithm.
Look for every boundary condition and write a test for it.

#### Overridden safeties
Turning off certain compiler warning may help you get build to succeed, but at the risk of endless debugging sessions.

#### Duplication
Every time you see duplication in the code, it represents a missed opportunity for abstraction.
The most obvious form of duplication is when you have clumps of identical code. These should be replaced with simple method.
A more form is the swith/case or if/else chain that appears again and again. These should be replaced with polymorphism.
Most design patterns are simply well-know ways to eliminate duplication.

#### Code at wrong level of abstraction
It is important to create abstractions that separate higher level general concepts from lower level detailed concepts. Sometimes we do this by creating abstract classes to hold the higher level concepts and derivatives to hold the lower level concepts. When we do this, we need to make sure that the separation is complete. We want all the lower level concepts to be in the derivatives and all the higher level concepts to be in the base class.

Good software design requires that we separate concepts at different levels and place them in different containers.
 
#### Base classes depending on their derivatives

Base classes should know nothing about their derivatives.

#### Too much information
Well-defined modules have very small interfaces that allow you to do a lot with a little.
A well-defined interface does not offer very many func- tions to depend upon, so coupling is low.

Hide your data. Hide your utility functions. Hide your constants and your temporaries. Don’t create classes with lots of methods or lots of instance variables.

#### Dead code
When you find dead code, do the right thing. Delete it from the system.

#### Vertical separation
Variables and function should be defined close to where they are used. Local variables should be declared just above their first usage and should have a small vertical scope. We don’t want local variables declared hundreds of lines distant from their usages.
Private functions should be defined just below their first usage.

#### Inconsistency

If you do something a certain way, do all similar things in the same way

#### Clutter
Variables that aren’t used, functions that are never called, comments that add no information, and so forth. All these things are clutter and should be removed.

