# **PHASE 1 - JavaScript**
## **1. JavaScript Fundamentals**
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


## **2. Functions in JavaScript**
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

## **3. Scope**
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

Identifiers are names that we declare variables and functions with. 
```js
const myVar = "myVar refers to the variable that contains this string"; // => undefined
function myFunc() {
  return "myFunc refers to this function that returns this string";
} // => undefined
```
The JS Engine makes two separate passes over the code:
1. **Compilation phase**
   1. JS engine reaches a variable declaration -> allocates memory and sets up a reference to variable's identifier.
   2. When the engine encounters a function declaration, it does 3 things:
      1. Allocates memory and sets up a reference to function's identifier.
      2. Creates new execution context with a new scope.
      3. Adds a reference to the parent scope (outer environment) to the scope chain, making variables and functions declared in the outer environment available in the new function's scope.
2. **Execution phase**
   1. JS engine runs through code line-by-line again, but this time it actually runs the code, assigning values to variables and invoking functions. 

### **Lexical Scoping**
```js
const myVar = "Foo";

function first() {
  console.log("Inside first()");

  console.log("myVar is currently equal to:", myVar);
}

function second() {
  const myVar = "Bar";

  first();
}
```
What do you expect when `second()` is invoked? Well, here it is: 
```js
second();
// LOG: Inside first()
// LOG: myVar is currently equal to: Foo
// => undefined
```
In this example, the asssignment of `myVar` as `Bar` is not visible to `first()`. This is because `second()` is **not** the parent scope of `first()`. 

No variable named `myVar` exists inside `first()`. When the JS engine reaches the second line of code inside the function, it consults the scope chain to figure out what `myVar` is:
```js
console.log("myVar is currently equal to:" myVar)
```

## **4. Working with Data Structures in JavaScript**
-----
### **Arrays**
Data structures associate and organize information. An **array** is an ordered list surrounded by `[]` and separated by commas:
```js
["This", "is", "an", "array", "of", "strings."];
// => ["This", "is", "an", "array", "of", "strings."]]
```
The array elements can be any data type in languages like JS, Python, Ruby, Lisp, etc. (not the case in other languages like C, C++, Java, Swift, etc.).

Use the `length` property to check how many elements are in an array: 
```js
const myArray = ["This", "array", "has", 5, "elements"];
myArray.length;
// => 5 
```

Every array element is assigned a unique index value that **starts at 0**. To access a specific element in an array, use **bracket notation**. 
```js
const winningNumbers = [32, 9, 14, 33, 48, 5];
// => undefined

winningNumbers[0];
// => 32

winningNumbers[3];
// => 33
```
If an array is particularly long and you need to access the very last element, you can use `anArray[anArray.length -]`.

Bracket notation is also useful for updating the value of an array element by its index number. 
```js
const planets = [
  "Mercury",
  "Venus",
  "Earth",
  "Mars",
  "Juptier",
  "Saturn",
  "Uranus",
  "Neptune",
];

planets[4] = "Jupiter"; //=> "Jupiter"

planets; //=> ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
```
Arrays can also contain other arrays (**nested arrays**). Again, bracket notation can be used to access these nested arrays and their elements. 
```js
const egregiouslyNestedArray = [
  "How",
  ["deep", ["can", ["we", ["go", ["?"], "Pretty"], "dang"], "deep,"], "it"],
  "seems.",
];

egregiouslyNestedArray[1];
//=> [ 'deep', [ 'can', [ 'we', [Array], 'dang' ], 'deep,' ], 'it' ]
egregiouslyNestedArray[2];
//=> 'seems.'
egregiouslyNestedArray[1][0];
//=> 'deep'
egregiouslyNestedArray[1][1];
//=> [ 'can', [ 'we', [ 'go', [Array], 'Pretty' ], 'dang' ], 'deep,' ]
egregiouslyNestedArray[1][2];
//=> 'it'
```
Generally speaking, nesting arrays is a terrible way to represent a deeply nested data structure. Keep your arrays **no more than two levels deep**. 
```js
const board = [
  ["X", "O", " "],
  [" ", "X", "O"],
  ["X", " ", "O"],
];

board; // => [["X", "O", " "], [" ", "X", "O"], ["X", " ", "O"]]
board[1]; // => [" ", "X", "O"]
board[0][0]; // => "X"
board[0][2]; // => " "
board[2][2]; // => "O"
```

