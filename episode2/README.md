# Names

Every time you give a name your intent is explain what is it.

```
int d; // elapsed time in days

int elapsedTimeInDays;
```
the correct name make the code easy to read and easy to understand.

## Describe the problem
Names describe the implementation details. It talks about  the problem and solutions.

## Avoid disinformation
Programmers should avoid words whose entrenched meaning vary from our intended meaning.

```
public abstract class SerialData(){

    public abstract int toSerial();
} 
```
it's too much generic.
## Pronounceable name

Words are, by definition, Pronounceable.
It would be a shame not to take advantage of that huge portion of our brains that has evolved to deal with spoken language.

## Avoid encoding
Avoid naming variables with special character.

## class names
Class and variables are names 
Avoid name like "Manager", "Data", "Info", "Helper"
Boolean variables should be predicates. (EX: isPostable, isEMpty)
Enums should be state or object descriptor
Methods are verbs

```
public boolean set(String name, String value);

if(set("username", "uncle bob")){

}
```

Set is a method, but it returns a boolean (should be predicated!)

## The scope length rule

there is a relation from scope length and name length

Variable should have longs scope can have longs name.

public class have long scopes and should have little name.
private class should have short scope with long explanatory name.
functions with larger scope should have short name.
private functions long name in a little scope.


#Recap
 - Choose your names thoughtful.
 - Remember when you name something you communicate your intent.
 - Avoid disinformation.
 - Create names the people can pronounce
 - Avoid encodings
 - Choose Parts of Speech well
 - The scope rules
 
