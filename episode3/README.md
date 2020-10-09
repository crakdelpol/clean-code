# Functions

The functions should do one think, do well and do only one thing.

in 1990 there was a simple rule:
the functions' length should be a ScreenFlow (about 20 lines)

Today with high resolutions of screen this rules can't be applied.

When function is too much big this is a symptom of class. 
Class is a group of functions.
The larges functions are the hidden class.

Refactor with method object will extract all function in one Class.

## One thing!
One Thing! Do it well and do it only!
The reasons we write functions is to decompose a larger concept into a set of steps at next level of abstraction.
the problem: what one thing mean?

### One level of Abstraction per function
In order to make sure our functions are doing "one thing", we need to make sure that the statements within our function are all at the same level of abstraction.

### prefer exceptions to returning error codes
Returning error codes from command functions is a violation of command query separation.
When you return an error code, you create the problem that the caller must deal with the error immediately.
On the other hand, if you use exceptions instead of returned error codes, then the error processing code can be separated from the happy path code and can be simplified.

example: 
```
try {
    deletePage(page);
    registry.deleteReference(page.name)
    configKeys.deleteKey(page.getkey())
}catch(Exception e){
    logger.log(e.getMessage());
}
```
 becomes
 
 ```

public void delete(Page page){

     try {
         deletePageAndAllReference(page)
     }catch(Exception e){
         logError(e)
     }

    private void deletePageAndAllReference(page){
        deletePage(page);
        registry.deleteReference(page.name)
        configKeys.deleteKey(page.getkey())
    }

    private void logError(Exception e){
        logger.log(e.getMessage());
    }
}
 ```

### Error handling is one thing
Functions should do one thing. Error handling is one thing. Thus, a function that handles error should do nothing else.

### generic rules
continue to extract function until you can't extract anymore
the classes should be composed of functions long 4 lines.

### conclusion
Remembers: 
- first rule: Functions must be small
- second rule: Functions must be smaller than that.
- third rule: well named function will save at you and every body a lot of time
- don't worry about efficiently of functions call
- the classes are hide in long functions
- the functions do one thing and only one.
-  If you can extract one function from another you should!
