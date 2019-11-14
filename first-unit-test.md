# First Unit Test

## Create Spec File

First create a file named **first-test.spec.ts** within the **app** directory of your project.

{% hint style="info" %}
The `.spec` part of the file name stands for the word _specification._
{% endhint %}

## Create [Jasmine ](https://jasmine.github.io/)Function

### [describe\(\)](https://jasmine.github.io/api/3.5/global.html#describe)

**describe\(\)** functions are for creating **groups of tests** \(often called a **suite**\) and take two parameters: a description **string** and a callback **function** in which our tests will live. The callback function here returns void and takes no parameters.

TODO EXPLAIN SUT

```typescript
describe('my first test', () => {
    let sut;

    beforeEach(() => {
        sut = {};
    });

    //...
});
```

### [beforeEach\(\)](https://jasmine.github.io/api/3.5/global.html#beforeEach)

**beforeEach\(\)** lets us define behavior to be executed _before_ each test in the describe-suite is executed. At the very least, it should be used to **reset the state** so that no test creates unexpected side-effects for another.

It requires a **function** argument as its first parameter that will be executed before each test and has an **optional second parameter** that takes a **number** to specify a **timeout** for an async beforeEach.

### [it\(\)](https://jasmine.github.io/api/3.5/global.html#it)

**it\(\)** is the function that actually creates a test. Similar to the **describe\(\)** function, the first argument is a **description string.** By convention, this description should **begin with the word 'should'**. This way, if the test fails, it will display what the code should be done **but is not**.

```typescript
describe('my first test', () => {
    let sut;

    beforeEach(() => {
        sut = {};
    });

    it('should be true if true', () => {
        //* Arrange test
        sut.a = false;

        //* Perform action(s)
        sut.a = true;

        //* Make Assertion
        expect(sut.a).toBe(true);
    });

});
```

### [expect\(\)](https://jasmine.github.io/api/3.5/global.html#expect) and [Matchers](https://jasmine.github.io/api/3.5/matchers.html)

On line 16 in the example above, we see **expect\(\)** being used along with the function, **toBe\(\)**, one of Jasmie's Matcher functions that serve as **assertions** for what we specified to be expected from the specification with **expect\(\)**. 

Matcher functions are what ultimately result in the test returning true or false.



### 

## 

