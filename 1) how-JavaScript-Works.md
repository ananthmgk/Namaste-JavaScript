```
let n = 2;
function square(num){
  let ans = num * num;
  return ans;
}
let square2 = square(n);
let square4 = square(4);
```
*) ### Everyting in JavaScript happens inside an "**Execution Context**" ==> _it's like a container_.
*) ### And JS is a synchronous Single-threaded language. which means, it runs in a specific order in one command at a time.

*)when we run the above JS program, an Execution Context is created, with two columns, the first is **Memory component(Variable Environment)** and the second is **Code component(Thread of Execution)**. Here it will create two phases, **Memory creation phase and Code execution phase**,

## Phase1:Memory creation phase
*) at first, when the code runs in the first line no.1 in the above code, it will create a Memory creation phase inside the Memory component as 
`n: undefined`, 
here `undefined` is like a placeholder, and the second line no.2 `square: {..}`, here it stores the whole code of function, then line no.6 
`square2: undefined`, 
and line no. 7 `square4: undefined`.

## Phase2: Code execution phase,
Now JS runs the whole program once again line by line, when it comes in the line no. 1 the `n: 2` the 2 value is placed in it, and in line no. 6 a func is 
_invoked_, which means, when it sees a func name with a parameter, it's now executed. so here when a func is invoked, 

  suddenly a new Execution Context is created inside the Code component, as with the same two columns, as the 1st is **Memory component** and 
  the second is **Code component**, here also it creates two phases like the above Memory creation phase and Code execution phase, in the 
  memory creation phase when it runs in line no.2 `num: undefined` is placed, and line no.3 `ans: undefined` is placed. 

  **Phase 2**: code execution phase, so here the `n` value 2 is placed in `num: 2`, and in line no. 3 the value of `num` is placed and the 
  calculation is done, it place the value in `ans: 4`, and in line no.4 it returns the `ans` value(`4`) to where the func is invoked, so here 
  the code execution takes the value in the local memory location as `4`, and it place the value in `square2: 4` after that this current 
  **Execution Context** is deleted.

  it moves in line no. 7, here also a func is invoked, so again a new Execution Context is created inside the Code component, like the 
  above explained.
Here all those work is done with a method called **Call Stack**, **Call Stack maintains the order of execution of Execution Context**.
we assume this call stack as a cup, at the bottom the **GEC(Global Execution Context** is the whole Execution Context) is poured, and when the func is invoked the new Execution Context is poured above the GEC, as soon as the first Execution Context returns, the first Execution Context will be deleted. and the control go's to the **GEC**, where it left, and it comes to the line no.7 and new Execution Context is poured above the GEC like wise...

### Note:
Here Call Stack is also called in several names **Call Stack, Execution Context stack, program stack, control stack, Runtime stack, Machine stack**.

This is the [Video link](https://www.youtube.com/watch?v=iLWTnMzWtj4&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=3) for the above explanation.

### Execution context diagram:-
![IMG_20220731_194205~2](https://user-images.githubusercontent.com/83916278/182032676-f2f814f7-8e8d-46a8-b630-3f22dd89972f.jpg)

### Call Stack diagram:-
![IMG_20220731_194234~2](https://user-images.githubusercontent.com/83916278/182032575-4c5dfb4e-ff9a-4af1-b60b-0dcc64bdba31.jpg)

