

In the simplest counter example, I update the document body manually any time this tool state changes. But, of course, this approach does not scale to complex applications. Instead of manually updating the DOM, I'm going to use React.

I'm adding to script the [inaudible 00:18] corresponding to React and react-dom packages and a root dev to render to. Now I can call the ReactDOM.render with my root component. The render function is called any time this store state changes, so I can safely pass the current state of this store as a prop to my root component.

Since this state is held inside the Redux store, the counter component can be a simple function, which is a supported way of declaring components since React 14.

I want to add, decrement, and increment buttons to the component, but I don't want to hard-code the Redux dependency into the component. So I just add on increment and on decrement props as callbacks. In my render method, I pass the callbacks that call store.dispatch with appropriate actions. Now the application state is updated when I click the buttons.

Let's recap how this application works. The counter component is what I call a dump component. It does not contain any business logic. It only specifies how the current application state transforms into renderable output and how the callbacks, passed via props, are bound to the event handlers.

When we render a counter, we specify that its value should be taken from the Redux store current state. When the user presses increment" or "decrement," we dispatch corresponding action to the Redux store. Our reducer specifies how the next state is calculated based on the current state and the action being dispatched.

Finally, we subscribe to the Redux store, so our render function runs anytime the state changes, so the counter gets the current state."