### **Array Methods**
Destructive methods mutate the object, while nondestructive methods do not mutate the object.

- `.push()` and `.unshift()` work in the same way:
  - Take one or more arguments (element or elements you want to add)
  - Return length of modified array
  - Destructive
  - `push()` adds elements to the **end** of an array
  - `.unshift()` adds them to the **beginning** of an array. 
```js
const superheroes = ["Catwoman", "Storm", "Jessica Jones"];

superheroes.push("Wonder Woman"); // => 4

superheroes; // => ["Catwoman", "Storm", "Jessica Jones", "Wonder Woman"]
// --------------------------------------------------
const cities = ["New York", "San Francisco"];

cities.unshift("Boston", "Chicago"); // => 4

cities; // => ["Boston", "Chicago", "New York", "San Francisco"]
```
- The **spread operator** (nondestructive) "spreads out" an array's elements into a new array, creating a copy.
```js
const coolCities = ["New York", "San Francisco"];

const copyOfCoolCities = [...coolCities];

copyOfCoolCities; //=> ["New York", "San Francisco"]
```
This method creates a shallow copy. If used to copy a nested array, the inner array **still points to the same location in memory**. Therefore, modifying the inner array in the copy changes the inner array in the original array as well (and vice versa). Use the spread operator to clone *non-nested* arrays. 

- `.pop()` and `.shift()` work in the same way:
  - Don't take arguments
  - Remove a single element
  - Return the element that is removed
  - Destructive
  - `.pop()` removes the **last array element**
  - `.shift()` removes the **first array element**. 
```js
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

days.pop(); // => "Sun"

days; // => ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat"]
// --------------------------------------------------
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

days.shift(); // => "Mon"

days; // => [Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
```
- `.slice()` (nondestructive) removes portions (slices) of array elements. Note that it creates a shallow copy like the spread operator (`...`).
```js
// Without arguments, returns copy of original array
const primes = [2, 3, 5, 7];

const copyOfPrimes = primes.slice();

primes; // => [2, 3, 5, 7]

copyOfPrimes; // => [2, 3, 5, 7]

// ONE argument
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

days.slice(5);// => ["Sat", "Sun"]

// TWO arguments
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

days.slice(2, 5);
// => ["Wed", "Thu", "Fri"]
```
To return a new array with the first element removed, call `.slice(1)`. To reference the last element in an array:
```js
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

days.slice(-1); // => ["Sun"]

days.slice(-3); // => ["Fri", "Sat", "Sun"]

days.slice(0, -1); // => ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat"]
```
- `splice()` (destructive) removes, adds and replaces elements (or any combination of the three).
```js
// ONE argument
// array.splice(start);
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

days.splice(2); // => ["Wed", "Thu", "Fri", "Sat", "Sun"]

days; // => ["Mon", "Tue"]
```
Here, `.splice()` **both** mutated the original array (removed a chunk, leaving only `["Mon", "Tue"]`) **and** returned a new array containing the removed chunk.

