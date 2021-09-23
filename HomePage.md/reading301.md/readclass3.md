**React Docs-lists and keys**

## What does the .map() return ?

.map() returns an array.

## If I want to loop through an array and display each value in JSX. How do I do that in React ?

First we have to use the .map() to go through these numbers, then We have to use ReactDOM.render to display the numbers.

## Each list item needs a unique ?

it needs a uniquely identifies.

## What is the purpose of a key ?

key helps the react identify which items have changed, are added or are removed, key should be given to the element inside the array to give the elements a stable identify.

**The Spread Operator**

## What is the spread operator ?

Spread syntax refers to the use of an ellipsis of three dots to expand an iterable object into the list of arguments.

## List 4 things that the spread operator can do

Copying an array
Concatenating or combining arrays
Using Math functions
Using an array as arguments
Adding an item to a list
Adding to state in React
Combining objects
Converting NodeList to an array

## Give an example of using the spread operator to combine two arrays

const animals = ['dogs','cats','camels','lion']
const animals2 = ['penguin','whale','sharks']
const allAnimals=[...animals,...animals2]

The Two arrays will combine to one array with length = 7

## Give an example of using the spread operator to add a new item to an array

const cars=['BMW','Toyota','Nissan','Mercedes']
const moreCars=['Musting','Ford',...cars]

The cars array strings will be in the moreCars array
so the final array will be
moreCars ['Musting','Ford','BMW','Toyota','Nissan','Mercedes']

## Give an example of using the spread operator to combine two objects into one

const objectOne = {hello: "🤪"}
const objectTwo = {world: "🐻"}
const objectThree = {...objectOne, ...objectTwo, laugh: "😂"}

**How to pass functions between components**

## In the video, what is the first step that the developer does to pass functions between components?

He made a function to pass through the objects.

## In your own words, what does the increment function do?

the increment function will go through the objects if the name will be the same it will return  as an array and counts again.

## How can you pass a method from a parent component into a child component?

methodName={this.methodName }

## How does the child component invoke a method that was passed to it from a parent component?

this.props.methodName()
