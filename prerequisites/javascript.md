---
id: javascript
title: Javascript
---

JavaScript (JS) is a lightweight, interpreted, or just-in-time compiled programming language with first-class functions. While it is most well-known as the scripting language for Web pages, many non-browser environments also use it, such as Node.js, Apache CouchDB and Adobe Acrobat. JavaScript is a prototype-based, multi-paradigm, single-threaded, dynamic language, supporting object-oriented, imperative, and declarative (e.g. functional programming) styles. Read more about JavaScript.

### ES5 & ES6 

ECMAScript is a trademarked scripting language specification that is defined by ECMA International. It was created to standardize JavaScript. The ES scripting language has many implementations, and the popular one is JavaScript. Generally, ECMAScript is used for client-side scripting of the World Wide Web.

ES5 is an abbreviation of ECMAScript 5 and also known as ECMAScript 2009. The sixth edition of the ECMAScript standard is ES6 or ECMAScript 6. It is also known as ECMAScript 2015. ES6 is a major enhancement in the JavaScript language that allows us to write programs for complex applications.
Below is a comparison given between the two specifications-

| **Based on**            | **ES5**                                                                                                   | **ES6**                                                                                                                                   |
|-------------------------|-----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **Data-types**          | ES5 supports primitive data types that are string, number, boolean, null, and undefined.                  | In ES6, there are some additions to JavaScript data types. It introduced a new primitive data type 'symbol' for supporting unique values. |
| **Performance**         | As ES5 is prior to ES6, there is a non-presence of some features, so it has a lower performance than ES6. | Because of new features and the shorthand storage implementation ES6 has a higher performance than ES5.                                   |
| **Object Manipulation** | ES5 is time-consuming than ES6.                                                                           | Due to destructuring and speed operators, object manipulation can be processed more smoothly in ES6.                                      |
| **Arrow Functions**     | In ES5, both function and return keywords are used to define a function.                                  | An arrow function is a new feature introduced in ES6 by which we don't require the function keyword to define the function.               |
| **Loops**               | In ES5, there is a use of for loop to iterate over elements.                                              | ES6 introduced the concept of `for...of` loop to perform an iteration over the values of the iterable objects.                              |


#### References
Please refer to the below references for more detail-