Using a negative start index with `.splice()` works the same as with `.slice()`:
```js
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
// => ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]

days.splice(-2); // => ["Sat", "Sun"]

days; // => ["Mon", "Tue", "Wed", "Thu", "Fri"]
```
```js
// TWO arguments
// array.splice(start, deleteCount);
const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
// => ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]

days.splice(2, 3); // => ["Wed", "Thu", "Fri"]

days; // => ["Mon", "Tue", "Sat", "Sun"]
```
After the first two arguments, every additional argument passed to `.splice()` is inserted into the array at the position indicated by the first argument:
```js
// THREE+ arguments
//array.splice(start, deleteCount, item1, item2, ...)
const menu = [
  "Jalapeno Poppers", "Cheeseburger", "Fish and Chips", 
  "French Fries",  "Onion Rings",
];

menu.splice(1, 2, "Veggie Burger", "House Salad", "Teriyaki Tofu");
// => ["Cheeseburger", "Fish and Chips"]

menu;
// => ["Jalapeno Poppers", "Veggie Burger", "House Salad", "Teriyaki Tofu", "French Fries", "Onion Rings"]
```
`.splice()` can insert elements anywhere in an array without removing anything by passing 0 as the second argument:
```js
const books = ["The Bluest Eye", "Kindred", "The Grass Dancer"];

books.splice(2, 0, "Giovanni’s Room", "The Color Purple");
// => []

books;
// => ["The Bluest Eye", "Kindred", "Giovanni’s Room", "The Color Purple", "The Grass Dancer"]
```
- **Bracket notation** (destructive) can also be used to replace elements:
```js
const cards = [
  "Ace of Spades", "Jack of Clubs", "Nine of Clubs",
  "Nine of Diamonds", "Three of Hearts",
];

cards[2] = "Ace of Clubs"; // => "Ace of Clubs"

cards;
// => ["Ace of Spades", "Jack of Clubs", "Ace of Clubs", "Nine of Diamonds", "Three of Hearts"]
```
- Combining `.slice()` and the spread operator replaces elements nondestructively:
```js
const menu = [
  "Jalapeno Poppers", "Cheeseburger", "Fish and Chips",
  "French Fries", "Onion Rings",
];

const newMenu = [
  ...menu.slice(0, 1),
  "Veggie Burger",
  "House Salad",
  "Teriyaki Tofu",
  ...menu.slice(3),
];

menu;
// => ["Jalapeno Poppers", "Cheeseburger", "Fish and Chips", "French Fries", "Onion Rings"]

newMenu;
// => ["Jalapeno Poppers", "Veggie Burger", "House Salad", "Teriyaki Tofu", "French Fries", "Onion Rings"]
```
Overview of JS Array Methods
| Method | What it does | Arguments | Destructive/Nondestructive | Return value |
| ----- | ----- | ----- | ----- | ----- |
| `Spread operator` | Adds element(s) to beginning or end of array | N/A| Nondestructive | New array
| `.push()` | Add element(s) to end of array | 1 or more | Destructive | Length of modified array |
| `.unshift()` | Add element(s) to beginning of array | 1 or more | Destructive | Length of modified array |
| `.pop()` | Remove last element | 0 | Destructive | Removed element |
| `.shift()` | Remove first element | 0 | Destructive | Removed element |
| `.slice()` | Remove 0 or more elements | 0, 1, or 2 | Nondestructive | New array containing removed elements | 
| `.splice()` | Remove, add or replace elements | 1 or more | Destructive | New array containing removed elements |

