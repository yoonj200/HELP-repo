# **PHASE 1 - JavaScript**
## **JavaScript Fundamentals**
-----
### **Variables**
Initialize variables with `var`, `let` or `const`.

```javascript
let pi; // => initialize
pi = 3.14159; // => assignment expression
let pi = 3.14159 // => both
```
Reassign variable values with assignment expression.

- **`let`** variables cannot be redeclared
- **`const`** variables cannot be redeclared or reassigned

General rule of thumb:
1. Use `var` ... never
2. Use `let`... when you know the variable value will change. 
3. Use `const`... for every other variable.

### **Comparisons**
Strict equality and inequality operators (`===`, `!==`)
- Return true if two values are equal or unequal *without performing type conversions*
```javascript
42 === 42; // => true

42 === "42"; // => false

9001 !== '9001' // => true

[] !== '' // => true
```
Loose equality and inequality operators (`==`, `!=`)
- Return true if two values are equal or unequal *if it can perform type conversions*
```javascript
"0" == false; // => true

null == undefined; // => true

9001 != '9001' // => false

[] != '' // => false
```
**Strict equality and inequality operators should be preferred for comparisons.**

Relational operators
- greater tahn (`>`)
- greater than or equals (`>=`)
- less than (`<`)
- less than or equals (`<=`)

### **Conditionals**
Truthy values are `true` upon conversion. Falsy values are `false`. 

Falsy values include: `false`, `null`, `undefined`, `0`, `NaN`, empty strings (`''`, `""`). **All other values are truthy.**
To check whether a value is truthy or falsy in a browser's JS console, pass it to the global Boolean object, which converts the value into its boolean equivalent:
```javascript
Boolean(false); // => false

Boolean(null); // => false

Boolean(undefined); // => false

Boolean(0); // => false

Boolean(NaN); // => false

Boolean(''); // => false

Boolean(true); // => true

Boolean(42); // => true

Boolean('Hello, world!'); // => true

Boolean({ firstName: 'Brendan', lastName: 'Eich' });
// => true
```

**`if` statement**
Syntax:
```javascript
if (condition) {
    // code block
}
```
`if...else` statements can return truthy and falsy values
```javascript
const age = 14;

let isAdult;

if (age >= 18) {
    isAdult = true;
} else {
    isAdult = false;
}
// => false

isAdult;
// => false
```
Here, `else` does not take a condition.

**`ternary expressions`**
Syntax:
```javascript
condition ? exprIfTrue : exprIfFalse
// exprIfTrue => executed if condition evaluates truthy value
// exprIfFalse => executed if condition evaluates falsy value
```
Example:
```javascript
const age = 26;
const isAdult = age >= 18 ? true : false;

isAdult;
// => true
```
Here, when the conditional code returns `true`, return `"true"`, and when it returns `false`, return `"false"`. 

The ternary (`if...else`) expression is only necessary **if the desired return value is something other than a Boolean** (a value that can either be true or false).

**`else if` and nested `if` statements**

```javascript
const age = 20;

let isAdult, canWork, canEnlist, canDrink;

if (age >= 21) {
    isAdult = true;
    canWork = true;
    canEnlist = true;
    canDrink = true;
} else if (age >= 18) {
    isAdult = true;
    canWork = true;
    canEnlist = true;
} else if (age >= 16) {
    canWork = true;
}
// => true

isAdult; // => true

canWork; // => true

canEnlist; // => true
``` 
The above example is redundant, so try nested `if` statements:
```javascript
const age = 17;

let isAdult, canWork, canEnlist, canDrink;

if (age >= 16) {
  canWork = true;

  if (age >= 18) {
    isAdult = true;
    canEnlist = true;

    if (age >= 21) {
      canDrink = true;
    }
  }
}

canWork;
```

