#Unit Tests

### The three law of TDD
- You may not write production code until you have written a failing unit test
- You may not write more of a unit test than is sufficient to fail, and not compiling is failing
- you may not write more production code than i sufficient to pass the currently failing tests

## Keeping Tests Clean
The dirtier the tests, the harder they are to change.

The problem is that tests must change as the production code evolves.

From release to release the cost of maintaining test suite rose. When managers asked why their estimates were getting so large, the developers blame the tests.
Without a test suite they lost the ability to make sure that changes their code base worked as expected.

> Test code is just as important as production code

### Tests Enable the -ilities
- Tests are what keep your production code flexible, maintainable and reusable.
- Tests allow you to make changes to code without fear.
- Tests enable change.
- Tests enable improving architecture.

Without tests, your code base rots.

## Build – Operate – Check Pattern
- Build – builds up the test data
- Operate – works on the test data
- Check – ensure the operation yielded the expected results

### One Assert per Test
Make tests very easy to read"
 - Given, When, Then naming

### Single Concept per Test
More important than a single assert per test

Ensures that your tests are laser focused and not testing miscellaneous (non-related) things

## F.I.R.S.T.

### Fast
tests should be fast / run quickly
### Independent
tests should NOT depend on each other – tests should be able to be run in any order they like
### Repeatable
they should be repeatable in ANY environment without need for any specific infrastructure
### Self-Validating
they should have a boolean output – pass or fail, nothing else
### Timely
they need to be written in a timely fashion – just before the production code is written – ensures they are easy to code against    

