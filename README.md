# jsLecture


---

### Week 1: Advanced JavaScript Concepts
**Day 1-2: Scope and Closures**
- Understand lexical scope and closures.
- Practice exercises on closures.

**Day 3: Hoisting**
- Learn how hoisting works for variables and functions.
- Practice examples and understand common pitfalls.

**Day 4-5: Event Loop and Asynchronous Programming**
- Understand the event loop, call stack, and task queue.
- Learn about asynchronous programming and callbacks.
- Practice exercises with setTimeout and setInterval.

**Day 6-7: Prototypes and Inheritance**
- Learn about prototypes and prototype chains.
- Understand inheritance in JavaScript.
- Practice creating objects with prototypes.

### Week 2: ES6+ Features
**Day 8: Let, Const, and Block Scoping**
- Learn the differences between var, let, and const.
- Understand block scoping.

**Day 9: Arrow Functions and Template Literals**
- Learn about arrow functions and their syntax.
- Understand template literals and their usage.

**Day 10: Destructuring Assignment**
- Learn about destructuring arrays and objects.
- Practice examples.

**Day 11: Rest and Spread Operators**
- Understand the rest and spread operators.
- Practice using them in different scenarios.

**Day 12-13: Promises and Async/Await**
- Learn about promises and how to handle asynchronous operations.
- Understand async/await syntax.
- Practice exercises.

**Day 14: Review and Practice**
- Review all ES6+ features covered.
- Solve coding challenges related to ES6+ features.

### Week 3: DOM Manipulation
**Day 15-16: Selecting and Modifying Elements**
- Learn how to select elements in the DOM.
- Practice modifying DOM elements.

**Day 17-18: Event Handling**
- Understand how to handle events.
- Practice adding and removing event listeners.

**Day 19: Creating and Removing Elements**
- Learn how to create and remove elements in the DOM.
- Practice examples.

**Day 20-21: Advanced DOM Manipulation Techniques**
- Learn about event delegation.
- Understand throttling and debouncing.
- Practice exercises.

### Week 4: Fetch API and AJAX
**Day 22-23: Introduction to Fetch API**
- Learn how to use the Fetch API.
- Practice fetching data from APIs.

**Day 24: Handling Responses and Errors**
- Understand how to handle responses.
- Learn about error handling in Fetch API.

**Day 25: XMLHttpRequest**
- Learn about XMLHttpRequest for AJAX.
- Practice examples.

**Day 26: Review and Practice**
- Review Fetch API and AJAX concepts.
- Solve coding challenges related to fetching and handling data.

### Week 5: Modern JavaScript Frameworks Overview
**Day 27-28: Introduction to React**
- Learn the basics of React.
- Practice creating a simple React app.

**Day 29: Introduction to Vue.js**
- Learn the basics of Vue.js.
- Practice creating a simple Vue.js app.

**Day 30: Introduction to Angular**
- Learn the basics of Angular.
- Practice creating a simple Angular app.

### Additional Weeks (Optional)
**Week 6: JavaScript Design Patterns**
- **Day 31: Module Pattern**
- **Day 32: Observer Pattern**
- **Day 33: Singleton Pattern**
- **Day 34: Factory Pattern**
- **Day 35-36: Practice and Implement Patterns**

**Week 7: Testing and Debugging**
- **Day 37-38: Unit Testing with Jest**
- **Day 39-40: Debugging Techniques**
- **Day 41-42: Console Tricks and Practice**

**Week 8: Performance Optimization**
- **Day 43-44: Minification and Bundling**
- **Day 45: Lazy Loading**
- **Day 46: Code Splitting**
- **Day 47: Caching**
- **Day 48-49: Practice and Optimize Projects**

**Week 9: Final Project**
- **Day 50-54: Build a Full-Fledged Project**
- **Day 55: Code Review and Refactor**
- **Day 56: Documentation**

---
### Day 1: Advanced JavaScript Concepts - Scope and Closures

#### Scope
1. **Lexical Scope**:
    - Lexical scope refers to the accessibility of variables based on their physical location within the source code.
    - JavaScript uses lexical scoping to manage variable visibility and lifetimes.

    ```javascript
    function outerFunction() {
        let outerVariable = 'I am outside!';
        
        function innerFunction() {
            console.log(outerVariable); // Can access outerVariable
        }
        
        innerFunction();
    }

    outerFunction(); // Logs: 'I am outside!'
    ```

2. **Global vs Local Scope**:
    - Global scope: Variables declared outside any function are in the global scope.
    - Local scope: Variables declared within a function are in the local scope of that function.

    ```javascript
    let globalVar = 'I am global';

    function myFunction() {
        let localVar = 'I am local';
        console.log(globalVar); // Can access globalVar
        console.log(localVar);  // Can access localVar
    }

    myFunction();
    console.log(localVar);  // Error: localVar is not defined
    ```

#### Closures
1. **Definition**:
    - A closure is a function that retains access to its lexical scope, even when the function is executed outside that scope.

    ```javascript
    function makeCounter() {
        let count = 0;
        
        return function() {
            count++;
            return count;
        };
    }

    const counter = makeCounter();
    console.log(counter()); // 1
    console.log(counter()); // 2
    ```