`switch` statements help streamline code with case statements.
Syntax:
```javascript
switch (expression) {
  case value1:
    //Statements executed when the
    //result of expression matches value1
    [break;]
  case value2:
    //Statements executed when the
    //result of expression matches value2
    [break;]
  ...
  case valueN:
    //Statements executed when the
    //result of expression matches valueN
    [break;]
  [default:
    //Statements executed when none of
    //the values match the value of the expression
    [break;]]
}
```
Example:
```javascript
const order = 'cheeseburger';

let ingredients;

switch (order) {
    case 'cheeseburger':
        ingredients = 'bun, burger, cheese, lettuce, tomato, onion';
        break;
    case 'hamburger':
        ingredients = 'bun, burger, lettuce, tomato, onion';
        break;
    case 'malted':
        ingredients = 'milk, ice cream, malted milk powder';
        break;
    default:
        console.log("Sorry, that's not on the menu right now.");
        break;
}
```
The same set of statements can be set to multiple cases:
```javascript

const order = 'cheeseburger';

let ingredients;

switch (order) {
    case 'cheeseburger':
    case 'hamburger':
    case 'malted':
        ingredients = 'milk, ice cream, malted milk powder'; 
        break; // ingredients don't make sense, it's just an example
    default:
        console.log("Sorry, that's not on the menu right now.");
        break;
}
```
The `default` keyword is similar to `else` in an `if...else` construction; however, it's different from an `else` in that **the only time it does NOT run is if the engine hits a `break` in one of the `case` statements**.

`break` is used to stop the switch statement from continuing to look at case statements once it finds a match.


