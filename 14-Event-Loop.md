## Topics in this section:
- Event Looop,
- Call Stack,
- Web API's(inside browser),
 - window,
 - setTimeout(),
 - DOM API's,
 - fetch(),
 - console
- Task Queue or Callback Queue,
- Microtask Queue,
- addEventListener().

![Capture](https://user-images.githubusercontent.com/83916278/191102257-7c6147f1-91d3-417a-bb25-5c82f584603a.JPG)

JavaScript is a **Syncronous Single Treaded Language**, because it has one **Call Stack** it can do only one thing at a time,
This **Call Stack** is present inside the **JavaScript Engine**, And all the code in JS is executed in the Call Stack.

## Theory Part:
```
function a() {
    console.log("a");
}
a();
console.log("End");
```
When a program runs in JS, First it creates a **Global Execution Context(GEC)** and it's pushed inside the **Call Stack**, inside GEC the whole code run line by line and it stores the **variables** and **func**, and to invoke the `a()` a **Execution Context** is created over the **GEC**, and the `a()` is executed and in the console it prints `a`, after finishing the `a()` func the `a`'s **EC** is poped out of the **Call Stack**.
 And when it comes to the last line of the code `console.log("End")` it prints `End` in the console.
After finishing the whole program, the **GEC** is also poped out of the **Call Stack**.

### So the main thing of the **Call Stack** is, what ever comes inside the Call Stack it will quickly executes and popes out of there.
It does not wait for nothing.

But what if we want a program to do it after 5 seconds. Here Call Stack wont do this work. 

Instead **Browser** does this work, it has a Timer.

Beacuse **JavaScript Engine** is build inside the Powerfull **Browser**.
### Browser--> JS Engine--> Call Stack--> GEC(here code run).

![Capture1](https://user-images.githubusercontent.com/83916278/191102337-63884742-0a36-4c12-8943-edc8868fe518.JPG)

## About Browser:
- Browser has a **Local Storage**, here it stores some data in it,
- It has a **Timer**,
- It has **URL**, to communicate to the external world and fetch datas from other server, and it shows in the **UI**.
- 
![Capture2](https://user-images.githubusercontent.com/83916278/191102375-eb8c3726-7cfe-43ea-a5e0-bab9132ca44e.JPG)

So here **JS Engine** can access the above those Browser's facilities..

![Capture3](https://user-images.githubusercontent.com/83916278/191102473-3b5216db-0b65-448f-9d4c-58d17fc5c4a9.JPG)

### Note: The list in the above image, are not in the Part of **JavaScript** 
**setTimeout()**, **DOM API(document.getElmt.....)**, **addEventListener()**, etc, which are not belongs to the **JS**, But **JS** can access those facilities through **window**.

The **window** mentioned in the image is the **Global Object**,
we can also use window.setTimeout() etc.... _all are same_ . Because **window** is in the Global Object, it atomaticaly sets the key to **window**.

## Example 1:
```
console.log("Start");

setTimeout(function cb() {
    console.log("Callback");
}, 5000);

console.log("End");
```
here we get `Start` `End` after 5 seconds `Callback` will be printed. We can see what is Happening inside.

![Capture4](https://user-images.githubusercontent.com/83916278/191102555-07e66615-8124-4b57-a424-2714c8749725.JPG)

As shown in the above image, when it goes to the first line, that console calls the **Web API** console through the **window** Object.

![Capture5](https://user-images.githubusercontent.com/83916278/191102625-733b8bde-29ea-4688-8851-f1a36a598e1e.JPG)

When it goes to the second line, the **setTimeout()** func stores the **Callback** func inside the Web API as marked in the above image along with the timer running. 

Suddenly JS moves to the next line and it prints `End` in the console.
After finishing the code, **GEC** is pops out of the Call Stack.

After the 5 seconds completes, the `cb()` callback func is **Queued** inside the **Callback Queue** is also called as **Task Queue**, see in the below picture.

![Capture6](https://user-images.githubusercontent.com/83916278/191102741-1cd080b3-468e-4ac5-8264-e79119641f9f.JPG)

Here comes the **Event Loop**, It acts like a Gate keeper, It checks wheather the Call Stack is empty if it's true, it checks wheather their is a call back func inside the callback Queue, if true, Event loop moves the `cb()` from the **Callback Queue** into the **Call Stack** and its executed and it prints `Callback`, So this is how setTimeout func works.

## Example 2:
```
console.log("Start");

document.getElementById("btn")
.addEventListener("click", function cb() {
    console.log("Callback");
});

console.log("End");
```
here we get  `Start` `End` and when the user clicks the button, `Callback` will be printed in the console.

Here `document.` and `addEventListener()` func also belongs to the **Web API**.

Whenever we run any Javascript code, `GEC` is created , after it goes to the first line of the code, **Start** will print in the console.

When it goes to the second line, it sees `document.getElementById().addEventListener()`, So here this line belongs to the **Browser** which connects through **Web API** in **DOM API** DOM is _html code_, and then `addEventListener` register `cb()` CallBack function with an event of _click_, this **CallBack** is registered in the **Web API** environment. see it in the below image.

![Capture7](https://user-images.githubusercontent.com/83916278/191102822-b55d0996-9a46-4d72-bf42-4cd19c4a28e5.JPG)

After the code moves on to the next line. And **End** is logged in the console.
After that **GEC** is removed from the Call Stack.

So the `cb()` callbck func waits inside the **Web API** environment untill the browser is closed, and when the given button is clicked, the `cb()` callbck func is moves to the **Callback Queue** and it waits over here, so after that event loop takes the `cb()` from the **Callback Queue** and it drops into the **Call Stack** if the **Call Stack** is **empty**, its then quickly executed, `Callback` will be printed in the console. and `cb()` is goes from the **Call Stack** and **Callback Queue** too. see it in the below image.

![Capture8](https://user-images.githubusercontent.com/83916278/191102949-11755985-46fc-46d1-aa87-0cca9bdaae2b.JPG)

### Note: Why do we need a **Callback Queue**?

Suppose when the user clicks the button more than a one times, that all `cb()` funcs are pushed inside the **Callback Queue** five ,six times and it waits line by line... see it in the below image.

![Capture9](https://user-images.githubusercontent.com/83916278/191103024-d9c659a2-c20e-42a8-a750-a701e7cc7f73.JPG)

## Next we are going to see about **fetch()**, it works in a diffrent ways.
- fetch goes and request an API call `"http://api.netflix.com"`, it returns a promise, when the promise becomes true,the **CallBack func** is executed.

## Example 3:
```
console.log("Start");

setTimeout(function cbT() {
    console.log("CB setTimeout");
}, 5000);

fetch("http://api.netflix.com")
.then(function cbF() {
    console.log("CB Netflix");
});

console.log("End");
```
here we get `Start` `End` after when fetch is true `CB Netflix` and after 5 seconds `CB setTimeout` will be printed.

here we know first `GEC` is created, then `Start` is printed, setTimeout- `cbT()` is registered inside the **Web API** environment and timer is started to run,
and in the next line it sees `fetch`.
`fetch` is also a **Web API** which is used to make a Network Calls.
the `fetch` register the `cbF()` *Callback func* inside the **Web API** environment.

As soon as when the data returns from the Netflix server, `cbF()` Callback func is pushed to a diffrent Queue called **Microtask Queue**, this **Microtask Queue** has **Higher Priority**. 
that means the callback func from the Microtask Queue is taken **first** and the callback func from the Callback Queue is taken **later**, 
### that means, it is taken if all the funcs from the Microtask Queue is finished taken.

All the **callback** func which comes through **Promises** and **Mutation observer** are send to the **Microtask Queue**.

## What will happen in this scenario....
If we have millons if lines in between `fetch` and `console.log("End")`, so at this time `GEC` is still inside the `Call Stack`, and at this time `cbF()` and `cbT()` will wait to execute. after finishing the code `End` prints in the console. 
`GEC` is popped out of the `Call Stack`, `Event loop` first takes the `cbF()` func from the **Microtask Queue** and it prints `CB Netflix` in the console,
and it takes `cbT()` func from the **Callback Queue** and it prints `CB setTimeout`.

### Suppose when the Microtask Queue creates a new **Microtask** by its own and that creates another one like wise if it goes on. at this time the function waiting in the **Callback Queue** never get a chance to execute, This is known as **STARVATION** of the Callback Queue.

![Capture10](https://user-images.githubusercontent.com/83916278/191103157-b143f70d-da1f-4bb0-b21f-affa358afe77.JPG)

### This is the [Video Link](https://www.youtube.com/watch?v=8zKuNo4ay8E&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=18) for the above Explanation.
