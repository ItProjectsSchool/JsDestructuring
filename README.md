# Destructuring (Array)
In this article I will show you how destructuring assignment works in JavaScript’s arrays. 
We have an array of numbers.

let numbers = [1,2,3,4,5];

I can get first two items in the array like this:  

let a = numbers[0] //a = 1
let b = numbers[1] //b = 2

With destructuring I can do it shorter. 
let [a,b] = numbers //a = 1, b = 2

And we get same results.
How it works. When we use this syntax, we ask our program to take first element from the array and put it in the variable a. Then we ask to take second element and put it to the variable b. 
If we want to get third items all we have to do it add new variable in the construction. Like this:

let [a,b,c] = numbers
Now c is equal to 3.

If we want to skip second item in the array, we can use empty space between 2 commas. 
let [a,,b]=numbers // a = 1, b = 3

This construction helps us put all items after second in a new array:
let [a, b, ...rest]=numbers

Destructuring assignment also works with difficult arrays: 
let numbers2 = [1, [2,[3]]]
We can use next construction to get items from the array. 
let [a,[b,[c]]] = numbers2

In these 2 cases we get undefined. 
let [a]=[]
let [,,,,,,,,b]=numbers

It happens because you try to access items in the array that are out of the bounds or don’t exist.
In this case if you want to get reasonable value we can set default value for a. 
let [a = 1]=[]
let [,,,,,,,,b = 2]=numbers
Now a = 1 and b = 2

Also you can cope one array to another using destructuring assignment. It looks like
let array1=[...numbers]
or
let [...array2]=numbers

Also we can join 2 arrays together: 
let array = [...array1, ...array2]

Sometimes destructuring assignments are used in function result.
function firstAndLastItem(someArray){
  return [someArray[0], someArray[someArray.length-1]]
}
let [first, last] =firstAndLastItem(numbers)
Now first is equal to 1 and last is equal to 5




