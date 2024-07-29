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

---
### Day 3: Advanced JavaScript Concepts - Event Loop and Asynchronous Programming

#### Event Loop
1. **Definition**:
    - The event loop is a fundamental concept in JavaScript that allows for non-blocking asynchronous programming.
    - It enables JavaScript to perform tasks like handling events, executing callbacks, and processing asynchronous operations.

2. **Call Stack**:
    - The call stack is a data structure that keeps track of function calls.
    - When a function is called, it’s added to the top of the stack. When the function returns, it’s removed from the stack.

    ```javascript
    function foo() {
        console.log("foo");
    }

    function bar() {
        foo();
        console.log("bar");
    }

    bar(); // Logs: "foo", "bar"
    ```

3. **Event Queue**:
    - The event queue (or task queue) is where asynchronous events (like click events, timer callbacks) are queued to be processed by the event loop.
    - When the call stack is empty, the event loop processes the next event in the queue.

    ```javascript
    console.log("Start");

    setTimeout(() => {
        console.log("Timeout");
    }, 0);

    console.log("End");

    // Logs: "Start", "End", "Timeout"
    ```

4. **Event Loop Process**:
    - The event loop continuously checks if the call stack is empty.
    - If the call stack is empty, it takes the first event from the event queue and pushes it onto the call stack for execution.

    ```javascript
    console.log("Start");

    setTimeout(() => {
        console.log("Timeout 1");
    }, 0);

    setTimeout(() => {
        console.log("Timeout 2");
    }, 0);

    console.log("End");

    // Logs: "Start", "End", "Timeout 1", "Timeout 2"
    ```

#### Asynchronous Programming
1. **Callbacks**:
    - A callback is a function passed as an argument to another function to be executed later.

    ```javascript
    function fetchData(callback) {
        setTimeout(() => {
            const data = { name: "John" };
            callback(data);
        }, 1000);
    }

    fetchData((data) => {
        console.log(data); // Logs: { name: "John" }
    });
    ```

2. **Promises**:
    - A promise represents a value that may be available now, or in the future, or never.
    - Promises have three states: pending, fulfilled, and rejected.

    ```javascript
    const promise = new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Success");
        }, 1000);
    });

    promise.then((value) => {
        console.log(value); // Logs: "Success"
    }).catch((error) => {
        console.error(error);
    });
    ```

3. **Async/Await**:
    - `async` and `await` provide a way to work with promises in a more synchronous fashion.
    - An `async` function always returns a promise.
    - The `await` keyword pauses the execution of the async function until the promise is resolved.

    ```javascript
    async function fetchData() {
        const promise = new Promise((resolve) => {
            setTimeout(() => {
                resolve("Data fetched");
            }, 1000);
        });

        const result = await promise;
        console.log(result); // Logs: "Data fetched"
    }

    fetchData();
    ```

#### Practice Exercises
1. **Exercise 1: Understanding the Event Loop**

    ```javascript
    console.log("First");

    setTimeout(() => {
        console.log("Second");
    }, 0);

    console.log("Third");

    // Logs: "First", "Third", "Second"
    ```

2. **Exercise 2: Using Callbacks**

    ```javascript
    function doHomework(subject, callback) {
        console.log(`Starting my ${subject} homework.`);
        callback();
    }

    doHomework('math', () => {
        console.log('Finished my homework');
    });

    // Logs: "Starting my math homework.", "Finished my homework"
    ```

3. **Exercise 3: Creating and Using Promises**

    ```javascript
    const myPromise = new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Promise resolved");
        }, 2000);
    });

    myPromise.then((message) => {
        console.log(message); // Logs: "Promise resolved"
    }).catch((error) => {
        console.error(error);
    });
    ```

4. **Exercise 4: Using Async/Await**

    ```javascript
    async function asyncFunction() {
        const promise = new Promise((resolve) => {
            setTimeout(() => {
                resolve("Async/Await resolved");
            }, 1500);
        });

        const result = await promise;
        console.log(result); // Logs: "Async/Await resolved"
    }

    asyncFunction();
    ```

### Summary
- **Event Loop**: Understand how the event loop processes the call stack and event queue.
- **Callbacks**: Learn how to handle asynchronous operations using callbacks.
- **Promises**: Understand the use of promises to manage asynchronous operations.
- **Async/Await**: Learn to write asynchronous code in a more readable and maintainable way using async/await.

---
### Day 4: Advanced JavaScript Concepts - Prototypes and Inheritance

#### Prototypes
1. **Definition**:
    - In JavaScript, every object has a prototype, which is also an object.
    - A prototype is a blueprint from which objects inherit properties and methods.

