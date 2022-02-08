
## execution contexts and lexical environments 

- A **Lexical Environment** is a specification type used to define the association of Identifiers to specific variables and functions based upon the lexical nesting structure of ECMAScript code. A Lexical Environment consists of an Environment Record and a possibly null reference to an ***outer Lexical Environment***.

in simple words : the place where we written phiscly in the code determen how the js engne will deside where things live and where things will be in the memory , and how things conect with each other 

- global environment and object 

---

```
let x = 10;

function timesTen(a){
    return a * 10;
}

let y = timesTen(x);

console.log(y);

```
- execution context (to understand hoisting)

  - The creation phase 
    - Create the global object i.e., window in the web browser or global in Node.js.
    - Create the this object and bind it to the global object.
    - Setup a memory heap for storing variables and function references.
    - Store the function declarations in the memory heap and variables within the global execution context with the initial values as undefined.

    ![](https://www.javascripttutorial.net/wp-content/uploads/2019/12/javascript-execution-context-global-execution-context-in-creation-phase.png)

  - The execution phase     
    the JavaScript engine executes the code line by line, assigns the values to variables, and executes the function calls.

    ![](https://www.javascripttutorial.net/wp-content/uploads/2019/12/javascript-execution-context-global-execution-context-in-execution-phase.png)

what about functions ?? (it prings out scopes)

For ***each function call***, the JavaScript engine creates a new function execution context.


- The function execution context is similar to the global execution context. But instead of creating the global object, the JavaScript engine creates the arguments object that is a reference to all the parameters of the function

![](https://www.javascripttutorial.net/wp-content/uploads/2019/12/javascript-execution-context-function-execution-context-in-creation-phase.png)

![](https://www.javascripttutorial.net/wp-content/uploads/2019/12/javascript-execution-context-function-execution-context-in-execution-phase.png)

- To keep track of all the execution contexts, including the global execution context and function execution contexts, the JavaScript engine uses the ***call stack (execution stack)***(last-in-first-out)

---

```
function add(a, b) {
  return a + b;
}

function average(a, b) {
  return add(a, b) / 2;
}

let x = average(10, 20);

```
![](https://www.javascripttutorial.net/wp-content/uploads/2019/12/JavaScript-Call-Stack.png)


```
function fn() {
    fn();
}

fn(); // stack overflow
```
---
scope chain and varible environments and Lexical environments 

```
function b() {
	console.log(myVar);
}

function a() {
	var myVar = 2;
	b();
}

var myVar = 1;
a();
```
***outer Lexical Environment*** 


the output is 1 

why ? 
when we are asking for a varible it will look for it in the current excution context then it will look to the outter  (reffrence )Lexical Environment in this case its the globel, function b is in the globle level same level as myVar = 1;    

this is called the ***scope chain***   
![](./imgs/000.PNG)

```
function a() {
  function b() {
    console.log(myVar);
  }
  var myVar = 2;
    
	b();
}

var myVar = 1;
a();
b();
```

the output is `2` and `ReferenceError : b is not defind `

![](./imgs/001.PNG)

that is how scopes formed 


---
## types and operators 

js uses dynamic typing 

