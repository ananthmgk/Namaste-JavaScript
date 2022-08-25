# This Topic is about:
- What is a Callback function in Javascript and its uses,
- Deep about Event-Listener,

## What is a Callback function?

Functions are first class citizens in Javascript, that we can pass a function in an another function, that passed function is called **Callback Function**.

We know that JavaScript is **Synchronous Single-threaded language**, it can do only one thing at a time in a specific order, but due to **Callback Function** we can do Asynch things inside Javascript.

<!-- It gives access to the whole Asynchronous world in a Synchronous Single-threaded language. -->

for Example 1:
```
function x(y) {

}

x(function y(){
    
})
```
here we are passing `y()` func to `x()` func, in this case `y` func is knows as **Callback fuction**.

Example 2:
### Using setTimeout().
**setTimeout** takes a callback function as a first arguments and it's stored in a seperate place, and setTimeout takes time in milli seconds as second arguments also stored in that seperate place.

after the **time** expires the callback function which is in the first arguments is executed.

```
setTimeout(function () {
    console.log("timer");
}, 5000);

function x(y) {
    console.log('x');
    y();
}
x(function y() {
    console.log('y');
});
```
here we get `x` `y` and 5 seconds `timer` will be printed. 
### So the setTimeout Asynchronous operation was not possible without these callback.
We gave this callback func to this Asynchronous setTimeout func, to call this callback func after some time in the code.


to be continued..................
