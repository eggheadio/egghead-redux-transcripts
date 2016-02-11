

In the previous lesson, I extracted the to-do and to-do list components from the to-do app component. In this lesson, I will continue extracting other presentational components to separate the looks from the behavior.

Now I want to extract the input and the button into a separate component called, at to-do." I'm declaring at to-do as a functional component that doesn't accept any props. I'm going to return these copy pasted input in button, but I'm wrapping them in a div because a component needs to have a single root element.

The functional components don't have instances. However, instead of using this, I can use a local variable called, "input," that I'm going to close over so I can write to it in the callback graph and I can read from it in the event handler.

Like previously, I want it to be a presentational component and not specify behavior, so I just called the function called, "on at click," passing the current input value. I make on at click a prop so that the component that uses at to-do can specify what happens when that button is clicked.

Again, the to-do app component acts as a container component for the at to-do. It specifies that when add button is clicked, we should dispatch an action with the type at to-do, the corresponding text, and the next to-do ID.

The last component I want to extract today is the footer, which contains all these three filter links. I'm creating a new functional component called, "footer." I'm not sure which props it needs, so I skip them. I paste the markup. It seems that the filter link need the visibility filter, so I add it as a prop.

I would like the footer and the filter link to be presentational components. However, the filter link includes a short dispatch call. I am replacing it with an on click call. I pass the filter as the single parameter for the calling component's convenience. I add on click to the props.

Now I need to specify it every time filter link is used. I add on filter click to the footer. I pass on click equals on filter click for every filter link in the footer, so whatever we pass to the footer as on filter click prop is going to end up in the filter link as on click.

Now I can use the footer component I just defined inside my to-do app component. I need to pass to props, one of them is the visibility filter so it can highlight the active link. Another prop is on filter click where I say that whenever a filter is clicked, I want to dispatch an action with a type set visibility filter and the filter being clicked.

Finally, I just noticed that the to-do app component doesn't actually have to be a class. I can turn it into a function. I prefer to-do that when possible.

Instead of destructuring the props inside the render method, I am now doing it inside the argument. I can remove now the destructuring. I'm also going to remove the render method declaration. The visible to-dos are only used in a single place, so I'm moving the get visible to-dos call to the to-do list to-dos prop declaration. Now the body of my function is just a single expression, so I can get rid of the return statement and unintended code to make it look nicer.

This concludes the initial refactoring of the to-do list application into a single container component called to-do app and many presentational components that are only concerned with how things look. Let's recap the data flow in this example.

We have a single container component called to-do app. We re-render it any time the store changes. It receives the keys of the global state object as the props, so it receives the to-dos and the visibility filter values.

The first component it renders is called at to-do. At to-do is a presentational component that renders an input and a button. When the button is clicked, it passes the current input value to the on app click function.

On app click function is a prop for the at to-do component. In this case, it is specified by the to-do app, which says that when the button is clicked, it should dispatch an action containing the current text in the action object. Dispatching the at to-do action will call our reducer, update this chore state with the new to-dos, and re-render the do app component with the new to-dos.

The to-dos themselves are rendered by the to-do list presentational component that receives two props, the currently visible to-dos and the on to-do click callback.

The to-do list component receives an array of to-dos, and it maps over them, rendering individual to-do components. It uses the spread operator to pass every property of the to-do object as a prop to to-do component. It specifies the on click handler as calling on to-do click with the ID of the particular to-do.

The to-do component is defined above. It is also a presentational component, so it doesn't specify the behavior. It says that when a list item is clicked, it should call the on click handler. Being a presentational component, it specifies how the component looks in different circumstances. In this case, it uses the completed prop to choose between two different styles of the to-do item.

The to-do list is also presentational component. It delegates actually handling the click to on to-do click prop. It passes the ID of the to-do being clicked.

Finally, the to-do app component reacts to it by dispatching an action containing the ID of the to-do clicked and the type toggle to-do. The store will call our reducer and update the state of the application, re-rendering the to-do app component with the new to-dos.

The footer component receives the current visibility filter as a prop and also receives the on filter click callback that sets the current visibility filter. The footer component renders three filter links, passing down their respective filter values, the on click handler, and the current visibility filter.

The filter link component being a presentational component doesn't know what to-do when it's clicked, so it calls the on click callback, passing the filter, which is different for each of those links, as an argument. The footer delegates handling the click of the filter link to its own prop, called on filter click.

Finally, the to-do app component being the container component in our application specifies the behavior, which in this case means that when the filter link is clicked, it should dispatch an action with the type set visibility filter, and the new filter.

Separation of the presentational components is not required in Redux, but I recommend this pattern because it decouples your rendering from Redux. So if you later choose to move your project to another framework, such as Relay, you will not have to change all your components because you can keep the presentational components exactly the same.

This approach also has downsides, such as that you have to thread a lot of props through the components to get them to the list components, including the callbacks. This problem can be easily solved by introducing many intermediate container components as we will see in the next lesson."