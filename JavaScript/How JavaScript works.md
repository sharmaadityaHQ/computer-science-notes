## How JavaScript works?

- JavaScript is a synchronous single threaded language. Only executes 1 command at a time in a specific order. Next line is executed once the current line has been executed.

- JS is a loosely typed language. You do not have to specify variable types in code.

- Everything in JavaScript happens inside an execution context.
- Execution context is like a big box with 2 components:-  
    1. Memory component or Variable environment - Variables and functions are stored as key-value pairs.
    2. Code component or Thread of Execution - Place where JS code is executed 1 line at a time.

        ![](../assets/execution-context.png)

- Execution context is created in 2 phases:-  
    1. Memory Allocation Phase - Memory is allocated to all variables and functions. `key` as variable name and `value` as undefined in case of variables and `key` as function name and `value` as code of the function in case of functions.
    2. Code Execution Phase - Value of variables is allocated in memory and code is executed in code component. In case of function invocations a new execution context is created. This new execution context is deleted after the function returns and its execution is complete. Global execution context is also deleted when the code execution is complete.

- Call Stack (execution context stack/program stack/control stack/runtime stack/machine stack) maintains the order of execution of execution contexts.
    1. Global execution context is pushed to call stack when any JS program is run.
    2. When a new execution context is created on function invocation it is pushed to call stack and popped out after execution is complete.
    3. Call stack is empty when execution of all JS code is complete.

- Hoisting
    1. Process where compiler allocates memory for variable and function declarations before the execution of the code.
    2. Declarations made using `let` and `const` are not initialized as part of hoisting. Until the line in which they are initialized is executed, any code that accesses these variables will throw an exception.

- `window` object
    1. `window` is a global object which is created by the JS engine along with the global execution context.
    2. A `this` variable is also created which points to the global object (`window` in case of browsers). (`this` === `window`)
    3. All variables and functions created in the global scope get attached to the `window` object. Eg. A variable `a` can be accessed as `window.a` or `a` or `this.a`. (`let` and `const` declarations are exceptions)

- Lexical environment
    1. Lexical environment is a specification object which only exists theoretically in the language specification to describe how things work.  We can’t get this object in our code and manipulate it directly.
    2. Lexical environment is created whenenever an execution context is created. Lexical environment = Local memory + reference to lexical environment of parent.
    3. Scope means area where you can access a specific variable or function in code.
    4. If JS engine does not find a variable in the local memory then it searches in the next level of scope chain (chain of lexical environments).

- Temporal Dead Zone (`TDZ`), `let` and `const`
    1. Time from when a `let`/`const` declaration is hoisted till the time it is initialized.
    2. Accessing a `let` variable before the initialization results in a `ReferenceError`.

    ```javascript
    { // TDZ starts at beginning of scope
        console.log(x); // undefined
        console.log(y); // ReferenceError
        var x = 1;
        let y = 2; // End of TDZ (for y)
    }
    ```

    3. `let` does not allow re-declaration in the same scope.
    4. `const` declarations have to be initialized in the same line. Assignment to constant variables gives `TypeError`.
    5. Best way to avoid `TDZ` is to have all declaration and initialization at the top of the file.
    6. `let` and `const` are block scoped. They are stored in a separate memory space which is reserved for that block. They are not added to the global `window` object.
    7. `var` variables are function scoped. They are only available inside the function they are created in, or if not created inside a function, they are globally scoped.

    ```javascript
    {
        var a = 10;
        let b = 20;
        const c = 30;
        console.log(a); // 10
        console.log(b); // 20
        console.log(c); // 30
    }
    console.log(a); // 10
    console.log(b); // ReferenceError: b is not defined
    console.log(c);
    ```

