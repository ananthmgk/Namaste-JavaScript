#  The Scope Chain Scope Lexical Environment.
### Scope in JavaScript is directly related to Lexical Environment.

## Lexical Environment is the Local memory along with the Lexical Environment of it's Parent
the name **Lexical** means in a **Sequence** in **Order**.`c()` func is Lexicaly sitting inside the `a()`,
Lexical parent is Where the specific code is present physicaly, that is.. `c()`'s Lexical parent is `a()` and `a()`'s Lexical parent is `Global`,
Lexical Environment is the Local memory + Lexical Environment of it's Parent.


![photo_2](https://user-images.githubusercontent.com/83916278/182886190-55403915-8977-4e0d-a581-6809f39b5804.jpg)

### Note: Whenever a Execution Context is created Lexical Environment is also created in it. 
In the above image, we can see Call Stack at the left side and the Code at the right side, In the Call Stack, I have mentioned the Lexical Environment in a
small box inside the Execution Context, this is reference to the Lexical Environment of it's Parent. So in the above image, `c()` func's parent is `b()` func,
So the `b()`'s memory component will be copied to the `c()`'s Lexical Environment. So that we can access the `b()`'s memory. 
Likewise `b()` func's parent is `GEC`, and `GEC`'s parent will be `null`. So that the Output we get is `10`. 
### This is we called as a **Scope Chain**.

So in the above image of the code line no.4 JS will try to find the `b` in the local memory of `c()`, if it's not their, JS will go to Lexical Environment
of it's parent `a()` and it find for `b`, if it's not their, JS will go to Lexical Environment of it's parent `GEC`, their it get's the `var b=10` `b` value
and it prints `10` in the console. 

Suppose if we didn't declare the `b` variable in the whole code, JS will go to Lexical Environment of Global's parent, thier it will see `null`.
here the program stops.
So it will print `b is not defined`.
### This is we called as  **Scope Chain**.

![Capture](https://user-images.githubusercontent.com/83916278/182897303-00311c4d-e57a-480f-8ce7-6d8c9e3e924a.JPG)

In the above image, inside the Call Stack we can see all the three Execution Contexts, here we see `(anonymous)` as GEC, `a`'s Execution Context above `GEC`,
and `c`'s Execution Context above `a`.

![Capture2](https://user-images.githubusercontent.com/83916278/182901700-80b05102-fc2c-4e7b-8ea5-5815d8251437.JPG)

In the above image if we select `(anonymous)` in the Call Stack, we see `Global` in the Scope, this is the Local Memory of GEC, here we can see `a: f a()`,
but not `c`.

![Capture3](https://user-images.githubusercontent.com/83916278/182904962-160ad191-4279-4f99-a345-a96137708fd1.JPG)

If we want to see the Lexical Environment of `a()`, select `a` in the Call Stack, and if we see in the Scope, we see Local Memory of `a` + Lexical 
Environment of it's parent as `Global` as it's in the above image.

![Capture4](https://user-images.githubusercontent.com/83916278/182905349-e3cb21a3-4db2-47b0-965d-272c563651fa.JPG)

Likewise we can see `c`'s Lexical Environment in the above image.  as we see Local Memory of `c` + Lexical Environment of it's parent `a` + Lexical 
Environment of it's parent `Global`. 
So `c` has access to all these variables and functions, 
### here we see `Closure`, because `c` has enclosed inside `a` this is what closure.

```
    function a() {
        console.log(b);
    };

    var b = 10;
    a();
```
===> here we get the Output is `10`. because here `console.log(b)` can access the `var b = 10` outside the func as by Lexical Environment.

```
    function a() {
        c();
        function c() {
            console.log(b);
        }
    };

    var b = 10;
    a();
```
===> here also we get the Output is `10`.

```
    function a() {
        var b = 10;
        c();
        function c() {

        }
    };

    a();
    console.log(b);
```
===> But here we get the Output `b is not defined`, because JS will go to Lexical Environment of Global's parent, thier it will see `null`.
here the program stops.
So it prints `b is not defined`.

## This is the [Video Link](https://www.youtube.com/watch?v=uH-tVP8MUs8&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=8) for the above Explanation.
