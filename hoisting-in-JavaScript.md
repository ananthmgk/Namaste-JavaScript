# Hoisting
```
*)  var x = 7;
    function getName() {
        console.log("Ananth");
    };
    getName();
    console.log(x);
```
    ==> here we will get Ananth and 7..

*)  getName();
    console.log(x);
    var x = 7;
    function getName() {
        console.log("Ananth");
    };

==> here we will get Ananth and undefined. x is not defined


*)  getName();
    console.log(x);
    function getName() {
        console.log("Ananth");
    };
    
==> here we will get Ananth and x is not defined. 

so Hoisting in JS, we can access these variables before we initialization.

*)  getName();
    console.log(x);
    let x = 7;
    function getName() {
        console.log("Ananth");
    };

==> here we will get Ananth and Cannot access 'x' before initialization.

*)  getName();
    console.log(x);
    function getName() {
    let x = 7;
        console.log("Ananth");
    };

==> But here we will get Ananth and x is not defined. 

So here Phase 1 is writing x value as undefined , by running the getName Func.

*)  function getName() {
        console.log("Ananth");
    };
    console.log(getName);

==> here it prints the whole func.. getName() {console.log("Ananth");}

*)  getName();
    console.log(x);
    console.log(getName);
    var x = 7;
    function getName() {
        console.log("Ananth");
    };

==> here Ananth, x is not defined and getName() {console.log("Ananth");}

Here first Phase 1 writes all the variables and functions as undefined and whole func. and in the second Phase code execution, it see's the func invoke in 
the first line. so it throw the undefined value, from GEC. If their is no x value (x=7), it throw as x is not defined. 

*)  
    let x = 7;
    let getName = () => {
        console.log("Ananth");
    };
    getName();
    console.log(x);
    console.log(getName);

When we write this in arrow function, it will say getName is not a function. so in GEC getName value is assign as undefined. Because JS will see as a variable

*)  
    let x = 7;
    let getName = function() => {
        console.log("Ananth");
    };
    getName();
    console.log(x);
    console.log(getName);

In this case also getName will assign as undefined.