- **MDN Resources** - [``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources)
- **JavaTPoint** - [``https://www.javatpoint.com/es5-vs-es6#:~:text=ES5%20is%20an%20abbreviation%20of,write%20programs%20for%20complex%20applications``](https://www.javatpoint.com/es5-vs-es6#:~:text=ES5%20is%20an%20abbreviation%20of,write%20programs%20for%20complex%20applications)

### Let,Const & Var

In JavaScript, variables can be declared using three different methods: var, let, and const.

-**Var** - The var is the oldest keyword to declare a variable in JavaScript. It is global scoped or function scoped. The scope of the var keyword is the global or function scope. It means variables defined outside the function can be accessed globally, and variables defined inside a particular function can be accessed within the function.

  **Syntaxt** - 
  ```bash 
  var brand = "Cogitate";
  console.log(brand); // output-> "Cogitate"
  ```
-**Let** - This keyword is used to declare variable locally. If you used this keyword to declare variable then the variable can accessible locally and it is changeable as well. It is good if the code gets huge. 

  **Syntaxt** - 
  ```bash 
  if (true) {
    let brand = "Cogitate";
    console.log(brand); // output-> "Cogitate"
    }
      
    /* This will be error and 
       show brand is not defined */
    console.log(brand);
  ```

-**Const** - This keyword is used to declare variable locally. If you use this keyword to declare a variable then the variable will only be accessible within that block similar to the variable defined by using let and difference between let and const is that the variables declared using const values can’t be reassigned. So we should assign the value while declaring the variable.

  **Syntaxt** - 
  ```bash 
const brand = "Cogitate";
console.log(brand); // output->"Cogitate"
  ```

**Note:** `var` used to be a part of ES5 but it had issues hence `let` & `const` were introduced in ES6.

#### References
Please refer to the below references for more detail-

- **MDN Resources** - [``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources)
- **GeekForGeeks** - [``https://www.geeksforgeeks.org/how-to-declare-variables-in-different-ways-in-javascript/``](https://www.geeksforgeeks.org/how-to-declare-variables-in-different-ways-in-javascript/)

### Import & Export

-**Import:**The static import statement is used to import read-only live bindings which are exported by another module.
Imported modules are in strict mode whether you declare them as such or not. The import statement cannot be used in embedded scripts unless such script has a type="module". Bindings imported are called live bindings because they are updated by the module that exported the binding.
  
  **Syntaxt** -
  
  ```bash 
import defaultExport from "module-name";
import * as name from "module-name";
import { export1 } from "module-name";
import { export1 as alias1 } from "module-name";
import { export1 , export2 } from "module-name";
import { export1 , export2 as alias2 , [...] } from "module-name";
import defaultExport, { export1 [ , [...] ] } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name";
var promise = import("module-name");
  ```

-**Export:**The export statement is used when creating JavaScript modules to export live bindings to functions, objects, or primitive values from the module so they can be used by other programs with the import statement. The value of an imported binding is subject to change in the module that exports it. When a module updates the value of a binding that it exports, the update will be visible in its imported value.
Exported modules are in strict mode whether you declare them as such or not. The export statement cannot be used in embedded scripts.
  
  **Syntaxt** -
  There are two types of exports:

  -Named Exports (Zero or more exports per module)
  
  -Default Exports (One per module)  
  
  ```bash 
// Exporting individual features
export let name1, name2, …, nameN; // also var, const
export let name1 = …, name2 = …, …, nameN; // also var, const
export function functionName(){...}
export class ClassName {...}

// Export list
export { name1, name2, …, nameN };

// Renaming exports
export { variable1 as name1, variable2 as name2, …, nameN };

// Exporting destructured assignments with renaming
export const { name1, name2: bar } = o;
export const [ name1, name2 ] = array;

// Default exports
export default expression;
export default function (…) { … } // also class, function*
export default function name1(…) { … } // also class, function*
export { name1 as default, … };

// Aggregating modules
export * from …; // does not set the default export
export * as name1 from …; // ECMAScript® 2O20
export { name1, name2, …, nameN } from …;
export { import1 as name1, import2 as name2, …, nameN } from …;
export { default, … } from …;

  ```

#### References
Please refer to the below references for more detail-

- **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
        
[``https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export``](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export)


### Callbacks

A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.
In other words, we can say that a function passed to another function as an argument is referred to as a callback function. The callback function runs after the completion of the outer function. It is useful to develop an asynchronous JavaScript code.
In JavaScript, a callback is easier to create. That is, we simply have to pass the callback function as a parameter to another function and call it right after the completion of the task. Callbacks are mainly used to handle the asynchronous operations such as the registering event listeners, fetching or inserting some data into/from the file, and many more.

**Syntaxt** -

```bash
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
```

#### References
Please refer to the below references for more detail-

- **MDN Resources** - [``https://developer.mozilla.org/en-US/docs/Glossary/Callback_function``](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)

- **JavaTPoint** - [``https://www.javatpoint.com/javascript-callback``](https://www.javatpoint.com/javascript-callback)

### Map & Reduce

-**Map:** The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.
`map()` calls a provided callbackFn function once for each element in an array, in order, and constructs a new array from the results. callbackFn is invoked only for indexes of the array which have assigned values (including undefined).
  
  **Syntaxt** -
  ```bash
  // Arrow function
map((element) => { /* ... */ })
map((element, index) => { /* ... */ })
map((element, index, array) => { /* ... */ })

// Callback function
map(callbackFn)
map(callbackFn, thisArg)

// Inline callback function
map(function(element) { /* ... */ })
map(function(element, index) { /* ... */ })
map(function(element, index, array){ /* ... */ })
map(function(element, index, array) { /* ... */ }, thisArg)

//Sample Code

const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```
-**Reduce:** The `reduce()` method executes a user-supplied "reducer" callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result of running the reducer across all elements of the array is a single value.
The first time that the callback is run there is no "return value of the previous calculation". If supplied, an initial value may be used in its place. Otherwise the array element at index 0 is used as the initial value and iteration starts from the next element (index 1 instead of index 0).
The reducer walks through the array element-by-element, at each step adding the current array value to the result from the previous step (this result is the running sum of all the previous steps) — until there are no more elements to add.



  **Syntaxt** -

  ```bash
  // Arrow function
reduce((previousValue, currentValue) => { /* ... */ } )
reduce((previousValue, currentValue, currentIndex) => { /* ... */ } )
reduce((previousValue, currentValue, currentIndex, array) => { /* ... */ } )
reduce((previousValue, currentValue, currentIndex, array) => { /* ... */ }, initialValue)

// Callback function
reduce(callbackFn)
reduce(callbackFn, initialValue)

// Inline callback function
reduce(function(previousValue, currentValue) { /* ... */ })
reduce(function(previousValue, currentValue, currentIndex) { /* ... */ })
reduce(function(previousValue, currentValue, currentIndex, array) { /* ... */ })
reduce(function(previousValue, currentValue, currentIndex, array) { /* ... */ }, initialValue)

//sample code

const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);

console.log(sumWithInitial);
// expected output: 10
  ```
#### References
Please refer to the below references for more detail-  
  - **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
        
[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

### Filter, Find & FindIndex

-**Filter:** The `filter()` method creates a new array with all elements that pass the test implemented by the provided function.
`filter()` calls a provided callbackFn function once for each element in an array, and constructs a new array of all the values for which callbackFn returns a value that coerces to true. callbackFn is invoked only for indexes of the array which have assigned values; it is not invoked for indexes which have been deleted or which have never been assigned values. Array elements which do not pass the callbackFn test are skipped, and are not included in the new array.


**Syntaxt** -

```bash
// Arrow function
filter((element) => { /* ... */ } )
filter((element, index) => { /* ... */ } )
filter((element, index, array) => { /* ... */ } )

// Callback function
filter(callbackFn)
filter(callbackFn, thisArg)

// Inline callback function
filter(function(element) { /* ... */ })
filter(function(element, index) { /* ... */ })
filter(function(element, index, array){ /* ... */ })
filter(function(element, index, array) { /* ... */ }, thisArg)

//Sample code
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

-**Find:**The `find()` method returns the first element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, undefined is returned.
The find method executes the callbackFn function once for each index of the array until the callbackFn returns a truthy value. If so, find immediately returns the value of that element. Otherwise, find returns undefined.

 **Syntax**
 ```bash
 // Arrow function
find((element) => { /* ... */ } )
find((element, index) => { /* ... */ } )
find((element, index, array) => { /* ... */ } )

// Callback function
find(callbackFn)
find(callbackFn, thisArg)

// Inline callback function
find(function(element) { /* ... */ })
find(function(element, index) { /* ... */ })
find(function(element, index, array){ /* ... */ })
find(function(element, index, array) { /* ... */ }, thisArg)

//Sample Code
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// expected output: 12
 ```
-**FindIndex:**The `findIndex()` method returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test.
The `findIndex()` method executes the callbackFn function once for every index in the array until it finds the one where callbackFn returns a truthy value.
If such an element is found, findIndex() immediately returns the element's index. If callbackFn never returns a truthy value (or the array's length is 0), findIndex() returns -1.

  **Syntax**
  ```bash
  // Arrow function
findIndex((element) => { /* ... */ } )
findIndex((element, index) => { /* ... */ } )
findIndex((element, index, array) => { /* ... */ } )

// Callback function
findIndex(callbackFn)
findIndex(callbackFn, thisArg)

// Inline callback function
findIndex(function(element) { /* ... */ })
findIndex(function(element, index) { /* ... */ })
findIndex(function(element, index, array){ /* ... */ })
findIndex(function(element, index, array) { /* ... */ }, thisArg)

//Sample Code
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// expected output: 3
  ```
#### References
Please refer to the below references for more detail-  
- **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
        
[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

### Arrow Functions & Hoisting

-**Arrow Functions (Expressions):** An arrow function expression is a compact alternative to a traditional function expression, but is limited and can't be used in all situations.
There are differences between arrow functions and traditional functions, as well as some limitations:

 - Arrow functions don't have their own bindings to this, arguments or super, and should not be used as methods.
 - Arrow functions don't have access to the new.target keyword.
 - Arrow functions aren't suitable for call, apply and bind methods, which generally rely on establishing a scope.
 - A rrow functions cannot be used as constructors.
 - Arrow functions cannot use yield, within its body.

**Syntax**
```bash
// Traditional Anonymous Function
function (a){
  return a + 100;
}

// Arrow Function Break Down

// 1. Remove the word "function" and place arrow between the argument and opening body bracket
(a) => {
  return a + 100;
}

// 2. Remove the body braces and word "return" -- the return is implied.
(a) => a + 100;

// 3. Remove the argument parentheses
a => a + 100;

//Sample Code
const materials = [
  'Hydrogen',
  'Helium',
  'Lithium',
  'Beryllium'
];

console.log(materials.map(material => material.length));
// expected output: Array [8, 6, 7, 9]
```

-**Hoisting:** JavaScript Hoisting refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.

Hoisting allows functions to be safely used in code before they are declared.

Variable and class declarations are also hoisted, so they too can be referenced before they are declared. Note that doing so can lead to unexpected errors, and is not generally recommended.

 - Function Hoisting
 One of the advantages of hoisting is that it lets you use a function before you declare it in your code.

 **Syntax**
```bash
 catName("Tiger");

function catName(name) {
  console.log("My cat's name is " + name);
}
/*
The result of the code above is: "My cat's name is Tiger"
*/

//Without hoisting you would have to write the same code like this:

function catName(name) {
  console.log("My cat's name is " + name);
}

catName("Tiger");
/*
The result of the code above is the same: "My cat's name is Tiger"
*/
```

 - Variable Hoisting
 Hoisting works with variables too, so you can use a variable in code before it is declared and/or initialized.
 However JavaScript only hoists declarations, not initializations! This means that initialization doesn't happen until the associated line of code is executed, even if the variable was originally initialized then declared, or declared and initialized in the same line.
 Until that point in the execution is reached the variable has its default initialization (undefined for a variable declared using var, otherwise uninitialized).

 **Syntax**
```bash
console.log(num); // Returns 'undefined' from hoisted var declaration (not 6)
var num; // Declaration
num = 6; // Initialization
console.log(num); // Returns 6 after the line with initialization is executed.

//The same thing happens if we declare and initialize the variable in the same line.

console.log(num); // Returns 'undefined' from hoisted var declaration (not 6)
var num = 6; // Initialization and declaration.
console.log(num); // Returns 6 after the line with initialization is executed.
```
#### References
Please refer to the below references for more detail-

- **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
        
[``https://developer.mozilla.org/en-US/docs/Glossary/Hoisting``](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)

### Promises, Async & Await

-**Promise:** The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.
A Promise is a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, the asynchronous method returns a promise to supply the value at some point in the future.

A Promise is in one of these states:

- pending: initial state, neither fulfilled nor rejected.
- fulfilled: meaning that the operation was completed successfully.
- rejected: meaning that the operation failed.

**Syntax**
```bash
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('foo');
  }, 300);
});

myPromise
  .then(handleResolvedA, handleRejectedA)
  .then(handleResolvedB, handleRejectedB)
  .then(handleResolvedC, handleRejectedC)
```

-**Async:**An async function is a function declared with the async keyword, and the await keyword is permitted within it. The async and await keywords enable asynchronous, promise-based behavior to be written in a cleaner style, avoiding the need to explicitly configure promise chains.

**Syntax**
```bash
async function name([param[, param[, ...param]]]) {
   statements
}

//Sample Code
function resolveAfter2Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved');
    }, 2000);
  });
}

