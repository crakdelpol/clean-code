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

#### Follow standard conventions
Every team should follow a coding standard based on common industry norms.

#### Replace magic numbers with named constants
In general, it is a bad idea to have raw numbers in your code. You should hide them behind well-named constants.

#### Be precise
When you make a decision in your code, make sure you make it precisely. Know why you have made it and how you will deal with any exceptions.
Ambiguities and imprecision in code are either a result of disagreements or laziness. In either case they should be eliminated.

#### Structure over convention
Enforce design decisions with structure over convention.
For example, switch/cases with nicely named enumerations are inferior to base classes with abstract methods.

#### Encapsulate conditionals
Boolean logic is hard enough to understand without having to see it in the context of an if or while statement.

For example:
``` if (shouldBeDeleted(timer))``` 
is preferable to:
``` if (timer.hasExpired() && !timer.isRecurrent())``` 


#### Avoid negative conditionals
Negatives are just a bit harder to understand than positives. So, when possible, conditionals should be expressed as positives.

#### Functions should do one thing
Functions of this kind do more than one thing, and should be converted into many smaller functions, each of which does one thing.

#### Hidden temporal couplings
Temporal couplings are often necessary, but you should not hide the coupling.

Example: 

```
public class MoogDiver { 
    Gradient gradient; 
    List<Spline> splines;
    public void dive(String reason) { 
        saturateGradient(); 
        reticulateSplines(); 
        diveForMoog(reason);
    }
}
```
The order of the three functions is important. You must saturate the gradient before you can reticulate the splines, and only then can you dive for the moog. Unfortunately, the code does not enforce this temporal coupling. Another programmer could call reticulate- Splines before saturateGradient was called, leading to an UnsaturatedGradientException. A better solution is:
```
public class MoogDiver { 
    Gradient gradient; 
    List<Spline> splines;

    public void dive(String reason) {
        Gradient gradient = saturateGradient(); 
        List<Spline> splines = reticulateSplines(gradient); 
        diveForMoog(splines, reason);
    }
}
```
Note that I left the instance variables in place. I presume that they are needed by pri- vate methods in the class. Even so, I want the arguments in place to make the temporal coupling explicit.

#### Don't be arbitrary
Have a reason for the way you structure your code, and make sure that reason is communicated by the structure of the code. If a structure appears arbitrary, others will feel empowered to change it. 
Public classes that are not utilities of some other class should not be scoped inside another class. The convention is to make them public at the top level of their package.

#### Encapsulate boundary conditions

Boundary conditions are hard to keep track of. Put the processing for them in one place.

```
if(level + 1 < tags.length) {
    parts = new Parse(body, tags, level + 1, offset + endTag);
    body = null;
}
```
Becomes
```
int nextLevel = level + 1; 
if(nextLevel < tags.length) {
    parts = new Parse(body, tags, nextLevel, offset + endTag);
    body = null; 
}
```

#### Functions should descend only ine level of abstraction
The statements within a function should all be written at the same level of abstraction.

example
```
public String render() throws Exception {
    StringBuffer html = new StringBuffer("<hr"); if(size > 0)
    html.append(" size=\"").append(size + 1).append("\""); html.append(">");
    return html.toString(); 
}
```

This method is mixing at least two levels of abstraction. The first is the notion that a horizontal rule has a size. The second is the syntax of the HR tag itself. This code comes from the HruleWidget module in FitNesse. This module detects a row of four or more dashes and converts it into the appropriate HR tag. The more dashes, the larger the size.

```
public String render() throws Exception {
    HtmlTag hr = new HtmlTag("hr"); if (extraDashes > 0)
    hr.addAttribute("size", hrSize(extraDashes)); return hr.html();
}
private String hrSize(int height) {
    int hrSize = height + 1;
    return String.format("%d", hrSize); 
}
```

This change separates the two levels of abstraction nicely. 
The render function simply con- structs an HR tag, without having to know anything about the HTML syntax of that tag. 
The HtmlTag module takes care of all the nasty syntax issues.

#### Keep configurable data at high levels

The configuration constants reside at a very high level and are easy to change.
They get passed down to the rest of the application. 

#### Avoid transitive navigation

Rather, we want our immediate collaborators to offer all the services we need. We should not have to roam through the object graph of the system, hunting for the method we want to call. Rather, we should simply be able to say:
```myCollaborator.doSomething().```

### Chose descriptive names
Make sure the name is descriptive.
Names in software are 90 percent of what make software readable. You need to take the time to choose them wisely and keep them relevant. Names are too important to treat carelessly.

#### Choose names at the appropriate level of abstraction
Don’t pick names that communicate implementation;
```
public interface Modem {
    boolean dial(String phoneNumber); 
    boolean disconnect();
    boolean send(char c);
    char recv();
    String getConnectedPhoneNumber();
}
```
```
public interface Modem {
    boolean connect(String connectionLocator); 
    boolean disconnect();
    boolean send(char c);
    char recv();
    String getConnectedLocator();
}
```

Now the names don’t make any commitments about phone numbers. They can still be used for a phone numbers, or they could be used for any other kind of connection strategy.

#### Use standard nomenclature where possible
Names are easier to understand if they are based on existing convention or usage.
The more you can use names that are overloaded with special meanings that are relevant to your project, the easier it will be for readers to know what your code is talking about.

#### Unambiguous names
Choose names that make the workings of a function or variable unambiguous

#### Use long names for long scopes
The length of a name should be related to the length of the scope. You can use very short variable names for tiny scopes, but for big scopes you should use longer names.

#### Avoid encodings
Names should not be encoded with type or scope information.

#### Names should describe side-effects

Names should describe everything that a function, variable, or class is or does. Don’t hide side effects with a name.

#### Insufficient tests

#### Use a coverage tool!

#### An ignored test is a question about an ambiguity

#### Test boundary conditions

#### Exhaustively test near bugs

#### Patterns of failure are revealing
Sometimes you can diagnose a problem by finding patterns in the way the test cases fail. This is another argument for making the test cases as complete as possible. Complete test cases, ordered in a reasonable way, expose patterns.

#### Test coverage patterns can be revealing

#### Test should be fast