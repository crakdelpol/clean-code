
# COMMENTS

Everytime you write a comment you fail!

## Good comments

- Legal Comments
```
// Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.
```
- Informative Comments
```
// format matched kk:mm:ss EEE, MMM dd, yyyy Pattern timeMatcher = Pattern.compile(
"\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```
- Explanation of Intent
```
public int compareTo(Object o) {
    if(o instanceof WikiPagePath) {
        WikiPagePath p = (WikiPagePath) o;
        String compressedName = StringUtil.join(names, ""); String compressedArgumentName = StringUtil.join(p.names, ""); return compressedName.compareTo(compressedArgumentName);
    }
return 1; // we are greater because we are the right type. }
```
- Clarification
```
public void testCompareTo() throws Exception {
WikiPagePath a = PathParser.parse("PageA"); WikiPagePath ab = PathParser.parse("PageA.PageB"); WikiPagePath b = PathParser.parse("PageB"); WikiPagePath aa = PathParser.parse("PageA.PageA"); WikiPagePath bb = PathParser.parse("PageB.PageB"); WikiPagePath ba = PathParser.parse("PageB.PageA");
}
assertTrue(a.compareTo(a) == 0); // a == a
assertTrue(a.compareTo(b) != 0); // a != b
assertTrue(ab.compareTo(ab) == 0); // ab == ab
assertTrue(a.compareTo(b) == -1); // a < b
assertTrue(aa.compareTo(ab) == -1); // aa < ab
assertTrue(ba.compareTo(bb) == -1); // ba < bb
assertTrue(b.compareTo(a) == 1); // b > a
assertTrue(ab.compareTo(aa) == 1); // ab > aa
assertTrue(bb.compareTo(ba) == 1); // bb > ba

```
- Warning of Consequences
```
// Don't run unless you
// have some time to kill.
public void _testWithReallyBigFile() {
    writeLinesToFile(10000000);
    response.setBody(testFile);
    response.readyToSend(this);
    String responseString = output.toString(); assertSubString("Content-Length: 1000000000", responseString); assertTrue(bytesSent > 1000000000);
}
```
- TODO comments
```
//TODO-MdM these are not needed
// We expect this to go away when we do the checkout model protected VersionInfo makeVersion() throws Exception
{
    return null;
}
```
- Amplification
```
String listItemContent = match.group(3).trim();
// the trim is real important. It removes the starting // spaces that could cause the item to be recognized
// as another list.
new ListItemWidget(this, listItemContent, this.level + 1); return buildList(text.substring(match.end()));
```
- Javadocs in Public APIs
There is nothing quite so helpful and satisfying as a well-described public API. The java- docs for the standard Java library are a case in point. It would be difficult, at best, to write Java programs without them.
If you are writing a public API, then you should certainly write good javadocs for it. But keep in mind the rest of the advice in this chapter. Javadocs can be just as misleading, nonlocal, and dishonest as any other kind of comment.

## Bad comments

- Mumbling
```
public void loadProperties() {
    try {
        String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE; FileInputStream propertiesStream = new FileInputStream(propertiesPath); loadedProperties.load(propertiesStream);
    }
    catch(IOException e) {
        // No properties files means all defaults are loaded
    }
}
```
- Redundant Comments
```
// Utility method that returns when this.closed is true. Throws an exception // if the timeout is reached.
public synchronized void waitForClose(final long timeoutMillis)
throws Exception {
if(!closed) {
wait(timeoutMillis); if(!closed)
throw new Exception("MockResponseSender could not be closed"); }
}
```
- Misleading Comments

Sometimes, with all the best intentions, a programmer makes a statement in his comments that isn’t precise enough to be accurate. Consider for another moment the badly redundant but also subtly misleading comment we saw in Listing 4-1.
Did you discover how the comment was misleading? The method does not return when this.closed becomes true. It returns if this.closed is true; otherwise, it waits for a blind time-out and then throws an exception if this.closed is still not true.
This subtle bit of misinformation, couched in a comment that is harder to read than the body of the code, could cause another programmer to blithely call this function in the expectation that it will return as soon as this.closed becomes true. That poor programmer would then find himself in a debugging session trying to figure out why his code executed so slowly.

