## Based off the diagram, What happens first, the 'render' or the ' componentDidMount '?

Render Happens first, and it will not pass to the componentDidMount until it passes through react updates DOM and refs .

## What is the very first thing to happen in the lifecycle of React?

The constructor is the first.

## Put the following thing in the order that they happen : -

1- Constructor.
2- Render.
3- ComponentDidMount.
4-React Updates.
5-ComponentWillUnmount.

## What does componentDidMount do ?

If you need to load anything using a network request or initialize the DOM, it should go here. this method is a good place to set up any subscriptions.