### **Objects**
Objects are data structures consisting of key-value pairs, similar to Ruby's `Hash`, Python's `Dictionary` or C-like languages' `struct`(ure). Not to be confused with object-oriented programming.
- Object properties (key-value pairs) can point to values of any data type, even other objects
```js
// const obj = {}; => empty object
const obj = { 
  key1: value1,
  key2: value2,
 };
```
There is no limit to how deeply nested objects can be, but keys MUST be unique.
```js
const address = {
  street: {
    line1: "11 Broadway",
    line2: "2nd Floor",
  },
  city: "New York",
  state: "NY",
  zipCode: "10004",
};
```
Accessing a value stored in an object is relatively simple.
- **Dot notation** uses the member access operator (single period) to access object values 
```js
address.street;
//=> { line1: "11 Broadway", line2: "2nd Floor" }

address.city;
//=> "New York"

address.state;
//=> "NY"

address.zipCode;
//=> "10004"

address.street.line1;
//=> "11 Broadway"

address.street.line2;
//=> "2nd Floor"
```
- **Bracket notation** uses the computed member access operator to access object values
```js
address["street"];
//=> { line1: "11 Broadway", line2: "2nd Floor" }

address["street"]["line1"];
//=> "11 Broadway"

address["street"]["line2"];
//=> "2nd Floor"

address["city"];
//=> "New York"

address["state"];
//=> "NY"

address["zipCode"];
//=> "10004"
```
- **Nonstandard keys** make dot notation unable to access properties, but bracket notation still works
```js
const wildKeys = {
  "Cash rules everything around me.": "Wu",
  "C.R.E.A.M.": "Tang",
  "Get the money.": "For",
  "$ $ bill, y'all!": "Ever",
};

wildKeys.'Cash rules everything around me.';
// ERROR: Uncaught SyntaxError: Unexpected string

wildKeys["$ $ bill, y'all!"];
//=> "Ever"
```
To access a property via dot natation, the key **must follow the same naming rules applied to variables and functions**.

Bracket notation accesses a property **dynamically**, meaning it can compute the value of variables on the fly:
```js
const meals = {
  breakfast: "Oatmeal",
  lunch: "Caesar salad",
  dinner: "Chimichangas",
};

let mealName = "lunch";

meals[mealName]; //=> "Caesar salad"
// NOTE: every key is technically a string! That's why this works.
```
Bracket notation can also **dynamically set properties** *during the creation of a new object*.
```js
const morningMeal = "breakfast";
const middayMeal = "lunch";
const eveningMeal = "dinner";
// wrapping the variable names in square brackets lets the JS engine know that it needs to interpret the contents 
const meals = {
  [morningMeal]: "French toast",
  [middayMeal]: "Personal pizza",
  [eveningMeal]: "Fish and chips",
};

meals;
//=> { breakfast: "French toast", lunch: "Personal pizza", dinner: "Fish and chips" }
```
Passing an object instance as an argument to the `Object.keys()` static method returns a list of its top-level keys. It **returns an array containing all of the keys** at the top level of the Object instance: 
```js
const wednesdayMenu = {
  cheesePlate: {
    soft: "Brie",
    semiSoft: "Fontina",
    hard: "Provolone",
  },
  fries: "Sweet potato",
  salad: "Southwestern",
};

Object.keys(wednesdayMenu); //=> ["cheesePlate", "fries", "salad"]
```
`Object.values()` static method works similarly to `Object.keys()`, but it **returns an array of values** instead.

### **Modifying Objects**
Add an object property using dot or bracket notation:
```js
const circle = {};

circle.radius = 5;

circle["diameter"] = 10;

circle.circumference = circle.diameter * Math.PI;
//=> 31.41592653589793

circle["area"] = Math.PI * circle.radius ** 2;
//=> 78.53981633974483

circle;
//=> { radius: 5, diameter: 10, circumference: 31.41592653589793, area: 78.53981633974483 }
```
Update or overwrite existing properties using dot or bracket notation:
```js
const mondayMenu = {
  cheesePlate: {
    soft: "Chèvre",
    semiSoft: "Gruyère",
    hard: "Manchego",
  },
  fries: "Curly",
  salad: "Cobb",
};

mondayMenu.fries = "Sweet potato";

mondayMenu;
//=> { cheesePlate: { soft: "Chèvre", semiSoft: "Gruyère", hard: "Manchego" }, fries: "Sweet potato", salad: "Cobb" }
```
The following functions takes three arguments: an object, the key identifying the property we want to update, and the `value` we want to change its value to.
```js

function destructivelyUpdateObject(obj, key, value) {
  obj[key] = value; //Why are we using bracket notation here?

  return obj;
}
```
We can update an object nondestructively with the spread operator:
```js
function nondestructivelyUpdateObject(obj, key, value) {
  const newObj = { ...obj };

  newObj[key] = value;

  return newObj;
}
```
Use `delete` to remove an object property (key):
```js
const wednesdayMenu = {
  cheesePlate: {
    soft: "Brie",
    semiSoft: "Fontina",
    hard: "Provolone",
  },
  fries: "Sweet potato",
  salad: "Southwestern",
};

delete wednesdayMenu.salad;
//=> true

wednesdayMenu;
//=> { cheesePlate: { soft: "Brie", semiSoft: "Fontina", hard: "Provolone" }, fries: "Sweet potato" }
```
Note: **arrays are special types of objects**
```js
typof []; // => "object"
```
This means we can set properties on an array like an object, as well as modify and access said properties:
```js
const myArray = [];
myArray.summary = "Empty array!";
myArray; // => [summary: "Empty array!"]

// ----------------------------------------

myArray["summary"] = "This array is totally empty.";
myArray; //=> [summary: "This array is totally empty."]
myArray.summary; //=> "This array is totally empty."

myArray.push(2,3,5,7); //=> 4
myArray; //=> [2, 3, 5, 7, summary: "This array is totally empty."]
```
However, an array's array-style elements are stored separately from its object-style properties. Something like `myArray.length` describes how many items exist in its list, but object-style properties are not included in that calculation.

