**React Docs - Forms**

## What is a 'Controlled Component'?

the react component that renders a form also controls what happens in that form on subsequent user input, so it controlled the form and the react at the same time.

## Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why

the displayed value will update as the user types, because the event method is running on every keystroke to update the react state.

## How do we target what the user is entering if we have an event handler on an input field?

  this.setState({value: event.target.value})

**The Conditional (Ternary) Operator Explained**

## Why would we use a ternary operator?

allows us to specify that a certain block of code should be executed if a certain condition is met.

## Rewrite the following statement using a ternary statement

## if(x===y){console.log(true);} else {console.log(false); }

x===y ? 'true' :'false';