```
```
- Mandated Comments
```
/** *
* @param title The title of the CD
* @param author The author of the CD
* @param tracks The number of tracks on the CD
* @param durationInMinutes The duration of the CD in minutes */
public void addCD(String title, String author,
    int tracks, int durationInMinutes) {
    CD cd = new CD();
    cd.title = title;
    cd.author = author;
    cd.tracks = tracks;
    cd.duration = duration;
    cdList.add(cd);
}
```
- Journal Comments
```
* Changes (from 11-Oct-2001)
* --------------------------
* 11-Oct-2001 : * Re-organised the class and moved it to new package com.jrefinery.date (DG);
* 05-Nov-2001 : * Added a getDescription() method, and eliminated NotableDate class (DG);
* 12-Nov-2001 : * IBD requires setDescription() method, now that NotableDate class is gone (DG); Changed getPreviousDayOfWeek(), getFollowingDayOfWeek() and getNearestDayOfWeek() to correct bugs (DG);
* 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
* 29-May-2002 : Moved the month constants into a separate interface (MonthConstants) (DG);
* 27-Aug-2002 : Fixed bug in addMonths() method, thanks to N???levka Petr (DG); Fixed errors reported by Checkstyle (DG);
* 03-Oct-2002 : Implemented Serializable (DG);
* 13-Mar-2003 : Fixed bug in addMonths method (DG);
* 29-May-2003 : Implemented Comparable. Updated the isInRange javadocs (DG); Fixed bug in addYears() method (1096282) (DG);

```
- Noise Comments
```
/**
* Default constructor. */
protected AnnualDateRule() { }

/** The day of the month. */
private int dayOfMonth;
```
- Scary noise
```
/** The name. */
private String name;

/** The version. */
private String version;

/** The licenceName. */
private String licenceName;

/** The version. */
private String info;
```
- Don’t Use a Comment When You Can Use a Function or a Variable

Consider the following stretch of code:
```
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```
This could be rephrased without the comment as
```
ArrayList moduleDependees = smodule.getDependSubsystems(); String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```
- Position Markers
```
// Actions //////////////////////////////////
```
- Closing Brace Comments
```
public class wc {
    public static void main(String[] args) {
    BufferedReader in = new BufferedReader(new InputStreamReader(System.in)); String line;
    int lineCount = 0;
    int charCount = 0;
    int wordCount = 0;
    try {
        while ((line = in.readLine()) != null) { lineCount++;
            charCount += line.length();
            String words[] = line.split("\\W"); wordCount += words.length;
        } //while
        System.out.println("wordCount = " + wordCount); System.out.println("lineCount = " + lineCount); System.out.println("charCount = " + charCount);
    } // try
    catch (IOException e) { System.err.println("Error:" + e.getMessage());
    } //catch
} //main }
```
- Attributions and Bylines
```
/* Added by Rick */
```
- Commented-Out Code
```
InputStreamResponse response = new InputStreamResponse();
response.setBody(formatter.getResultStream(), formatter.getByteCount());
// InputStream resultsStream = formatter.getResultStream();
// StreamReader reader = new StreamReader(resultsStream);
// response.setContent(reader.read(formatter.getByteCount()));
```
- HTML Comments
```
/**
* Task to run fit tests.
* This task runs fitnesse tests and publishes the results.
* <p/>
* <pre>
* Usage:
* &lt;taskdef name=&quot;execute-fitnesse-tests&quot;
*
* *OR
* &lt;taskdef classpathref=&quot;classpath&quot;
* resource=&quot;tasks.properties&quot; /&gt;
* <p/>
* &lt;execute-fitnesse-tests
* suitepage=&quot;FitNesse.SuiteAcceptanceTests&quot;
* fitnesseport=&quot;8082&quot;
* resultsdir=&quot;${results.dir}&quot;
* resultshtmlpage=&quot;fit-results.html&quot;
* classpathref=&quot;classpath&quot; /&gt;
* </pre> */
```
- Nonlocal Information
```
/**
* Port on which fitnesse would run. Defaults to <b>8082</b>. *
* @param fitnessePort
*/
public void setFitnessePort(int fitnessePort) {
this.fitnessePort = fitnessePort; }
```
- Too Much Information
```
/*
RFC 2045 - Multipurpose Internet Mail Extensions (MIME)
Part One: Format of Internet Message Bodies
section 6.8. Base64 Content-Transfer-Encoding
The encoding process represents 24-bit groups of input bits as output strings of 4 encoded characters. Proceeding from left to right, a 24-bit input group is formed by concatenating 3 8-bit input groups. These 24 bits are then treated as 4 concatenated 6-bit groups, each of which is translated into a single digit in the base64 alphabet. When encoding a bit stream via the base64 encoding, the bit stream must be presumed to be ordered with the most-significant-bit first. That is, the first bit in the stream will be the high-order bit in the first 8-bit byte, and the eighth bit will be the low-order bit in the first 8-bit byte, and so on.
*/
```
- Inobvious Connection
```
/*
RFC 2045 - Multipurpose Internet Mail Extensions (MIME)
Part One: Format of Internet Message Bodies
section 6.8. Base64 Content-Transfer-Encoding
The encoding process represents 24-bit groups of input bits as output strings of 4 encoded characters. Proceeding from left to right, a 24-bit input group is formed by concatenating 3 8-bit input groups. These 24 bits are then treated as 4 concatenated 6-bit groups, each of which is translated into a single digit in the base64 alphabet. When encoding a bit stream via the base64 encoding, the bit stream must be presumed to be ordered with the most-significant-bit first. That is, the first bit in the stream will be the high-order bit in the first 8-bit byte, and the eighth bit will be the low-order bit in the first 8-bit byte, and so on.
*/
```
- Function Headers
```
Short functions don’t need much description. A well-chosen name for a small function that does one thing is usually better than a comment header.
```
- Javadocs in Nonpublic Code
```

As useful as javadocs are for public APIs, they are anathema to code that is not intended for public consumption. Generating javadoc pages for the classes and functions inside a system is not generally useful, and the extra formality of the javadoc comments amounts to little more than cruft and distraction.
```