Remember, **all keys in objects and all indexes in arrays are actually strings**. 
```js
const myArray = [];

myArray[0] = "Will this be an `Object` property or an `Array` element?";
myArray.length; //=> 1
myArray;
//=> ["Will this be an `Object` property or an `Array` element?"]

myArray["0"] = "What about this one?";
myArray.length; //=> 1
myArray; //=> ["What about this one?"]
```
When accessing elements or properties of an array, the engine routes all integers and integers masquerading as strings (e.g., '14', "953", etc.) to the array's special list of elements, and it treats everything else as a simple Object property. 

- **For accessing array elements, always use integers**
- **Be wary of setting Object-style properties on an array.** It's usually more trouble than it's worth.
- **All object keys, including array indexes, are strings.** This is important to know when learning to iterate over objects.

### **Debugging**
Tracing is using output statements (like `console.log()`) to provide feedback about "what the machine is thinking." 
- Imaging debugging an order delivery process when your food is missing.

The browser (not JS!) provides an object called `console`. The 
built-in console object for debugging. The `console` object has specific methods that send text to the DevTools logging area ("the console"). 

**`console.log()`** logs general information to the console and can take multiple arguments. 
```js
console.log('Hello,', 'world!') // LOG: Hello, world!
```
Questions to consider in debugging code...
- Is what we passed in what the function got?
- Is the thing the function did what we expected it to do?
- Does the operator work like we thought it did?

**`console.error()`** prints out an error to the console and can take multiple arguments. 
```js
console.error('This is an error message.'); // ERROR: This is an error message.
```
This is helpful when letting future engineers (including yourself) know that this message is more important than the average logged message. 

**`console.warn()`** is a step down in severity from `console.error()`.
```js
console.warn('This is a warning message.'); // WARN: This is a warning message. 
```
**`console.table()`** prints a table of entries. Example:
```js
const family = {
  mother: {
    firstName: "Susan",
    lastName: "Doyle",
    age: 32
  },
  father: {
    firstName: "John",
    lastName: "Doyle",
    age: 33
  },
  daughter: {
    firstName: "Lily",
    lastName: "Doyle",
    age: 5
  },
  son: {
    firstName: "Mike",
    lastName: "Doyle",
    age: 8
  }
}
```
| (index) | firstName | lastName | age |
| ----- | ----- | ----- | ----- |
| mother | "Susan" | "Doyle" | 32 | 
| father | "John" | "Doyle" | 33 |
| daughter | "Lily" | "Doyle" | 5 | 
| son | "Mike" | "Doyle" | 8 | 

**Note**: Over the course of your programming career, you'll probably spend significantly more time debugging than actually writing new code. Just as your coding skills will improve with practice, so too will your debugging skills.

