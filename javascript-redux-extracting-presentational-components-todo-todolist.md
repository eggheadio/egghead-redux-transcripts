

In the last few lessons, we created user interface for a simple React and Redux to-do list where I can add items, toggle them as completed, and change the currently visible to-dos.

We do that by having a single to-do app component that has the input, the button for adding to-dos, the list of currently visible to-dos with click handler. It has this three links that let us change the currently visible to-dos.

The single component approach worked so far. However, we really want to have many components that can be used, tested, and changed by different people separately. So we're going to refactor our application in this lesson.

The first component I want to extract from the to-do app component is the to-do component that renders a single list item. I am declaring the to-do component as a function which React 14 allows me to do. I'm not sure which props it's going to have, so I'll leave them blank for now. I will just paste the list item I covered before.

The first thing I'm doing is removing the special key property because it's only needed when I enumerate an array. I'll use it later when enumerating many to-dos.

One of my goals with this refactoring is to make every component as flexible as it is reasonable. Right now, I have hardcoded that clicking a to-do always causes the toggle to-do action. This is perfectly fine to do in your app.

However, I prefer to have a bunch of components that don't specify any behaviors, and that are only concerned with how things look or how they render. I call such components the presentational components.

I would like to give to-do a presentational component, so I removed the on click handler. I promote it to be a prop so that anyone who uses to-do component can specify what happens on the click. You don't have to-do this in your Redux apps, but I find it to be a very convenient pattern.

Finally, while it doesn't have a lot of difference, I prefer to keep it explicit what is the data that the component needs to render. Instead of passing a to-do object, I pass completed and text fields as separate props.

Note how the to-do component is now a purely presentational component and doesn't specify any behavior. But it knows how to render at to-do.

The next component I create is called to-do list. It's also a presentational component. It's only concerned with how things look.

It accepts an array of to-dos. It's going to render an unordered list of them by calling the to-dos map function and rendering at to-do component for every to-do. It tells React to use to-do ID as the unique key for the elements. It spreads over the to-do object properties so the text and completed end up as props on the to-do component.

I need to specify what happens when a to-do is clicked. I could have dispatched an action here. Again, that would be fine, but I want it to a presentational component, so I'm going to call another function, called on to-do click, and pass the ID of the to-do, and let it decide what should happen. On to-do click is another prop for the to-do list.

Both to-do and to-do list are presentational components, so we need something I call, container components" to actually pass the data from this chore and to specify the behavior. In this case, the top level to-do app component acts as a container component. We will see more examples of container components in the future lessons.

In this case, it just renders the to-do list with visible to-dos as the to-dos, and with a callback that says that when on to-do click is called with a to-do ID, we should dispatch an action on the chore with the type toggle to-do and the ID of the to-do.

Let's recap again how this works. The do to app component renders a to-do list, and it passes a function to it that can dispatch an action. The to-do list component renders the to-do component and passes on click prop which calls on to-do click.

The to-do component just uses the on click prop it receives and binds it to the list item on click. This way, when it's called, the on to-do click is called, and this dispatches the action and updates the visible to-dos because the action updates the store."