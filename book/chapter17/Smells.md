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
Any function or class should implement the behaviors that another programmer could reasonably expect("The principle of The Least Surprise").

#### Incorrect behavior at the boundaries

Every boundary condition, every corner case, every quirk and exception represents something that can confound an elegant and intuitive algorithm.
Look for every boundary condition and write a test for it.

#### Overridden safeties
Turning off certain compiler warning may help you get build to succeed, but at the risk of endless debugging sessions.

#### Duplication
Every time you see duplication in the code, it represents a missed opportunity for abstraction.
The most obvious form of duplication is when you have clumps of identical code. These should be replaced with simple method.
A more form is the switch/case or if/else chain that appears again and again. These should be replaced with polymorphism.
Most design patterns are simply well-know ways to eliminate duplication.

#### Code at wrong level of abstraction
It is important to create abstractions that separate higher level general concepts from lower level detailed concepts. Sometimes we do this by creating abstract classes to hold the higher level concepts and derivatives to hold the lower level concepts. When we do this, we need to make sure that the separation is complete. We want all the lower level concepts to be in the derivatives and all the higher level concepts to be in the base class.

Good software design requires that we separate concepts at different levels and place them in different containers.
 
#### Base classes depending on their derivatives

Base classes should know nothing about their derivatives.

#### Too much information
Well-defined modules have very small interfaces that allow you to do a lot with a little.
A well-defined interface does not offer very many functions to depend upon, so coupling is low.

Hide your data. Hide your utility functions. Hide your constants and your temporaries. Don’t create classes with lots of methods or lots of instance variables.

#### Dead code
When you find dead code, do the right thing. Delete it from the system.

#### Vertical separation
Variables and function should be defined close to where they are used. Local variables should be declared just above their first usage and should have a small vertical scope. We don’t want local variables declared hundreds of lines distant from their usages.
Private functions should be defined just below their first usage.

#### Inconsistency

If you do something a certain way, do all similar things in the same way

#### Clutter
Variables that are not used, functions that are never called, comments that add no information, and so forth. All these things are clutter and should be removed.

#### Artificial coupling 
artificial coupling is a coupling between two modules that serves no direct purpose. It is a result of putting a variable, constant, or function in a temporarily convenient, though inappropriate, location.

#### Feature envy
The methods of a class should be interested in the variables and functions of the class they belong to, and not the variables and functions of other classes.

#### Selector arguments
Selector arguments are just a lazy way to avoid splitting a large function into several smaller functions. 

#### Obscured intent
We want code to be as expressive as possible. Run-on expressions, Hungarian notation, and magic numbers all obscure the author’s intent.

#### Misplaced Responsibility
One of the most important decisions a software developer can make is where to put code.
Code should be placed where a reader would naturally expect it to be.

#### Inappropriate static
In general, you should prefer nonstatic methods to static methods. When in doubt, make the function nonstatic. If you really want a function to be static, make sure that there is no chance that you’ll want it to behave polymorphically.

#### Use explanatory variables
One of the more powerful ways to make a program readable is to break the calculations up into intermediate val- ues that are held in variables with meaningful names.

#### Function names should say what they do
If you have to look at the implementation (or documentation) of the function to know what it does, then you should work to find a better name or rearrange the functionality so that it can be placed in functions with better names.

#### Understand the algorithm
You think you know the right algorithm for something, but then you wind up fiddling with it, prodding and poking at it, until you get it to “work.” How do you know it “works”? Because it passes the test cases you can think of.
Before you consider yourself to be done with a function, make sure you understand how it works. It is not good enough that it passes all the tests. You must know that the solution is correct.
Often the best way to gain this knowledge and understanding is to refactor the function into something that is so clean and expressive that it is obvious how it works.

#### Make logical dependencies physical
If one module depends upon another, that dependency should be physical, not just logical.
Rather, it should explicitly ask that module for all the information it depends upon.

Example:
```
public class HourlyReporter {
    private HourlyReportFormatter formatter;
    private List<LineItem> page;
    private final int PAGE_SIZE = 55;

    public HourlyReporter(HourlyReportFormatter formatter) { 
        this.formatter = formatter;
        page = new ArrayList<LineItem>();
    }

    public void generateReport(List<HourlyEmployee> employees) {
        for (HourlyEmployee e : employees) {
            addLineItemToPage(e);
            if (page.size() == PAGE_SIZE)
                printAndClearItemList(); 
        }
        if (page.size() > 0)
            printAndClearItemList();
    }

    private void printAndClearItemList() {
        formatter.format(page); page.clear();
    }

    private void addLineItemToPage(HourlyEmployee e) {
        LineItem item = new LineItem();
        item.name = e.getName();
        item.hours = e.getTenthsWorked() / 10;
        item.tenths = e.getTenthsWorked() % 10;
        page.add(item); 
    }

    public class LineItem {
        public String name;
        public int hours;
        public int tenths;
    }
}
``` 
The fact that PAGE_SIZE is declared in HourlyReporter represents a misplaced responsibility that causes HourlyReporter to assume that it knows what the page size ought to be. Such an assumption is a logical dependency. HourlyReporter depends on the fact that HourlyReportFormatter can deal with page sizes of 55. If some implementation of HourlyReportFormatter could not deal with such sizes, then there would be an error.


#### Prefer polymorphism to if/else or switch/case

There may be no more than one switch statement for a given type of selection. The cases in that switch statement must create polymorphic objects that take the place of other such switch statements in the rest of the system.