async function asyncCall() {
  console.log('calling');
  const result = await resolveAfter2Seconds();
  console.log(result);
  // expected output: "resolved"
}

asyncCall();
```
-**Await:**The await operator is used to wait for a Promise. It can only be used inside an async function within regular JavaScript code; however it can be used on its own with JavaScript modules.
The await expression causes async function execution to pause until a Promise is settled (that is, fulfilled or rejected), and to resume execution of the async function after fulfillment. When resumed, the value of the await expression is that of the fulfilled Promise.

**Syntax**
```bash
[rv] = await expression
//Sample Code
function resolveAfter2Seconds(x) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(x);
    }, 2000);
  });
}

async function f1() {
  var x = await resolveAfter2Seconds(10);
  console.log(x); // 10
}

f1();
```
#### References
Please refer to the below references for more detail-

- **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
        
[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)

### Spread Operator

`Spread syntax (...)` allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

**Syntax**
```bash
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers));
// expected output: 6

console.log(sum.apply(null, numbers));
// expected output: 6
```
#### References
Please refer to the below references for more detail-

- **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

### Property Shorthand, Destructuring, Spread Operator

-**Property Shorthand:**Objects in JavaScript are the most important data-type and forms the building blocks for modern JavaScript. These objects are quite different from JavaScript primitive data-types (Number, String, Boolean, null, undefined, and symbol) in the sense that while these primitive data-types all store a single value each (depending on their types).

The shorthand syntax for object property value is very popular and widely used nowadays. The code looks cleaner and easy to read. The shorthand property makes the code size smaller and simpler.

**Syntax**
```bash
// Object property shorthand
const name = 'Raj'
const age = 20
const location = 'India'
  
