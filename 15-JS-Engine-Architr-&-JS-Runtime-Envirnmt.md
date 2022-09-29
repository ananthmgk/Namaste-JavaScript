### JavaScript can run in everywhere, If a `JavaScript Runtime Environment` is present in a device, it can run a JavaScript code.

## JavaScript Runtime Environment has:
- JavaScript Engine,
- Set of API s,
- Event Loop,
- CallBack Queue,
- MicroTask Queue.

![Capture2](https://user-images.githubusercontent.com/83916278/192956823-7ef4f1a1-b9ae-4e32-be04-349a024c7390.JPG)

JavaScript Engine is the Heart of the **JavaScript Runtime Environment**.

### Every Browser has an **JavaScript Runtime Environment**,
### Node.js has also **JavaScript Runtime Environment**, it can run JavaScript outside the Browser, ex- in a watercooler, Smart Watch, Robot etc...

Note: The API present inside a Browser is known as **Local Storage**.

Using **ECMAScript** language Standards, 
- **Chakra** JavaSript Engine is used in **Microsoft Edge**,
- **SpiderMonkey** JavaSript Engine is used in **Mozilla Firefox**, And this is the first JavaScript Engine created by `Brinton Ike`,
- **V8** JavaSript Engine is used in **Google Chrome**, **Node.js**, **Deno** and **V8.net**, which is the fastest engine in the world.

## Inside JavaScript Engine:
When JavaScript code is send inside the JS engine, it take 3 major steps are
- `Code` -> `Parsing` -> `Compilation` -> `Execution`.

### Parsing:
During Parsing time the code which we had written are broken into `Tokens`, for exmple, see the below image

![Capture3](https://user-images.githubusercontent.com/83916278/192956923-1c9ebaee-a3e7-46a0-b6c9-91058f61c927.JPG)

and next step is known as `Syntax Parser`, it takes the code and convert it into `AST` **Abstract Syntax Tree**. it looks like the below image.

![Capture4](https://user-images.githubusercontent.com/83916278/192956963-00bb974b-4bc9-4ce0-af7a-943abf09b5c5.JPG)

This is the **Abstract Tree** for `const bestJScourse = 'NamasteJavaScript';` in the above image.

#### Compilation:
And the `AST` which is generated is send to the `Compilation` inside this,

`JIT` **Just In Time** Compilation takes place. it means, it desides to take both the **Interpretter** and **Compiler** Language, 

We can see what is `Interpretter`..
Interpretter method is, executing the code line by line, it dont know what will happen in the next line. is more fast than Compiler.

Now We can see what is `Compiler`..
Here the whole code is **Compiled** (capture) first and a new code is formed which is the optimed version of the first code and then it is executed. It is more Efficience than Interpretter. 

### Is JavaScript is a Interpretter language or Compiler Language?
 - Now the New version of JavaScript works in both the Interpretter and Compiler Language. it depends upon the JS Engine.

here `JIT` plays the major role to prefer both the Interpretter and Compiler Language. it coverts the code into `Bytecode`.

### The next step is Execution..

It has two main steps,
- **Memory Heap**,
- **CallStack**.

![Capture5](https://user-images.githubusercontent.com/83916278/192956996-64b57084-3272-4445-b279-b1203aef5ad1.JPG)

### Memory Heap:
 Is the space, where all the variables and funcs are assinged inside it. it has **Garbage Collector** which it moves all the unused variables and funcs to the Garbage Collector,  this Garbage Collector uses `Mark and sweep` algorithems.

### CallStack:
 We already know about this CallStack.
 
 ![Capture](https://user-images.githubusercontent.com/83916278/192957364-3ba364d0-2fde-4ed4-ae71-a05568762b01.JPG)

 The above image shows the flow chart of JS Engine for `V8`, Google's.
 
 ![Capture1](https://user-images.githubusercontent.com/83916278/192957509-faa7f804-5e3c-4eed-bf89-b1b16f7dd2d1.JPG)


### This is the [Video Link](https://www.youtube.com/watch?v=2WJL19wDH68&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=19) for the above Explanation.
