# SHORTEST JS Program `window` `this` keyword.
An Empty File is the shortest JavaScript Program. 

![Shortest JS progm](https://user-images.githubusercontent.com/83916278/182637755-dd6ce41a-c0b7-4793-97a3-328949b77450.JPG)

As it was an Empty file, JS engine do lot of thing, doing behind the scene. 

![GEC in empty file](https://user-images.githubusercontent.com/83916278/182642624-2f13eb86-04aa-4e60-84ae-cb17dce06d1b.JPG)

It creates a GEC, we can see in the above image, in the Scope we can see a Huge Object.
Inside GEC a Global object called `window` or `this` is created.
Here `window` === `this` is `true`.

![window = this](https://user-images.githubusercontent.com/83916278/182643618-606c804d-c86f-41c2-a769-5cf405e6f8b8.JPG)

In the console if we type `window` or `this`, a Huge object is shown as it was created by JS Engine. Inside we can see lot of functions, methods and variables, 
which is inside the **Global space**, we can access these func and variables at any where in our JS program.

### Here at the Global level `this` points to the `window`, `window` is a Global object which is created along with the GEC.

Here **Global space** is, if any code which is outside a function is stored in the Global space. 

![Global space](https://user-images.githubusercontent.com/83916278/182651452-fa622d62-d46b-4b37-a19f-e60b89ca1c7a.JPG)

In the above image inside the scope ,we can see the `a` variable and `b` variable, but `c` variable is not stored. 
This means these all variables are inside `window` and `this` object. we access this varibles by
`console.log(window.a)` ==> output will be `10`
`console.log(this.a)` ==> output will be `10`
`console.log(a)` ==> output will be `10`, these all are same.
But if we access c like `console.log(c)` ==> output will be `c is not defined`.

This is the [Video link](https://www.youtube.com/watch?v=QCRpVw2KXf8) for the above explanation.