- Shadowing
    1. When a variable is declared in a certain scope having the same name defined on its outer scope and when we use the variable from the inner scope, the value assigned to the variable in the inner scope is the value that will be stored in the variable in the memory space.
    2. Illegal Shadowing - While shadowing a variable, it should not cross the boundary of the scope. We can shadow `var` variable by `let` variable but cannot do the opposite.

    ```javascript
    function func() {
        var a = 1;
        let b = 2;
        
        if (true) {
            let a = 3; // Legal Shadowing
            var b = 4; // Illegal Shadowing
            console.log(a); // 3
            console.log(b); // SyntaxError: b has already been declared
        }
    }
    func();
    ```

- Closures
    1. A function along with its lexical environment is called closure. When we return a function a closure is returned.

    ```javascript
    function x() {
        var a = 7;
        function y() {
            console.log(a);
        }
        return y;
    }
    var z = x();
    z(); // 7
    ```

    2. Closures are created every time a function is created, at function creation time.
    3. Function arguments are always passed by value. All objects interact with reference.
    4. Common uses of closures
        - Module Design Pattern
        - Currying
        - Functions like `once`
        - memoize
        - maintaining state in `async` world
        - setTimeout
        - Iterators
    5. Closures might lead to over consumption of memory as every time a clousre is formed it consumes a lot of memory and those variables are not garbage collected. It can also lead to memory leaks, freeze browser if not handled properly.
    6. Garbage collector is a part of JS engine which frees up the unutilized memory. Modern JS engines smartly garbage collect code which is not being used.
    7. Closures can be used for data privacy/data hiding.

    ```javascript
    function counter(){
        var count = 0; // count is a private variable
        return function incrementCounter(){
            count++;
            console.log(count);
        }
    }
    var counter1 = counter();
    counter1();
    ```

- Functions
    1. Function Statement/Function Declaration

    ```javascript
        function a(){
            console.log('called a');
        }
        a();
    ```

    2. Function Expression

    ```javascript
        var b = function(){
            console.log('called b');
        }
        b();
    ```

    Function expression and function statement behave differently during hoisting. Function expression is similar to normal variable and is assigned `undefined` until the function expression code is executed.

    3. Anonymous Function - Do not have a name, can be used as values in function expressions.
    4. Named Function Expression

    ```javascript
        var b = function xyz(){
            console.log('called b');
        }
        xyz(); // ReferenceError: xyz is not defined
        b(); // called b
    ```

    5. Parameters are the values that a function can receive.

    ```javascript
        function a(param1, param2){
            console.log('called a');
        }
        a();
    ```

    6. Arguments are the values that are passed to a function.

    ```javascript
        a(10, 20);
    ```

    7. First Class Functions - The ability to use functions as values, pass them to other functions and return them from a function.
    8. Callback Function

    ```javascript
        function x(y){
            /*
                y is a callback function. It is passed to x
                and is called sometime later in the program.
            */
        }
        x(function y(){

        })
    ```
    9. Event listeners and clousres

    ```javascript
        function addEventListeners() {
            let count = 0;
            document.getElementById('clickMe').addEventListener('click', function xyz(){
                console.log('Click', count++);
            });
        }
        addEventListeners();
    ```

    Event listeners are heavy and are removed as they form closure and take up memory.

- Asynchronous JS and Event loop
    1. Call stack is present inside the JS engine and can only execute 1 thing at a time.
    2. Some frequently used Web API's :-
        - setTimeout()
        - DOM API's
        - fetch()
        - localStorage
        - console
        - location 

    We can use web api's inside our JS code via the global object (`window` in case of browsers). Eg. `window.setTimeout()` or `setTimeout()`

    3. Event loop continuously monitors the call stack and the callback queue. If call stack is empty and the callback queue has some function waiting to be exectuted then that function is pushed into the call stack.
    4. Microtask queue is similar to callback queue but has higher priority. All callback functions which come through promises, mutation observer go to microtask queue. All other callbacks from setTimeout, DOM API's go to the callback queue.
    5. Event loop will only pick tasks from callback queue once all tasks in the microtask queue are completed.
    6. If the task in the callback queue does not get the chance to execute for a long time due to multiple tasks in the microtask queue then it is called starvation of the task inside callback queue.
    7. Memory heap is the space where all variables and functions are assigned memory.


