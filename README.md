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

Link to youtube video https://youtu.be/jqxF1KQV9f8

# Destructuring (Object)
We continue to work with destructuring in one of the most used programming languages (javascript). In the previous part of the article, we discussed how to use destructuring in an array. And today our major focus will be on learning how to harness the power of destructuring for objects.    
Imagine we have the data of a men including his name, age and some characteristics like height, weight and hair colour.   
That look like this:

const men = {   
  name: 'Mark',   
  age: 20,   
  info: {   
	height: 180,   
	weight: 75,   
	hairColor: 'black'   
  }    
}    

And we can display our men:

console.log('Name is '+men.name);     
console.log('Age is '+men.age);    
console.log('Height is '+men.info.height);    
console.log('Weight is '+men.info.weight);    
console.log('Hair color is '+men.info.hairColor);    

Results:    
Name is Mark   
Age is 20   
Height is 180   
Weight is 75   
Hair color is black    

It is an ordinary way, but there are some disadvantages to it.  
And the major one is a long code. You can easily make a typo that will result in an error.   
And Destructuring can help us simplify it.   
Destructuring helps us breaking down a complex structure (like arrays and object) into simpler parts.   

For example, we can get the name from our object like this:
let {name} = men; 

The program takes property name from the object men and put it to the variable that has the same name as the property. In our case it is a variable name;

Another example.
let {name, age} = men;
Here we used object destructuring syntax to assign values to variables name and age. This is one of the most basic forms of object destructuring.


Also, we can declare our variables before destructuring syntax. In that case, we can get value from the object like this:

let name;
let age;

({name, age} = men)
We have to use parenthesis in that case. If we omit them, we get an error. It happens because for js code like this:
{name, age} is a block statement, which will lead to an error because a block cannot appear at the left-hand side of an assignment expression.

If we want to use another name to our variables (that doesn't exist in our object), we can use this syntax: key: new_name

let {name: myName} =  men
console.log(myName) // Mark

Let's to add a new variable in our code.
let {name, age, someVariable} = men

console.log(someVariable) // undefined

As we see our someVariable is equal to undefined. 
It happens because someVariable it is a non-existent property in our object.

We can pass the default value that will be assigned to non-existent variables instead of undefined. Like in the example below:
let {name, age, someVariable = 1} = men

console.log(someVariable) //1

Our next step will be nested object destructuring.
How can we quickly get nested info from the object? 

To get neccessary info we have to use next syntax:

let {info: {height, weight, hairColor}} =  men
console.log(height, weight, hairColor) // 180, 75, black

Now, let's talk about the rest parameter in our destructuring syntax.
What do you think we will get as a result of this code?

let {name, ...rest} = men



