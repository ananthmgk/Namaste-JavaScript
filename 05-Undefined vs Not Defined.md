# Undefined vs Not Defined in JavaScript.
![Capture1](https://user-images.githubusercontent.com/83916278/182814408-494af0e4-44f6-4223-a779-1fa602cb6b64.JPG)


JS creates a GEC, even before a single line of code is being executed. in this, JS collects all the variables, and it place the value as undefined in the GEC,
In the picture when we see in the console, `undefined` is printed in the first line. Because when we see in the VScode page line no.1 console is placed before 
the `a` variable, so it take the `a` value from GEC and prints as `undefined`. and in the 3rd line console is placed after the `a` variable. so in this line it 
get the a value as `10` and it prints in the console. 

As we can see in the 2nd line of the console page `10`. and at the 3rd line of the same page we can see `x is not defined` because if we see in the vs code 
`x` is not defined as a variable, so `x` will not have a place in the GEC as. so console.log(x) prints x is not defined.

![Capture2](https://user-images.githubusercontent.com/83916278/182819854-31dfdcdc-5cb8-450c-beb0-216a344c9281.JPG)

In tha above image shows JS is very flexible, because `a` variable can store numbers, booleans, strings etc. So it is called as loosly type language.

## This is [Video link](https://www.youtube.com/watch?v=B7iF6G3EyIk&list=PLlasXeu85E9cQ32gLCvAvr9vNaUccPVNP&index=7) the for the above explanation.
