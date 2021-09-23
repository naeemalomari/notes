## Object literals.
## What is Objects ?
## Objects is  a set of variables and functions to create a model of a something you would recognize from the real world, in an object variables become a properties, and functions become a methods, and also they have names called a key, this key have **only** have one name, the value of this name could be a String, Boolean, Numbers, Array or even another object.
*[I recommend to watch this video ](https://www.simplilearn.com/tutorials/javascript-tutorial/javascript-objects)*.
## How to create an object ?
## Literal notation the easiest and most popular wat to create objects, separate each keep from it's value using **colon**, and separate each property and method with a comma. treat the values like you do for the variables, string live in quotes too and arrays in square brackets.
## This is how to write an object : **Let hotelName = hotel . name ;**
**Let roomsFree=hotel.checkAvailablity();**
## where the hotel is the object, the dot notation is the member operator, and the property /method name is checkAvailablity();
## Document Object Model :
## methods that find elements in the DOM tree are called DOM queries, this queries is available once else you should use a variable to store the results of this query .caching the selection is the saves that browser looking through the DOM tree to find the same element.
## return individual elements can be in two ways -> getElementById() AND querySelector().
## No two elements can share the same value for the Id attribute getElementById() is the most efficient and quickest way to access an element.
## querySelector() it's very flexible because it's parameter is a CSS selector but it's more recent addition to the DOM.
## how ?
**document.getElementById('one')**
## where document object, . member operator, getElementById('one') is the method and ('one') is the parameter.
## item() method specify the index number of the element you want as a parameter but first you have to check if there is another number stored in the same element by using length property, this is the first way to select an element from a node list , the second one is array syntax and it's better than the item() because it's faster.
## Adding or removing HTML content : there is two ways to add and remove *The inner HTML property, which you have to create variable holding markup, select element whose content you want to update and update content of selected element with new markup and the second way is DOM manipulation methods, create new text node, create new element node, add text node to element node, select element you want to add the new fragment to and append the new fragment to the selected element.
## there are two steps to accessing and updating attributes, select the element node that carries the attribute and follow it with a period symbols, and then there is some method or properties you have to use to work with the element's attribute , here is some of these methods getAttribute(),hasAttribute(),setAttribute();removeAttribute(), and the properties **className and Id.** 

*[Here is my source](https://slack-files.com/files-pri-safe/TNGRRLUMA-F0230Q81ZRV/javascript_and_jquery_interactive_jon_du__1_.pdf?c=1622300000-73f93ecb4b6f174e)*.