2. **Use Cases**:
    - **Encapsulation**: Closures allow you to create private variables and methods.
    - **Callbacks**: Often used in event handlers, setTimeout, setInterval, etc.

    ```javascript
    function createGreeting(greeting) {
        return function(name) {
            console.log(`${greeting}, ${name}!`);
        };
    }

    const sayHello = createGreeting('Hello');
    sayHello('Alice'); // 'Hello, Alice!'
    sayHello('Bob');   // 'Hello, Bob!'
    ```

#### Practice Exercises
1. **Exercise 1: Lexical Scope**

    ```javascript
    function outer() {
        let a = 1;
        
        function inner() {
            let b = 2;
            console.log(a + b); // Should print 3
        }
        
        inner();
    }
    
    outer();
    ```

2. **Exercise 2: Closures**

    ```javascript
    function multiplier(factor) {
        return function(number) {
            return number * factor;
        };
    }

    const double = multiplier(2);
    console.log(double(5)); // Should print 10

    const triple = multiplier(3);
    console.log(triple(5)); // Should print 15
    ```

3. **Exercise 3: Private Variables with Closures**

    ```javascript
    function createCounter() {
        let count = 0;
        
        return {
            increment() {
                count++;
                return count;
            },
            decrement() {
                count--;
                return count;
            },
            getCount() {
                return count;
            }
        };
    }

    const counter = createCounter();
    console.log(counter.increment()); // Should print 1
    console.log(counter.increment()); // Should print 2
    console.log(counter.decrement()); // Should print 1
    console.log(counter.getCount());  // Should print 1
    ```

### Summary
- **Lexical Scope**: Understand how variable scope is determined by the physical placement of the code.
- **Closures**: Learn how functions can retain access to their lexical scope, providing powerful ways to manage state and create private variables.

---
### Day 2: Advanced JavaScript Concepts - Hoisting

#### Hoisting
1. **Definition**:
    - Hoisting is JavaScript's default behavior of moving declarations to the top of the current scope (script or function) during the compile phase.
    - Only declarations are hoisted, not initializations.

2. **Variable Hoisting**:
    - Variables declared with `var` are hoisted to the top of their containing function or script.
    - `let` and `const` variables are also hoisted but are not initialized until their definition is evaluated. This results in a "temporal dead zone" where accessing them before declaration throws an error.

    ```javascript
    console.log(a); // undefined
    var a = 5;
    console.log(a); // 5

    console.log(b); // ReferenceError: Cannot access 'b' before initialization
    let b = 10;
    console.log(b); // 10
    ```

3. **Function Hoisting**:
    - Function declarations are hoisted to the top of their scope and can be called before they are defined in the code.
    - Function expressions are not hoisted.

    ```javascript
    hoistedFunction(); // "This function is hoisted"

    function hoistedFunction() {
        console.log("This function is hoisted");
    }

    nonHoistedFunction(); // TypeError: nonHoistedFunction is not a function

    var nonHoistedFunction = function() {
        console.log("This function is not hoisted");
    };
    ```

4. **Class Hoisting**:
    - Classes declared with `class` are hoisted but similar to `let` and `const`, they are not initialized until evaluated.

    ```javascript
    const instance = new MyClass(); // ReferenceError: Cannot access 'MyClass' before initialization

    class MyClass {
        constructor() {
            console.log("MyClass instance created");
        }
    }
    ```

#### Practice Exercises
1. **Exercise 1: Variable Hoisting with `var`**

    ```javascript
    console.log(x); // undefined
    var x = 10;
    console.log(x); // 10

    function testVarHoisting() {
        console.log(y); // undefined
        var y = 20;
        console.log(y); // 20
    }

    testVarHoisting();
    ```

2. **Exercise 2: Variable Hoisting with `let` and `const`**

    ```javascript
    try {
        console.log(a); // ReferenceError
        let a = 5;
    } catch (e) {
        console.log(e.message); // "Cannot access 'a' before initialization"
    }

    try {
        console.log(b); // ReferenceError
        const b = 10;
    } catch (e) {
        console.log(e.message); // "Cannot access 'b' before initialization"
    }
    ```

3. **Exercise 3: Function Hoisting**

    ```javascript
    hoistedFunc(); // "Hoisted Function"

    function hoistedFunc() {
        console.log("Hoisted Function");
    }

    try {
        nonHoistedFunc(); // TypeError
    } catch (e) {
        console.log(e.message); // "nonHoistedFunc is not a function"
    }

    var nonHoistedFunc = function() {
        console.log("Non-Hoisted Function");
    };
    ```

4. **Exercise 4: Class Hoisting**

    ```javascript
    try {
        const myInstance = new MyClass(); // ReferenceError
    } catch (e) {
        console.log(e.message); // "Cannot access 'MyClass' before initialization"
    }

    class MyClass {
        constructor() {
            console.log("MyClass instance created");
        }
    }

    const myInstance = new MyClass(); // "MyClass instance created"
    ```

### Summary
- **Hoisting**: Understand how variable and function declarations are moved to the top of their scope.
- **Variables**: Recognize the differences in hoisting behavior between `var`, `let`, and `const`.
- **Functions and Classes**: Learn how function declarations and class definitions are hoisted.