# OBJECT AND DATA STRUCTURE

difference from Objects and Data Structure
Objects hide their data behind abstractions and expose functions that operate on that data. Data struc-ture expose their data and have no meaningful functions.

data structure:
    public variables
    no method

class:
    private variables
    public method

```
//procedural shape
public class Square {
    public Point topLeft;
    public double side;
}
public class Rectangle {
    public Point topLeft;
    public double height;
    public double width;
}
public class Circle {
    public Point center;
    public double radius;
}
public class Geometry {
    public final double PI = 3.141592653589793;
    public double area(Object shape) throws NoSuchShapeException {
        if (shape instanceof Square) {
            Square s = (Square)shape;
         return s.side * s.side;
        } else if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle)shape;
             return r.height * r.width;
        } else if (shape instanceof Circle) {
            Circle c = (Circle)shape;
            return PI * c.radius * c.radius;
        }
        throw new NoSuchShapeException(); }
}

```
```

//Polymorphic shape
public class Square implements Shape {
    private Point topLeft;
    private double side;
    public double area() {
        return side*side;
    }
}

public class Rectangle implements Shape {
    private Point topLeft;
    private double height;
    private double width;

    public double area() {
        return height * width;
    }
}

public class Circle implements Shape {
    private Point center;
    private double radius;
    public final double PI = 3.141592653589793;

    public double area() {
        return PI * radius * radius;
    }
}
```


Procedural code (code using data structures) makes it easy to add new functions without changing the existing data structures. OO code, on the other hand, makes it easy to add new classes without changing existing functions.
The complement is also true:

- Procedural code makes it hard to add new data structures because all the functions must change.

- OO code makes it hard to add new functions because all the classes must change(the expression problem).

So, the things that are hard for OO are easy for procedures, and the things that are hard for procedures are easy for OO!

The less implementation you expose the more opportunity do you have to crate polymorphic class

### The Law of Demeter
More precisely, the Law of Demeter says that a method f of a class C should only call the methods of these:
 - C
 - An object created by f
 - An object passed as an argument to f
 - An object held in an instance variable of C

The method should not invoke methods on objects that are returned by any of the allowed functions. In other words, talk to friends, not to strangers.

The following code3 appears to violate the Law of Demeter (among other things) because it calls the getScratchDir() function on the return value of getOptions() and then calls getAbsolutePath() on the return value of getScratchDir().

```final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();```

### DTO data transfer object

The quintessential form of a data structure is a class with public variables and no functions. This is sometimes called a data transfer object, or DTO. DTOs are very useful structures, especially when communicating with databases or parsing messages from sockets, and so on. They often become the first in a series of translation stages that convert raw data in a database into objects in the application code.

### Active Record
Active Records are special forms of DTOs. They are data structures with public (or bean- accessed) variables; but they typically have navigational methods like save and find. Typi- cally these Active Records are direct translations from database tables, or other data sources.

Unfortunately we often find that developers try to treat these data structures as though they were objects by putting business rule methods in them. This is awkward because it creates a hybrid between a data structure and an object.

The solution, of course, is to treat the Active Record as a data structure and to create separate objects that contain the business rules and that hide their internal data (which are probably just instances of the Active Record).


## Boundaries
it's a separation from things can be crated and things can be abstract
database(concrete) -> DO (abstract)

DB depends from domain but domain not depends from database

application and DO -> db interface layer -> database
interface -> implementation -> physical database

Domain object and database are not the same thing
separate if with a layer
