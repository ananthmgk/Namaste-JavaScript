# In this topic we cover about:
- `let`,
- `const`,
- `Block`,
- `Scope` &
- `Shadowing`.

### Block is defined by these `{...}` curly braces, this is perfect valid JS code called Block. Is also known as **Compound Statement**.
### A Block is used to combine multiple JS statement into one group.
### We can group multiple statement together in a **Block**, so that we can use it in a place, where JS expects only one statement.
```
Eg. {
     var a = 10;
     console.log(a);
    }
```
here we use muliple statement together in a Block.

`if(true) console.log(true);` ==> here the if statement needs one statement, so this is correct, But if we want mutiple statement, we need to grouping 
them using Block. 
```
Eg.
    if(true) {
      var a = 10;
      console.log(a); 
    }
```
#### About `Block Scope`:
 The Scope of this Block is, what all variables and functions we can access inside this Block is called **Block Scope**.
 ```
     {
        var a = 10;
        let b = 20;
        const c = 30;
    }
 ```
 ==> here we use three types of variables, and 
 ###see how these variables behaves inside this Block, How Hoisting works inside this Block. And when we see in the Sources of the above code.
 
 ![Capture1](https://user-images.githubusercontent.com/83916278/183265948-52dd9a8d-c87f-4f6b-b7e8-f690d4f25c4c.JPG)

Here when we put a Debugger at the begging of the code, we can see, what will happen when Hoisting, In the Scope the Rounded part is called **Block Scope**.
In this we see their is a seperate Block Scope reserved for `let b` and `const c`, and the `var a` is stored in the Global Scope. That's y `let` and `const`
are stated as Block Scope.

### Thoe `let` and `const` are inside the Block Scope, they can't be access outside the the Block. Where `var` can be accessed, Because `var` is stored 
inside the Global Scope.

```
Eg.
    {
     var a = 10;
     let b = 20;
     const c =30; 
     console.log(a);
     console.log(b);
     console.log(c);
    }
     console.log(a);
     console.log(b);
     console.log(c);
```
==> here we get `10` `20` `30` `10` and `ReferenceError: b is not defined`. Because `let` and `const` are not in the Global Scope. 
At this time the Block Scope will be deleted, and the Global Scope with the value of `a:10` will be their.

### About `Shadowing` in JS:

```
    var a = 100;
{
    var a = 10;
    let b = 20;
    const c =30; 
    console.log(a);
    console.log(b);
    console.log(c);
}
    console.log(a);
```
==> here we get `10` `20` `30` `10`, because `var a = 100` and `var a = 10` both are pointing to the same location (Global Scope). 
So when JS runs the code line by line. the last assinged `var` variable's value is printed in the console.

```
    let b = 100;
{
    var a = 10;
    let b = 20;
    const c =30; 
    console.log(a);
    console.log(b);
    console.log(c);
}
    console.log(b);
``` 
==> here we get `10` `20` `30` `100`, because here we have two `let` variables, here `let b = 20` is in the **Block Scope**, so 
the `console.log(b)` inside the **Block Scope** takes the value as `20`, and it prints the value. 

And the another `let b = 100` is out of the **Block Scope**, that means inside the **Script Scope**, so the `console.log(b)` 
inside the **Script Scope** takes the value as `100`, and it prints the value.

![Capture2](https://user-images.githubusercontent.com/83916278/183337891-5353f72d-2007-47b4-9ec3-f467c3c741bd.JPG)

If you see in the above image. when we put a debugger in the 6th line. and see, we have three Scopes inside the **Scopes**. 
**Block Scope**, **Script Scope** and **Global Scope**, and their correspondent variables in it. That's y it prints different
values. That is knows as **Shadowing**.

This same thing happens in `const` also.

```
    const c = 100;
{
    var a = 10;
    let b = 20;
    const c =30; 
    console.log(a);
    console.log(b);
    console.log(c);
}
    console.log(c);
```
==> here also we get `10` `20` `30` `100`, by the above `let` explanation.

```
    const c = 100;
function x() {
    const c =30;
    console.log(c);
}
x();
console.log(c);
```
==> here we get `30` `100`, because it Shadows in the function Scope also.

### About Illegal Shadowing.

```
let a = 20;
{
    var a = 20;
}
```
==> here we get `SyntaxError: Identifier 'a' has already been declared`.
If I try to Shadow `let` using `var`, it throws a SyntaxError. Is like Illegal Shadowing.

But we can Shadow `var` using `var`,
And we can Shadow `let` using `let`,
And we can Shadow `const` using `const`

```
let a = 20;
function x() {
    var a = 20;
};
```
==> here it won't shows any Error, because `var` is inside it boudaries. This is not a Illagal Shadowing.








