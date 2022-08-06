## This Topic is about 
- **Temporal Dead Zone**,
- Are **let** & **const** declarations Hoisted in JS?,
- Difference betweeen **SyntaxError**, **ReferenceError** and **TypeError**?

Notes: ###`let` and `const` declarations are Hiosted, But their declarations is diffrent than the `var` declarations, these are will be in the Temporal Dead 
###Zone for time being.
```
      console.log(b);
      console.log(a);
      let a = 10;
      var b = 100;
```
here we will get the Output as `undefined` and `Uncaught ReferenceError: Cannot access 'a' before initialization.`

here before initialization, we known that the first answer `undefined` came by `var` **that was because of Hoisting**, and `let` throws an error called 
`ReferenceError: Cannot access 'a' before initialization.` because let and const will store the `undefined` value in diffrent memory space called 
**Temporal Dead Zone**,  and not in `Global` or `Window` or `this`. So here JS cannot access those values. so it throws the error, `cannot access` through 
`ReferenceError`. 

So here the error says that cannot access `a` before it was initialied. 
So
```
console.log(b);
let a = 10;
console.log(a);
var b = 100;
```
here we get Output as `undefined` & `10`. **Because here console is asked after the initialization.**

![Capture1](https://user-images.githubusercontent.com/83916278/183249440-8ed204da-c6ed-4ffd-9c28-01277da2f226.JPG)

here we can see that `a` is stored in a separate memory space called **Temporal Dead Zone**, `Script` in the value as `undefined`. So we can't access this
value before inserting a value in it, is Hoisting in let.
and `b` value is stored in the `Global`.

![Capture2](https://user-images.githubusercontent.com/83916278/183249763-0b4db0b3-32a8-495d-8bc9-59cb7a73a63f.JPG)

In the above image we move the line to the second line, so a value `10` is assinged. and now we can access the value.

** Temporal Dead Zone is the time when this `let` variable was Hoisted and till it is initialied some value, That time between that is known as
Temporal Dead Zone.**

## About `ReferenceError`:

```
      console.log(x);
```
here we get `Uncaught ReferenceError: x is not defined`. beacause their is no x is defined, and their was no `Reference`. so it throws the error through 
`ReferenceError`.

```
      console.log(a);
      let a = 10;
```
here we get `Uncaught ReferenceError: Cannot access 'a' before initialization.`

## About SyntaxError:
### Note: if a SyntaxError came, JS doesn't read a single line.
`let` is little more strict than `var`
```
      let a = 10;
      let a = 100; 
```
here we get `SyntaxError: Identifier 'a' has already been declared`, so we can't redeclarate the let value. JS won't run a single line, if it sees a 
redeclaration of `let`. it throws a SyntaxError and close the program.

```
      let a = 10;
      var a = 100; 
```
here also we get the above same SyntaxError. `'a' has already been declared`.

```
      var a = 10;
      var a = 100; 
      console.log(a);
```
here get `100`. as the last `a` value. in this `var` we can redeclarat the value. it wont throw a error.

## About `const`:
`const` is even more strict than `let`, 

```
      let a;
      a = 10;
      console.log(a);
```
here we get `10`, because in `let` we can declare first and we can initialize it in any where in the code. But we can't do this in `const`.

```
      let a;
      a = 10;
      console.log(a);
      const b;
      b = 10;
      console.log(b);
```
here we get `SyntaxError: Missing initializer in const declaration`. it throws a SyntaxError. it won't read a single line.
### So while declaring const we have to initialize it in the same line.
```
      let a;
      a = 10;
      console.log(a);
      const b = 100;
      console.log(b);
```
here we get `10` & `100`.

## About `TypeError`:
```
      let a;
      a = 10;
      console.log(a);
      const b = 100;
      b = 1000;
      console.log(b);
```
here we get `TypeError: Assignment to constant variable.` TypeError says that, their is a `const` value is been redeclarated.

## This is the [Video Link](https://www.youtube.com/watch?v=BNC6slYCj50&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=9) for the above explanation.
