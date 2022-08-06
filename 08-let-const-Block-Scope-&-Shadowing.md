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

`if(true) console.log(true);` ==> here the if statement needs one statement, so it this is correct, But if we want mutiple statement, we need to grouping 
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
 ==> here we use three types of variables, and ###see how these variables behaves inside this Block, How Hoisting works inside this Block.
 And when we see in the Sources of the above code.
 
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
 console.log(b);
 console.log(c);

So in block " var a = 10;" influences the value within the block hence  
console.log(a); >> 10 and outside of the block 'Variable in Global environment' influences 
value of a hence console.log(a); >> 100

Illegal shadowing:

let a = 200;
{
 var a =20;
}

as 'var' declaration goes to 'Global environment' and sets in Memory context, it cannot be 
set using 'Block environment' value Hence:    
Uncaught SyntaxError: Identifier 'a' has already been declared