Debugging can sometimes make you feel sad. You'll fix one bug and ten new ones appear. 

If it's any `console`-ation, we all make mistakes. Treat debugging as a learning opportunity. Often, looking at your code critically and trying to figure out why something isn't working will afford you a much deeper understanding of how some feature of the language actually works.

### **JS Loops**
The **`for` loop** is made up of four statements:
- **Initialization**: used to initialize a **counter** variable
- **Condition**: an expression evaluated before each pass through the loop
  - If condition evaluates true, loop body statements execute
  - If condition evaluates false, loop exits
- **Iteration**: expression executed at the end of each iteration (typically incrementing or decrementing a counter to bring loop closer to completion)
- **Loop body**: code that runs on each pass through the loop 
```js
for ([initialization]; [condition]; [iteration]) {
  [loop body]
}
// ---------------------------------------
for (let age = 30; age < 40; age++) {
  console.log("I'm ${age} years old. Happy birthday to me!");
  debugger;
}
```
The **`while` loop** repeats an actino in a loop based on a condition (like `for` loop), but only requires condition and loop statements
```js
while ([condition]) {
  [loop body]
}
//----------------------
const gifts = ["teddy bear", "drone", "doll"];

function wrapGifts(gifts) {
  let i = 0; // the initialization moves OUTSIDE the body of the loop!
  while (i < gifts.length) {
    console.log(`Wrapped ${gifts[i]} and added a bow!`);
    i++; // the iteration moves INSIDE the body of the loop!
  }

  return gifts;
}

wrapGifts(gifts);
// LOG: Wrapped teddy bear and added a bow!
// LOG: Wrapped drone and added a bow!
// LOG: Wrapped doll and added a bow!
// => ["teddy bear", "drone", "doll"]
```
Note: When using `while` loops, leaving out iteration can result in a condition that always evaluates to `true` => infinite loop

The `for` loop is the most common looping construct in JS. A general heuristic for choosing which loop to use is to try the `for` loop first, then try a `while` loop if that doesn't work. 

### **Object Iteration**
| Looping | Iteration|
| ----- | ----- | 
| Executing a set of statements **repeatedly until a condition is met** | Executing a set of statements **once for each element in a collection** |

```js
let myArray = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];

for (let i = 0; i < myArray.length; i++) {
  console.log(myArray[i]);
}

//---------- Both accomplish the same task ----------

let myArray = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];

let j = 0;

while (j < myArray.length) {
  console.log(myArray[j++]);
}
```
A better way to do this is with the **for...of** statement:
```js
const myArray = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];

for (const element of myArray) {
  console.log(element);
}
```
**for...of** is specifically meant for iteration results. There is no initialization of a counter, no condition, no incrementing the counter, and no bracket notation to access elements in the array. **Use a `for...of` statement anytime you want to iterate over an array**.
- `for...of` also allows for `const` instead of `let`, since there is no reassignment occurring. On each trip into the loop body, it assigns the next element in the collection to a new element variable
  - Upon reaching the end of the block, the block-scoped variable vanishes and we return to the top
- `for...of` also iterates over strings (strings are basically an ordered colleciton of characters)
```js
for (const char of 'Hello, world!') {
  console.log(char);
}
// LOG: H
// LOG: e
// LOG: l
// LOG: l
// LOG: o
// LOG: ,
// LOG:
// LOG: w
// LOG: o
// LOG: r
// LOG: l
// LOG: d
// LOG: !
```
**`for...in`** statements are similar to `for...of` statements, but is generally used for **iterating over object properties**
```js
for (const [KEY] in [OBJECT]) {
  // code in statement body
}

// -------------------------------------------

const address = {
  street1: '11 Broadway',
  street2: '2nd Floor',
  city: 'New York',
  state: 'NY',
  zipCode: '10004',
};

for (const key in address) {
  console.log(key);
}

// LOG: street1
// LOG: street2
// LOG: city
// LOG: state
// LOG: zipCode
```
**Accessing the object's value** is as simple as combining the passed-in key with the bracket operator (the dot operator doesn't work for this purpose):
```js
const address = {
  street1: '11 Broadway',
  street2: '2nd Floor',
  city: 'New York',
  state: 'NY',
  zipCode: "10004"
};

for (const key in address) {
  console.log(address[key]);
}

// LOG: 11 Broadway
// LOG: 2nd Floor
// LOG: New York
// LOG: NY
// LOG: 10004
```
The `for...in` statement works with arrays because **arrays are objects**. DON'T use `for...in` to iterate over arrays. From MDN documentation: 

