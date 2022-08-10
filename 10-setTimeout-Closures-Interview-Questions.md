# Interview Questions about `Closures` and `setTimeout`.

### Question no.1:
Use setTimeout function to print a number after 3 seconds  and its explanation.

```
    function x() {
        var i = 1;
        setTimeout(function() {
            console.log(i);
        }, 3000);
        console.log("Namaste JavaScript");
    }
    x();
```
==> here we get `Namaste JavaScript` at 1st, and After 3 seconds `1` will print. here I will explain how JS works, JS reads the line one by one, when 
reaching the `console.log(i)` it takes the answer and it stored in place in a different **Local Scope**. 

This function forms a **Closure**, and takes value of `i` in a different place.

And when it reaches the line `console.log("Namaste JavaScript")` it prints the string in the console, And after the 3 second, and it takes the `i` value 
and puts it in the Callstack and it prints `1` in the console.

![Capture](https://user-images.githubusercontent.com/83916278/183965687-34b6094a-4668-4aa4-8de2-be38f65fdd1c.JPG)

### Question no.2:
Use setTimeout function to print 1 to 5 after each an every second. which means 1 after 1 second, 2 after 1 seconds, 3 after 1 seconds etc..

```
function x() {
    for(var i = 1; i <=5; i++) {
        setTimeout(function() {
            console.log(i);
        }, i * 1000);
    }
    console.log("Namaste JavaScript");
}
x();
```
==> here it prints `Namaste JavaScript` after 1 second `6` after 1 second `6` after 1 second `6` after 1 second `6` after 1 second `6` after 1 second `6`.
Because of the **Closure**, when a Closure is formed, it's like function along with it's **Lexical Environment**, even when a function taken out from it's 
original scope, still it remember it's Lexical Environment that means it will remember it's variables also. 

So when setTimeout stores it's function in a seperate memory, so the Closure remember its variable reference to `i` not the value of `i`. When this loop 
runs all the 5, pointing to the same reference `i`. Because we know that `var` store in a single **Global Scope**,

So here loop runs very fast than a second, so the `i` var loops to hit `6` and it stops their. after a second the `i` refers to `6`. so it prints `6`,
for every five times in a second.

So to correct this Bug we have to use `let` because let store in different place called **Temporal Dead Zone**, it **creates a new Block Scope for each an 
every iteration**.

```
function x() {
    for(let i = 1; i <=5; i++) {
        setTimeout(function() {
            console.log(i);
        }, i * 1000);
    }
    console.log("Namaste JavaScript");
}
x()
```

![Capture1](https://user-images.githubusercontent.com/83916278/183965930-2e0b695d-8edb-4dfd-9e1b-7ef793243a22.JPG)

==> here it prints  `Namaste JavaScript` after 1 second `1` after 1 second `2` after 1 second `3` after 1 second `4` after 1 second `5` after 1 second `6`.
In each time this setTimeout runs, it has it's own copy of new variable of `i`.

### Question no.2:
How to write this above code correctly using `var` and without using `let`.
For this Closures will help.

So according to the `var` of this program, tis `i` refers to the same location, so we have to set a new copy of `i` every time, 
So that we Form a Closure by enclosing this setTimeout function inside a new `function close()`.

```
function x() {
    for(var i = 1; i <=5; i++) {
        function close(x) {
            setTimeout(function() {
                console.log(x);
            }, x * 1000);
        }
        close(i);
    }
    console.log("Namaste JavaScript");
}
x();
```
and we have to supply the `i` which is in the `console.log(x)` to the new copy of `i`, So we have to call the `close()` with an `i`. like ` close(i)`,
and pass this `i` as `x` like `close(x)`,and print the `x`. it works correctly.
