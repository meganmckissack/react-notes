# React

functional programming is immutable (can’t be changed)

in react we’ll use `const` and not `let` so that the variables imply they’re not changeable 

Object-oriented programming is imperative - **Imperative programming** is when we tell our program exactly what we want to do and how we want it done. This means explicitly stating all the steps needed to get to an end result.

React is declarative - **Declarative programming** is when we tell our program what the end result should be and then let our program decide the best way to achieve this result.

Imperative example

```jsx
const originalArray = [1,2,3];
let doubledArray = [];
originalArray.forEach(function(element) {
  const doubledElement = element * 2;
  doubledArray.push(doubledElement);
});
doubledArray;
```

Declarative example

```jsx
const originalArray = [1,2,3];
const newArray = originalArray.map(function(element) {
  return element * 2;
});
```

pure function - given a specific input, always returns the same output

```jsx
function addOne(num) {
  return num + 1;
}
```

      **A pure function always returns an output.**

**A pure function can not have side effects -** A side effect is when a function changes something in the application outside of the function. Pure functions should only return a single thing. They should not alter anything else in the application.

**Pure functions cannot rely on external variables or state**

**Pure functions are easier to test**

**What You See Is What You Get**

**Pure functions result in fewer bugs**

A function expression is when an anonymous function (that is, a function that doesn't have a name) is stored inside a variable to be called later.

A function that returns yet another function is known as a **higher-order function**
Functions that take other functions as arguments are also higher-order functions as well.

**[Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)**

A closure is an inner function that has access to variables from an outer function. In JavaScript, closures are created every time a function is created, at function creation time.

```jsx
function welcome(salutation) {
  return function(yourName) {
    return `${salutation}! Nice to meet you, ${yourName}!`
  }
}

const heyThere = welcome("Hey there");

heyThere("Joe")
"Hey there! Nice to meet you, Joe!"

Another example with same function 
const spanishGreeting = welcome("Buenos días!");
> spanishGreeting("Joe");
"Buenos días! Nice to meet you, Joe!"

inner function has access to yourName variable and the outter function's salutation variable
```

**Currying**
When we **curry** a function, we take a function with multiple arguments and then rewrite it as a series of functions, each with one argument.

```jsx
function aThingIMaybeLike(howMuchILikeIt) {
  return function(thing) {
    return function(reason) {
      return `I ${howMuchILikeIt} ${thing} because ${reason}.`;
    }
  }
}

aThingIMaybeLike("really like")("functional programming") ("it's cool")
```

Higher order fuctions

`map()`

```jsx
const numArray = [1, 2, 3, 4, 5];
const doubledArray = numArray.map(function(element) {
  return element * 2;
});
doubledArray;

or
const doubledArray = numArray.map (e => e * 2);
```

In the example above, we don't mutate an array. Instead, we save mapped `numArray`
 into a new constant.

**Use `Array.prototype.map()` whenever you want to modify every element in an array.**

**`reduce()`**

```jsx
const numArray = [3, 7, 5];
const summedArray = numArray.reduce(function(currentValue, element) {
  return element + currentValue;
}, 0);
```

In the example above, reduce takes two arguments. The first is the `currentValue`of the `reduce()`function. The second is the `element`of the array. Finally, note the `0`after the function itself. This is an initial value that we can optionally provide. That way, `reduce()`knows what the `currentValue`
 will start with. Note that if we wanted to multiply or divide, this initial value would be `1`Otherwise, we'd be multiplying or dividing by zero!

**Use `Array.prototype.reduce()` whenever you want to "reduce" an array down to a single element.**

**`filter()`**

```jsx
const numArray = [7, 14, 32, 8];
const filteredArray = numArray.filter(e => e > 10);
```

**Use `Array.prototype.filter()` whenever you want to filter an array based on certain conditions**

**Recursion**

Recursion is simply a function that calls itself.

```jsx
const incrementCounter = (counter) => {
  if (counter >= 3) {
    return counter;
  } else {
    console.log(counter);
    return incrementCounter(counter + 1);
  }
}

incrementCounter(0);
```

Our recursive function includes two conditionals. The first includes what is called the **base case**. This is the final condition where our function will stop calling itself. If we don't have a base case, a recursive function will call itself forever.

The second conditional includes the recursion itself. Each time this conditional is reached, the function will call itself. The argument we pass in is `counter + 1` because we want the new value of the counter to be incremented by one.

three main parts to a recursive function

- **Base case**: The final condition of a successfully called recursive function.
- **Termination case**: A conditional that's called if something goes wrong. This prevents an infinite loop.
- **Recursion**: This part of the function is where the magic happens and the function calls itself.