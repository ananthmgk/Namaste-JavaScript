# How functions work in JavaScript & with Variable Environment.
```
var x = 1;
a();
b();
console.log(x);

function a() {
    var x = 10;
    console.log(x);
};

function b() {
    var x = 100;
    console.log(x);
};
```
==> Here the output will be `10,100` & `1`.
![GEC created](https://user-images.githubusercontent.com/83916278/182544242-7615b7b5-3a6d-4979-9a07-2999b5a05fdb.JPG)

 When a JS runs a program, a GEC is created with two components Memory context and Code Component, see the above image for ref. first it will collect all the 
 variables and fuctions in it. after then this GEC is pushed inside the Callstack.
 
 ![Code compnt](https://user-images.githubusercontent.com/83916278/182554035-a629cba5-2cef-476f-b028-bcde251aafd4.JPG)

 
 After this the Code is one again runs from the top to bottom. By running, it will replace `x = 1` in the GEC, and when runs in the second line, it see's a 
 function invokation `a()`, So it will create a new EC in the code compont with the same two columns, inside this memory compnt a seperate var `x = 10` is 
 created, suddenly this EC is pushed inside the callstack above the GEC. And when it see's the `console.log(x)` is take the value of x in this local EC and 
 it prints it on the console.
  After this whole EC will be deleted.
  Then the GEC runs to the next line from where it left, it moves to line 3, their also it see's a func invokatoin, `b()` after seeing this a new EC is 
  created inside the GEC code component, as like the previous method.
  After this line no 4 `console.log(x)` is executed, and it take the value from the GEC `x = 1` and it will prints it to the console. 
  After that the whole GEC will be deleted.
  
  ![GEC is created](https://user-images.githubusercontent.com/83916278/182556691-ff862330-84fb-42cf-8ae8-56c51f439c8a.JPG)
  
  When the code moves to the line no.1, a GEC is created, we can see it in the above image. their we can see `anonymous is (GEC)` in the Call Stack, and in 
  the Scope we can see `x: undefined` `a: f a()` and `b: f b()`. 
  
  After this when the code moves to the second line, `x = 1` will be placed in the scope.
  
  ![line no.7](https://user-images.githubusercontent.com/83916278/182559450-880b5ef3-2302-4e90-9699-327a8244237a.JPG)


After this when the code moves to the line no.7, a new EC is created inside the call and the `anonymous` GEC is pushed down you can it in the above image,
and in the scope u can see Local Scope and Global scope. inside local scope we see `x: undefined` and in the Global scope we see all `func` and `x: 1`. 
because the code is in the line no.7.

And when the code moves to line no.8, `x: 10`, And when in line no.3 the EC will be deleted in the call stack, and the control moves to the `anonymous` GEC 
and it prints the x value in the console.

when the code moves to the line no.12 again the above method is followed...
After the b() func finished, the control moves to the line no. 4. it prints the x value in the console. and atlast the whole GEC will be deleted.