2. **Prototype Chain**:
    - The prototype chain is used to build an inheritance hierarchy.
    - Objects inherit from other objects, and this chain of inheritance is called the prototype chain.

    ```javascript
    const animal = {
        eats: true,
        walk() {
            console.log("Animal walks");
        }
    };

    const rabbit = {
        jumps: true,
        __proto__: animal
    };

    console.log(rabbit.eats); // true
    rabbit.walk(); // "Animal walks"
    ```

3. **Object.prototype**:
    - All objects in JavaScript inherit from `Object.prototype`.
    - This is the top of the prototype chain.

    ```javascript
    const obj = {};
    console.log(obj.toString()); // "[object Object]"
    console.log(obj.hasOwnProperty('toString')); // false
    ```

#### Inheritance
1. **Constructor Functions**:
    - Constructor functions are used to create multiple similar objects.
    - They use the `this` keyword to set properties of the created object.

    ```javascript
    function Animal(name) {
        this.name = name;
        this.eats = true;
    }

    Animal.prototype.walk = function() {
        console.log(`${this.name} walks`);
    };

    const rabbit = new Animal("Rabbit");
    console.log(rabbit.name); // "Rabbit"
    rabbit.walk(); // "Rabbit walks"
    ```

2. **ES6 Classes**:
    - ES6 introduced classes as a syntactic sugar over constructor functions and prototypes.
    - They provide a cleaner and more intuitive syntax for creating objects and dealing with inheritance.

    ```javascript
    class Animal {
        constructor(name) {
            this.name = name;
            this.eats = true;
        }

        walk() {
            console.log(`${this.name} walks`);
        }
    }

    class Rabbit extends Animal {
        constructor(name) {
            super(name);
            this.jumps = true;
        }
    }

    const rabbit = new Rabbit("Rabbit");
    console.log(rabbit.name); // "Rabbit"
    console.log(rabbit.eats); // true
    console.log(rabbit.jumps); // true
    rabbit.walk(); // "Rabbit walks"
    ```

#### Practice Exercises
1. **Exercise 1: Prototype Chain**

    ```javascript
    const vehicle = {
        hasEngine: true
    };

    const car = {
        hasWheels: true,
        __proto__: vehicle
    };

    const electricCar = {
        hasBattery: true,
        __proto__: car
    };

    console.log(electricCar.hasEngine); // true
    console.log(electricCar.hasWheels); // true
    console.log(electricCar.hasBattery); // true
    ```

2. **Exercise 2: Constructor Functions**

    ```javascript
    function Person(name, age) {
        this.name = name;
        this.age = age;
    }

    Person.prototype.greet = function() {
        console.log(`Hello, my name is ${this.name}`);
    };

    const john = new Person("John", 30);
    const jane = new Person("Jane", 25);

    john.greet(); // "Hello, my name is John"
    jane.greet(); // "Hello, my name is Jane"
    ```

3. **Exercise 3: ES6 Classes**

    ```javascript
    class Shape {
        constructor(color) {
            this.color = color;
        }

        describe() {
            return `A shape of color ${this.color}`;
        }
    }

    class Circle extends Shape {
        constructor(color, radius) {
            super(color);
            this.radius = radius;
        }

        area() {
            return Math.PI * this.radius * this.radius;
        }
    }

    const myCircle = new Circle("red", 10);
    console.log(myCircle.describe()); // "A shape of color red"
    console.log(myCircle.area()); // 314.159...
    ```

### Summary
- **Prototypes**: Understand how objects inherit properties and methods through the prototype chain.
- **Constructor Functions**: Learn to create objects using constructor functions.
- **ES6 Classes**: Use ES6 classes to create objects and handle inheritance in a more intuitive way.

---
### Day 5: Advanced JavaScript Concepts - Prototypes and Inheritance (Continued)

#### More on Prototypes
1. **Adding Methods to Prototypes**:
    - You can add methods to an object's prototype to ensure that all instances of that object share the same method, saving memory.

    ```javascript
    function Person(name) {
        this.name = name;
    }

    Person.prototype.greet = function() {
        console.log(`Hello, my name is ${this.name}`);
    };

    const alice = new Person("Alice");
    const bob = new Person("Bob");

    alice.greet(); // "Hello, my name is Alice"
    bob.greet();   // "Hello, my name is Bob"
    ```

2. **Prototype Property**:
    - The `prototype` property is available only on functions, as they are meant to be constructors.
    - Instances created using constructor functions have an internal `[[Prototype]]` property that links to the constructor's `prototype`.

    ```javascript
    function Animal() {}
    console.log(Animal.prototype); // {}

    const dog = new Animal();
    console.log(Object.getPrototypeOf(dog) === Animal.prototype); // true
    ```

