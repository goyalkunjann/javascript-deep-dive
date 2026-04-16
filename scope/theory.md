# JavaScript Scope (Deep Dive)

---

## What is Scope?

Scope defines where variables are accessible in a program.

In simple terms, scope determines which parts of code can access a variable.

---

## Why Scope is Important

- Controls variable accessibility  
- Prevents naming conflicts  
- Helps write predictable and maintainable code  
- Foundation for closures and execution context  

---

# Types of Scope

---

## 1. Global Scope

Variables declared outside any function or block belong to global scope.

```js
var a = 10;

function test() {
  console.log(a); // 10
}
```

### Key Points

- Accessible throughout the program  
- Stored in the global object (window in browser)  
- Overuse can lead to conflicts  

---

## 2. Function Scope

Variables declared inside a function are accessible only within that function.

```js
function test() {
  var b = 20;
  console.log(b); // 20
}

test();
```

### Key Points

- `var` is function scoped  
- Not accessible outside the function  
- Each function creates its own scope  

---

## 3. Block Scope

Variables declared using `let` and `const` inside `{}` are block scoped.

```js
{
  let x = 10;
  const y = 20;
}
```

### Key Points

- Introduced in ES6  
- Accessible only within the block  
- Safer than `var`  

---

# var vs let vs const (Scope Perspective)

| Keyword | Scope Type | Re-declare | Re-assign |
|--------|-----------|-----------|-----------|
| var    | Function  | Yes       | Yes       |
| let    | Block     | No        | Yes       |
| const  | Block     | No        | No        |

---

# Lexical Scope

Scope is determined by where the code is written, not where it is executed.

```js
function outer() {
  let a = 10;

  function inner() {
    console.log(a);
  }

  return inner;
}

outer()(); // 10
```

### Key Points

- Also called static scope  
- Defined at code writing time  
- Used in closures  

---

# Scope Chain

If a variable is not found in the current scope, JavaScript looks in the outer scope.

```js
let a = 1;

function outer() {
  let b = 2;

  function inner() {
    console.log(a, b);
  }

  inner();
}

outer();
```

### Key Points

- Lookup happens upward  
- Stops at global scope  
- If not found → ReferenceError  

---

# Shadowing

When a variable in an inner scope overrides a variable in an outer scope.

```js
let a = 10;

function test() {
  let a = 20;
  console.log(a); // 20
}
```

---

## Illegal Shadowing

```js
let a = 10;

function test() {
  var a = 20; // Error
}
```

---

# Scope in Loops

## Using var

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
// 3 3 3
```

Same variable reference is used.

---

## Using let

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
// 0 1 2
```

A new variable is created for each iteration.

---

# Scope vs Execution Context

| Scope                                  | Execution Context         |
|---------------------------------------|---------------------------|
| Defines where variables are accessible | Defines how code executes |
| Static concept                         | Runtime concept           |

---

# Key Takeaways

- Scope defines variable accessibility  
- `var` is function scoped  
- `let` and `const` are block scoped  
- JavaScript follows lexical scoping  
- Scope chain is used for variable lookup  
- Shadowing can override variables  
- Loop behavior differs for `var` and `let`
