## 1- What is Closure in Java Script?
A function along with a reference to its outer environment together forms a Closure. or.
Closure is a combination of a function and it's Lexical Scope Bundle together forms a Closure.

Each an every function in JS has access to it's outer environment, that means access to the variable and function present in the environment of the parent. Even when this function executed in the other scope, It still remember it's outer environment where it's originally present in the code. that is what Closure is.

### Example:
```
    let g = 20;
    function f() {
        let z = 100;
        function a(d) {
        let x = 10;
            function b(c) {
            console.log(x,z,d,c,g);
            }
        return b;
        };
        return a;
    }

    f(5)(3)(10);

    f(4)(2)(9);

    let e = f(6)(8);
    e(7);
```
==> here we `10` `100` `5` `3` `10` `20` | `10` `100` `2` `9` `20` & `10` `100` `8` `7` `20`.

```
here 
    a(5)(3);
is same as
    let e = a(5);
    e(3);
```

## 2- What will happen if we put a new variable at the outer most of the `f func`, can we access it?
### Ans: Yes we can access it..

### Example:
```
    let g = 20;
    function f() {
        let z = 100;
        function a(d) {
        let x = 10;
            function b(c) {
            console.log(x,z,d,c,g);
            }
        return b;
        };
        return a;
    }

    f(5)(3)(10);
```
==> here we get `10` `100` `3` `10` `20`.

## 3- What will happen if the above code have a conflicting name(collision of same name) of `let x` with a different value on outer the `f func`?
### Ans: It will give the same answer.
```
    let g = 20;
    let x = 11;
    function f() {
        let z = 100;
        function a(d) {
        let x = 10;
            function b(c) {
            console.log(x,z,d,c,g);
            }
        return b;
        };
        return a;
    }

    f(5)(3)(10);

```
==> here we get `10` `100` `3` `10` `20`. Beacuse the `b func` forms a closure with `x`, That means the `b func` has access to `x = 10` variable and not `x = 11`, so it prints `10`.

## 4- What will happen when we put the same conflicting name `x = 11` variable near the `x = 10`?
```
    let g = 20;
    function f() {
        let z = 100;
        function a(d) {
        let x = 10;
        let x = 11;
            function b(c) {
            console.log(x,z,d,c,g);
            }
        return b;
        };
        return a;
    }

    f(5)(3)(10);
```
==> here we get `SyntaxError: Identifier 'x' has already been declared`.

## 5- What will happen when we put the same conflicting name `x = 11` and the `x = 10` with `var` variable?

```
    let g = 20;
    function f() {
        let z = 100;
        function a(d) {
        var x = 10;
        var x = 11;
            function b(c) {
            console.log(x,z,d,c,g);
            }
        return b;
        };
        return a;
    }

    f(5)(3)(10);
```
==> here we get `11 100 3 10 20`. the last reffered value is printed.

## 5- Advantages of Closures.

### Ans: Closure helps us in Data hidding encapsulation.
### Explanation: If we have a variable, and it want to prevent it from other function accessible. it encapsulate the data, so that other func cannot access it.

### Example:
```
    let count = 0;

    function incrementCounter() {
        count++;
    }
```
==> here anybody can access this `count` variable. So to prevent that, we use Closures.
So we must wrap the whole code inside a Closure.
```
    function counter() {
        let count = 0;

        function incrementCounter() {
            count++;
        }
    }
    console.log(count);
```
==> here we get `ReferenceError: count is not defined`, because, now the `count` variable is hidden, nobody can access this variable. So here `incrementCounter` func can only access this `count` variable.

So when we return this `incrementCounter` func, it forms a Closure.
```
    function counter() {
        let count = 0;

        function incrementCounter() {
            count++;
            console.log(count);
        }
        return incrementCounter;
    }

    let counter1 = counter();
    counter1();
    counter1();
```
==> here we get `1` `2` and when we reenter the `counter1()` again it prints `3`.

### If we insert an another `let counter2`.
```
    function counter() {
        let count = 0;

        function incrementCounter() {
            count++;
            console.log(count);
        }
        return incrementCounter;
    }

    let counter1 = counter();
    counter1();
    counter1();

    let counter2 = counter();
    counter2();
    counter2();
```
==> here we get `1` `2` `1` `2`, because , in this case it will be a fresh counter itself.

## 6- Is this above code is Good in Scalable, Because if we want to decrement the count, how it will be?

### Yes we can use Constructor function to increment and decrement.
We can create a Closure with this Constructor function also.

```
    function Counter() {
        let count = 0;
        this.incrementCounter = function() {
            count++;
            console.log(count);
        }
        this.decrementCounter = function() {
            count--;
            console.log(count);
        }
    }

    let counter1 = new Counter();
    counter1.incrementCounter();
    counter1.incrementCounter();
    counter1.decrementCounter();
```
==> here we get `1` `2` `1`.

This is like a Constructor function. It constructs a new counter, whenever this counter function is called and gives us.

## Disadvantages of Closures.
### Ans: It Creates lot of memory in the program, forms a **Garbage Collector**.

## What is Garbage Collector?
Whenever their is some unused variables, Garbage Collector takes it out of the memory.

## How are Closures and Garbage Collector related to each other?
### Ans: They are related to each other.

### This is the [Video Link](https://www.youtube.com/watch?v=t1nFAMws5FI&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=14) for the above Explanation.