3. **Prototype Inheritance**:
    - Objects can inherit properties and methods from other objects via the prototype chain.

    ```javascript
    const animal = {
        eats: true
    };

    const rabbit = Object.create(animal);
    rabbit.jumps = true;

    console.log(rabbit.eats);  // true
    console.log(rabbit.jumps); // true
    ```

#### Inheritance with Classes
1. **Class Inheritance**:
    - Classes in ES6 make inheritance more straightforward and readable.

    ```javascript
    class Animal {
        constructor(name) {
            this.name = name;
        }

        speak() {
            console.log(`${this.name} makes a noise`);
        }
    }

    class Dog extends Animal {
        constructor(name, breed) {
            super(name);
            this.breed = breed;
        }

        speak() {
            console.log(`${this.name} barks`);
        }
    }

    const myDog = new Dog("Buddy", "Golden Retriever");
    myDog.speak(); // "Buddy barks"
    ```

2. **Static Methods**:
    - Static methods are defined on the class itself, not on instances of the class.
    - They are called on the class, not on instances.

    ```javascript
    class MathHelper {
        static square(x) {
            return x * x;
        }
    }

    console.log(MathHelper.square(4)); // 16
    ```

#### Practice Exercises
1. **Exercise 1: Extending Prototypes**

    ```javascript
    function Car(brand) {
        this.brand = brand;
    }

    Car.prototype.drive = function() {
        console.log(`${this.brand} is driving`);
    };

    const tesla = new Car("Tesla");
    const bmw = new Car("BMW");

    tesla.drive(); // "Tesla is driving"
    bmw.drive();   // "BMW is driving"
    ```

2. **Exercise 2: Prototype Chain**

    ```javascript
    const person = {
        isHuman: false,
        printIntroduction() {
            console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
        }
    };

    const me = Object.create(person);
    me.name = "John";
    me.isHuman = true;

    me.printIntroduction(); // "My name is John. Am I human? true"
    ```

3. **Exercise 3: Class Inheritance**

    ```javascript
    class Vehicle {
        constructor(make) {
            this.make = make;
        }

        start() {
            console.log(`${this.make} vehicle started`);
        }
    }

    class Motorcycle extends Vehicle {
        constructor(make, type) {
            super(make);
            this.type = type;
        }

        start() {
            console.log(`${this.make} ${this.type} started`);
        }
    }

    const myBike = new Motorcycle("Yamaha", "Sport");
    myBike.start(); // "Yamaha Sport started"
    ```

4. **Exercise 4: Static Methods**

    ```javascript
    class Calculator {
        static add(a, b) {
            return a + b;
        }

        static subtract(a, b) {
            return a - b;
        }
    }

    console.log(Calculator.add(10, 5));    // 15
    console.log(Calculator.subtract(10, 5)); // 5
    ```

### Summary
- **Prototypes**: Extend objects by adding methods to their prototypes.
- **Prototype Chain**: Understand how objects inherit properties and methods via the prototype chain.
- **Class Inheritance**: Use ES6 classes for clearer and more readable inheritance.
- **Static Methods**: Define methods that belong to the class itself rather than instances of the class.
Spend one hour today studying these concepts, working through the provided examples, and completing the exercises
---
### Day 6: Advanced JavaScript Concepts - Closures and IIFE (Immediately Invoked Function Expressions)

#### Closures
1. **Definition**:
    - A closure is a function that retains access to its lexical scope, even when the function is executed outside that scope.
    - Closures are created whenever a function is created, at function creation time.

2. **Lexical Scope**:
    - Lexical scope means that a function can access variables from its outer (parent) scope, even after the parent function has finished executing.

    ```javascript
    function outerFunction() {
        const outerVariable = "I am outside!";
        
        function innerFunction() {
            console.log(outerVariable);
        }

        return innerFunction;
    }

    const myInnerFunction = outerFunction();
    myInnerFunction(); // Logs: "I am outside!"
    ```

3. **Practical Use Cases**:
    - **Data Privacy**: Closures can be used to create private variables and methods.
    - **Function Factories**: Create functions with pre-set arguments.
    - **Maintaining State**: Closures can maintain state between function calls.

    ```javascript
    // Data Privacy
    function createCounter() {
        let count = 0;
        return {
            increment: function() {
                count++;
                console.log(count);
            },
            decrement: function() {
                count--;
                console.log(count);
            },
            getCount: function() {
                return count;
            }
        };
    }

    const counter = createCounter();
    counter.increment(); // 1
    counter.increment(); // 2
    console.log(counter.getCount()); // 2

    // Function Factories
    function createMultiplier(multiplier) {
        return function(num) {
            return num * multiplier;
        };
    }

    const double = createMultiplier(2);
    const triple = createMultiplier(3);

    console.log(double(5)); // 10
    console.log(triple(5)); // 15

    // Maintaining State
    function createLogger(name) {
        return function(message) {
            console.log(`[${name}] ${message}`);
        };
    }

    const appLogger = createLogger("App");
    appLogger("Application started"); // [App] Application started
    ```

