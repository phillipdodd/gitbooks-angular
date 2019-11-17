# Writing Good Unit Tests

## Using a SUT Object

**sut** stands for **system under testing** and can be used to ensure that the state in which you are testing your app is as you'd expect it to be, with no surprises.

This is accomplished by declaring such an variable within the **describe** function, and using the **beforeEach** function to set it to an empty object before every **it** test that is run.

```typescript
describe('my first test', () => {
    let sut;

    beforeEach(() => {
        sut = {};
    });

    //...
});
```

## Sensible Test Statements

For every test that is run, the statement that appears next to the pass/fail of the test will be the statement provided to the **it** function with its parent **describe** function's statement prepended to it. If that **describe** is nested in another **describe,** it will continue prepending until all statements are accounted for. For example, this:

```javascript
//* Outer describe for the service
describe('user service', () => {

    //* Inner describe for the service method
    describe('getUser method', () => {

        //* it test to run on the method
        it('should get correct user', () => {
            // <insert test here>
        });
    });
});
```

Would result in the statement of

> user service getUser method should get correct user

{% hint style="info" %}
**describe** statements should be refer to the over-all "thing" being tested, while **it** statements should refer to a _specific functionality_ that is being tested.
{% endhint %}

By proper usage of nesting **describe** functions and beginning **it** statements with the word `should`, tests suites will have easy to understand and organized statements.

## Three Phases of it\(\)

### Arrange

First, the state should be arranged in such a way that makes sense for your test.

### Act

Second, the actions you are seeking to test should be taken.

### Assert

Lastly, Assertions should be made to verify that your test passed or failed as expected. Whether or not your Assertions 'pass' is what will be displayed in the final results in the test report.

```javascript
//* Outer describe for the service
describe('example', () => {
    let sut;

    beforeEach(() => {
        sut = {};
    });
    
    it('should be true if true', () => {
        //* Arrange the state
        sut.a = false;

        //* Act upon the state
        sut.a = true;

        //* Make an Assertion
        expect(sut.a).toBe(true);
    });
});
```

## Tell a Story

The **it** should tell the complete story of a test, without too much looking around needed to figure out what is going on. 

### beforeEach\(\) for less interesting set up

### Keep critical setup in it\(\)



