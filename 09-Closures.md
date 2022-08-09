This topic is about:

# Closures In JavaScript.

```
    function x() {
        var a = 7;
        function y() {
            console.log(a);
        }
        y();
    }
    x();
```
==> here we get `7`,because it is based on Lexical Environment. **This is what Closure is**.

### Note: Functions along with it's Lexical Environment bundle together, forms a closure, that is knows as **Closure**.

![Capture](https://user-images.githubusercontent.com/83916278/183598258-3a2eb2d5-fb06-4d74-a051-7117c4567129.JPG)


In the above image, we put a a Debugger in the `console.log(a)` line, and see in the Scope, thier are three scopes, `Local`,`Closure` & `Global`, it says 
that, inside `y()` it forms a Closure with the variable `x()` **Lexical Scope**, which means the **`y` forms a Closure and it has access to it's 
Parent Lexical Scope `x`**.

## Closure in MDN Docs:

![Capture1](https://user-images.githubusercontent.com/83916278/183598324-1fc97d81-0b25-43c1-bcb2-8a168936a86c.JPG)

### Some function methods, Examples:
```
    function x() {
        var a = function y() {
            console.log('a');
        };

        a();
    }
    x();
```
we can assign a function to a variable, like above.

```
    function x() {
        var a = 7;

        y();
    }
    x(function y() {
        console.log(a);
    });
```
we can pass a function to a another function as a parameter.

And also we can return this function as below, when we invoke the `x()` the function, it returns the func to the place where the func was invoked. so we put
`var b` to see the result.

```
    function x() {
        var a = 7;
        function y() {
            console.log(a);
        }
        return y;
    }
    var z = x();
    console.log(z);
```
==> here we get  the whole function as `ƒ y() {console.log(a);}`. here what happed to the above code, when we invoke a function `x()`, a new 
**Execution Context** will be created, and after returning `y`. the `x`'s Execution Context will be deleted.

### so now `z` have the `y` func and it's Lexical Environment. And if we invoke the `z()` func some where else in the program, it prints `7`, Because,Here
### **Closure** will take place to help us, by remembering the `y`'s **Lexical Scope**, they remember, where they were actualy present in the code
### so it have the `var a = 7` in it. So it prints `7`. 

see in the below code...

```
    function x() {
        var a = 7;
        function y() {
            console.log(a);
        }
        return y;
    }
    var z = x();
    console.log(z);
    // 
    // 
    // 
    // 
    z();
```
==> here we get `ƒ y() {console.log(a);}` & `7`, So here, it returns the Closure and `y`'s parent Lexical Scope and it was put in the `var z`. so we can 
access the `a` value.

If we put another variable below the `var a = 7`..

```
    function x() {
        var a = 7;
        function y() {
            console.log(a);
        }
        a = 100;
        return y;
    }
    var z = x();
    console.log(z);
    // 
    // 
    // 
    // 
    z();
```
==> here we get `ƒ y() {console.log(a);}` & `100`. Here `a`'s ***reference*** is changed to `100`.

### When we put the whole func into the another func, in a Scope Chain.

```
    function z() {
        var b = 900;
        function x() {
            var a = 7;
            function y() {
                console.log(a,b);
            }
            y();
        }
        x();
    }
    z();
```
==> here we get `7` `100`. Here the **Closure** took place.

In the above code if we put a debugger in the `console.log(a,b);` line. in the Scope, we see `Closure(x)` and `Closure(z)` and their variables in it.

![Capture3](https://user-images.githubusercontent.com/83916278/183598393-77947f09-7bb9-4c4e-8d1e-ec8a45995c84.JPG)


### That means `y` forms a Closure with the Scope of `x` and Scope of `z` along with it's variable.

### Uses of Closures:
- **Module Design Pattern**,
- **Currying**,
- **Function like once**,
- **memoize**,
- maintaining **state in async** world,
- **setTimeouts**,
- **Iterators**,
- and many more......

### This is the [Video Link](https://www.youtube.com/watch?v=qikxEIxsXco&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=12) for the above Explanation.