- A `for...in` loop iterates over the properties of an object in an arbitrary order ... one cannot depend on the seeming orderliness of iteration, at least in a cross-browser setting.

### **Traversing Nested Objects**

**Objects in Objects**
Here's an example:
```js
const userInfo = {
  firstName: "Avi",
  lastName: "Flombaum",
  company: {
    name: "Flatbook Labs",
    jobTitle: "Developer Apprentice",
  },
  friends: [
    {
      firstName: "Nancy",
      lastName: "Burgess",
      company: {
        name: "Flatbook Labs",
        jobTitle: "Developer Apprentice",
      },
    },
    {
      firstName: "Corinna",
      lastName: "Jackson",
      company: {
        name: "Flatbook Labs",
        jobTitle: "Lead Developer",
      },
    },
  ],
  projects: [
    {
      title: "Flatbook",
      description:
        "The premier Flatiron School-based social network in the world.",
    },
    {
      title: "Scuber",
      description:
        "A burgeoning startup helping busy parents transport their children to and from all of their activities on scooters.",
    },
  ],
};
```
You can grab a value using dot notation
```js 
userInfo.lastName; //=> "Flombaum"
```
If the property being accessed is nested in another object, just append additional key(s)
```js
userInfo.company.jobTitle; //=> "Developer Apprentice"
```
If the property is nested inside an array, specify the index for the intended element
```js
userInfo.friends[0].firstName; //=> "Nancy"
userInfo.projects[1].title; //=> "Scuber"
```
**Arrays in Arrays**
Working with nested arrays is similar to nested objects. Simply replace the named properties of nested objects with indexes of nested arrays. 

Here's an example:
```js
const letters = ["a", ["b", ["c", ["d", ["e"]], "f"]]];

letters[1];
//=> ["b", ["c", ["d", ["e"]], "f"]]
letters[1][1];
//=> ["c", ["d", ["e"]], "f"]
letters[1][1][1];
//=> ["d", ["e"]]
letters[1][1][1][1];
//=> ["e"]
letters[1][1][1][1][0];
//=> "e"
// Each lookup (each square bracket pair) drills down into each successive nested array
```
Use **recursion** to iterate over nested objects and arrays. A recursive function is **a function that calls itself** (until it doesn't).
```js
function recurse() {
    if(condition) {
        // stop calling itself
        //...
    } else {
        recurse(); // calls itself here
    }
}
```
Let's say you want to count down from a specified number to 1 (3 to 1 in this example).
```js
function countDown(fromNumber) {
  console.log(fromNumber);
  let nextNumber = fromNumber - 1;
  if (nextNumber > 0) {
    countDown(nextNumber)
  }
}
countdown(3); //=> 3 2 1
```


## **5. Array Iteration**
-----


## **6. JavaScript Advanced Syntax**
-----


## **7. Flatiron's Three Pillars of JavaScript**
-----


## **8. JavaScript and the DOM
-----


## **9. JavaScript Events**
-----


## **10. Communicating with the Server**
-----


## **11. Combining the Three Pillars**
-----


## **12. Algorithmic Problem Solving**
-----


## **13. Context in JavaScript**
-----


## **14. Object-Oriented JavaScript**
-----


## **15. JavaScript Inheritance**
-----