// User with ES6 shorthand
// property 
const user = {
    name,      
    age,
    location
}
  
console.log(user) 
//Output
{name:'Raj',age:20,location:'India'}
```
-**Destructuring**
The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

**Syntax**
```bash
let a, b, rest;
[a, b] = [10, 20];
console.log(a); // 10
console.log(b); // 20

[a, b, ...rest] = [10, 20, 30, 40, 50];
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]

({ a, b } = { a: 10, b: 20 });
console.log(a); // 10
console.log(b); // 20

// Stage 4(finished) proposal
({a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40});
console.log(a); // 10
console.log(b); // 20
console.log(rest); // {c: 30, d: 40}

//Sample Code
let a, b, rest;
[a, b] = [10, 20];

console.log(a);
// expected output: 10

console.log(b);
// expected output: 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest);
// expected output: Array [30,40,50]
```

-**Spread Operator**
`Spread syntax (...)` allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

**Syntax**
```bash
myFunction(...iterableObj); // pass all elements of iterableObj as arguments to function myFunction

//Sample Code
function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers));
// expected output: 6

console.log(sum.apply(null, numbers));
// expected output: 6
```
#### References
Please refer to the below references for more detail-

- **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

- **GeekForGeeks Resources**-

[``https://www.geeksforgeeks.org/shorthand-syntax-for-object-property-value-in-es6/``](https://www.geeksforgeeks.org/shorthand-syntax-for-object-property-value-in-es6/)

### '?.' , '&&' And '??' Operators

-**'?.' (Optional Chaining Operator):**The `optional chaining operator (?.)` enables you to read the value of a property located deep within a chain of connected objects without having to check that each reference in the chain is valid.

The ?. operator is like the . chaining operator, except that instead of causing an error if a reference is nullish (null or undefined), the expression short-circuits with a return value of undefined. When used with function calls, it returns undefined if the given function does not exist.

The optional chaining operator provides a way to simplify accessing values through connected objects when it's possible that a reference or function may be undefined or null.

**Syntax**
```bash
obj.val?.prop
obj.val?.[expr]
obj.arr?.[index]
obj.func?.(args)

//Sample Code
const adventurer = {
  name: 'Alice',
  cat: {
    name: 'Dinah'
  }
};

const dogName = adventurer.dog?.name;
console.log(dogName);
// expected output: undefined

console.log(adventurer.someNonExistentMethod?.());
// expected output: undefined
```

-**'&&' (Logical AND Operator):**The logical `AND (&&)` operator (logical conjunction) for a set of boolean operands will be true if and only if all the operands are true. Otherwise it will be false.

More generally, the operator returns the value of the first falsy operand encountered when evaluating from left to right, or the value of the last operand if they are all truthy.

**Syntax**
```bash
expr1 && expr2

//Sample Code
const a = 3;
const b = -2;

console.log(a > 0 && b > 0);
// expected output: false
```

-**'??' (Nullish Coalescing Operator):**The nullish coalescing operator (??) is a logical operator that returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand.

**Syntax**
```bash
leftExpr ?? rightExpr

//Sample Code
const foo = null ?? 'default string';
console.log(foo);
// expected output: "default string"

const baz = 0 ?? 42;
console.log(baz);
// expected output: 0
```

#### References
Please refer to the below references for more detail-

- **MDN Resources** - 

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining)

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND)

[``https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator``](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator)