#### IIFE (Immediately Invoked Function Expressions)
1. **Definition**:
    - An IIFE is a function that runs as soon as it is defined.
    - It is a design pattern also known as a self-executing anonymous function.

    ```javascript
    (function() {
        console.log("This is an IIFE");
    })();
    ```

2. **Purpose and Benefits**:
    - **Encapsulation**: IIFE helps in creating a private scope, avoiding polluting the global scope.
    - **Module Pattern**: IIFE can be used to create modules, encapsulating related code together.
    - **Initialization**: IIFE can be used to initialize variables and execute code immediately.

    ```javascript
    // Encapsulation
    (function() {
        const privateVar = "I am private";
        console.log(privateVar); // Logs: "I am private"
    })();
    
    // privateVar is not accessible here
    // console.log(privateVar); // ReferenceError

    // Module Pattern
    const myModule = (function() {
        const moduleVariable = "Module variable";

        function moduleMethod() {
            console.log(moduleVariable);
        }

        return {
            publicMethod: moduleMethod
        };
    })();

    myModule.publicMethod(); // Logs: "Module variable"
    ```

3. **Syntax Variations**:
    - IIFE can be written using different syntax variations, but they all achieve the same goal of immediate execution.

    ```javascript
    // Function Expression
    (function() {
        console.log("IIFE with function expression");
    })();

    // Arrow Function
    (() => {
        console.log("IIFE with arrow function");
    })();

    // Named Function Expression
    (function namedIIFE() {
        console.log("Named IIFE");
    })();
    ```

#### Practice Exercises
1. **Exercise 1: Simple Closure**

    ```javascript
    function greet(name) {
        const greeting = "Hello, " + name;
        return function() {
            console.log(greeting);
        };
    }

    const greetJohn = greet("John");
    greetJohn(); // Logs: "Hello, John"
    ```

2. **Exercise 2: Closure with Private Variables**

    ```javascript
    function bankAccount(initialBalance) {
        let balance = initialBalance;
        return {
            deposit: function(amount) {
                balance += amount;
                console.log(`Deposited: $${amount}, New Balance: $${balance}`);
            },
            withdraw: function(amount) {
                if (amount <= balance) {
                    balance -= amount;
                    console.log(`Withdrew: $${amount}, New Balance: $${balance}`);
                } else {
                    console.log(`Insufficient funds. Current Balance: $${balance}`);
                }
            },
            getBalance: function() {
                return balance;
            }
        };
    }

    const myAccount = bankAccount(100);
    myAccount.deposit(50); // Deposited: $50, New Balance: $150
    myAccount.withdraw(30); // Withdrew: $30, New Balance: $120
    console.log(myAccount.getBalance()); // 120
    ```

3. **Exercise 3: IIFE for Encapsulation**

    ```javascript
    (function() {
        const privateVar = "Encapsulated variable";
        function privateFunction() {
            console.log(privateVar);
        }
        privateFunction(); // Logs: "Encapsulated variable"
    })();
    ```

4. **Exercise 4: Module Pattern with IIFE**

    ```javascript
    const calculatorModule = (function() {
        let result = 0;

        function add(num) {
            result += num;
            return result;
        }

        function subtract(num) {
            result -= num;
            return result;
        }

        function multiply(num) {
            result *= num;
            return result;
        }

        function divide(num) {
            if (num !== 0) {
                result /= num;
                return result;
            } else {
                console.log("Cannot divide by zero");
                return result;
            }
        }

        function getResult() {
            return result;
        }

        return {
            add,
            subtract,
            multiply,
            divide,
            getResult
        };
    })();

    console.log(calculatorModule.add(5)); // 5
    console.log(calculatorModule.multiply(2)); // 10
    console.log(calculatorModule.subtract(4)); // 6
    console.log(calculatorModule.divide(3)); // 2
    console.log(calculatorModule.getResult()); // 2
    ```

### Summary
- **Closures**: Understand how functions retain access to their lexical scope.
- **Lexical Scope**: Learn how variables from the parent scope are accessible in the child function.
- **Practical Uses of Closures**: Data privacy, function factories, and maintaining state.
- **IIFE**: Create functions that execute immediately to encapsulate code and avoid polluting the global scope.
- **Module Pattern**: Use IIFE to create self-contained modules.

Spend one hour today studying these concepts, working through the provided examples, and completing the exercises.