### **Logical Operators**
The logical NOT operator (`!`) can be used to negate an expression. It returns the opposite of the expression's truthiness.
```javascript
const truthyValue = 'This value is truthy.';
const falseyValue = 0;

!truthyValue; // => false
!!truthyValue; // => true
```
Using two NOT operators (`!!`) will convert any value into a Boolean (if you don't feel like using Boolean() for whatever reason.)

The logical AND (`&&`) and OR (`||`) operators take two expressions. 
```javascript
expression1 && expression2

expression1 || expression2
```
There are three ways the `&&` operator can be evaluated:
| Left side | Right side | Return value | Truthiness of return value |
| ---------- | ---------- | ---------- | ---------- |
| Falsey | Doesn't matter | Left side | Falsey |
| Truthy | Falsey | Right side | Falsey |
| Truthy | Truthy | Right side | Truthy |

Then there are three ways the `||` operator can be evaluated:
| Left side | Right side | Return value | Truthiness of return value |
| ---------- | ---------- | ---------- | ---------- |
| Truthy | Doesn't matter | Left side | Truthy |
| Falsey | Truthy | Right side | Truthy |
| Falsey | Falsey | Right side | Falsey |

```javascript
0 && false; // 0

0 && true; // 0

true && NaN; // NaN

true && !1; // false

!0 && "This is a string"; // This is a string

!0 && ""; // ''

!0 && !!""; // false

0 || false; // false

true || false; // true

true || 1; // true

!true || !false // true

!1 || !0 //  true
```


## **Functions in JavaScript**
-----
### **Functions**
A function is an object that contains a sequence of JavaScript statements. We can execute or call it **multiple times**.

To execute or call a function in JS, add `()` after its name (ex: `functionName()`). 

**Parameters** are locally-scoped variabels that are usable ("scoped") inside the function. 
```javascript
function exerciseDog(dogName, dogBreed) {
  ...
}
```
JS assigns **arguments** of "Byron" and "poodle" to the parameters `dogName` and `dogBreed` when called like so: 
```javascript
exerciseDog("Byron", "poodle")
```
If expected arguments aren't given, the parameters values will be `undefined`. This will *not* cause an error, but can lead to bugs.

When JS reaches a `return` in code, no further code behavior occurs. 

### **Arrow Functions**
Function declaration:
```javascript
function foo() {
  return 'bar';
}

// OR

const foo = function() {
  return 'bar';
}
```
Arrow function syntax:
```javascript
const add = (parameter1, parameter2) => parameter1 + parameter2;
          // Parameter list            // Function body
add(2,3); // 5
```
Here, we declare a variable `add` and assign an anonymous function as its value. When there are **no braces**, arrow functions have an **implicit return** (automatically return result of last expression). **This is the only time when a JS function doesn't require *explicit return* with the `return` keyword**.

If the arrow function only has one parameter, the `()` becomes optional. Almost all developers drop the parentheses in this case. 
```javascript
const twoAdder = x => x + 2;
// is the same as
const twoAdder = (x) => x + 2;
```
If an arrow function needs to work with more than one expression, use `{}` to wrap the lines of code **and** declare a return. 
```javascript
const sum = (parameter1, parameter2) => {
  console.log(`Adding ${parameter1}`)
  console.log(`Adding ${parameter2}`)
  return parameter1 + parameter2
}
sum(1,2)
```
Arrow functions are used in JS iterator methods. An iterator method allows you to work with a data set one at a time.
Example: 
```javascript
const nums = [1,2,3]
const squares = nums.map(x => x ** 2)
squares; // [1,4,9]
nums; // [1,2,3]
```

### **Callback Functions**

**Functions can be passed into other functions.** In JS, functions are **objects** with special properties that can be invoked. 
Passing an object into a function:
```javascript
function iReturnThings (thing) {
  return thing;
}

iReturnThings({ firstName: 'Brendan', lasName: 'Eich' })
// => {firstName: "Brendan", lastName: "Eich"}
```
Passing a function into a function and invoking it: 
```javascript
function iInvokeThings (thing) {
  return thing();
}

iInvokeThings(function () { return 4 + 5; });
// => 9
iInvokeThings(function () { return 'Hello, ' + 'world!'; });
// => "Hello, world!"
```
**Callback functions** are functions passed into another function wherein it might be invoked. These functions are not invoked immediately - they are instead *called back*, or invoked at a later point. 

Note that callback functions are generally better as anonymous functions. Naming them works, but it clutters things up. Also, we refer to them by the name of the parameter into which they're passed:
```javascript
function main (cb) {
  console.log(cb())
}

main(function () {
  return "After I get passed to the main() function as the only argument, I'm stored in the local 'cb' variable!"
})
```
1. The anonymous function, `function () { return "After I get passed... }`, is passed as the lone argument to the invocation of `main()`.
2. `main()` stores the passed-in function in the local `cb` variable and then invokes the callback function.
3. The invoked callback returns its long string, which was `console.log()`-ed out in `main()`.

## **Scope**
-----
### **Intro to Scope**
Scope is where something is available. Every **execution context** creates a new scope that encompasses all variables and functions declared in it. 
```javascript
// 'myFunc' is declared in global scope and available everywhere
function myFunc() {
  return 42;
}
// => undefined

// 'myVar' is able to reference and invoke 'myFunc' because both are declared in same scope (global execution context):
const myVar = myFunc() * 2;
// => undefined

myVar;
// => 84
```
Declaring a function with its own code creates a **function scope**. Anything declared inside the function **cannot be referenced from the outside**.

A block statement also creates **block scope**, but there are some things to know.
`var` variables are **not** block-scoped:
```javascript
if (true) {
  var myVar = 42;
}
myVar; // => 42
```
`const` and `let` variables are block-scoped:
```javascript
if (true) {
  const myVar = 42;

  let myOtherVar = 9001;
}
myVar;
// Uncaught ReferenceError: myVar is not defined
myOtherVar;
// Uncaught ReferenceError: myOtherVar is not defined
```
Variables declared without `const`, `let` or `var` are always globally scoped (**implicit globals**). No matter where these variables are declared, they're always globally scoped.
1. Always use `const` and `let` to declare variables.
2. Every function creates its own scope, and any variables or functions declared inside will be unavailable outside of it.

### **Scope Chain**
A function declared at the top level of a JS file has the global scope as its outer scope. When that function is invoked, it can access all variables and functions declared in the global scope. 
- Upon invocation, it creates a new scope and **retains a reference to the outer scope in which it was declared**.
- Inside the function's body, in addition to variables and functions declared in that function, it also has **access to variables and functions declared in the outer scope**. 
```js
const globalVar = 1;

function firstFunc() {
  const firstVar = 2;

  return firstVar + globalVar;
}

firstFunc();
// => 3
```
What matters for scope chain is **where the function is declared** - not where it is invoked.

### **Lexical Scoping**