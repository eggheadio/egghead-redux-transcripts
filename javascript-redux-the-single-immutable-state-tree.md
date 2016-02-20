

The first principle of Redux is whether your app is a really simple one like this counter example, or a complex application with a lot of UI, and change of state, you are going to represent the whole state of your application as a single JavaScript object.

All mutations, and changes to the state in Redux are explicit, so it is possible to keep track of all of them. In this case, I am logging every state change in the application in the console. You can see that, in the counter example, there isn't really much state to keep track of so it can be represented by a JavaScript number.

Here is a different example, a list of independent counters that I can add and remove. In this case, a single number is not enough to represent the state of the application, so we use an array of JavaScript numbers.

In a more complex application, there is more state to keep track of. This is a typical todo app, where I can add todos, I can cross them as completed ones, and I can change their current filter. Looking back at the history of the state changes, we can see that the initial state of the app was a JavaScript object, containing an array under the 'todos' key, and a string saying "SHOW_ALL", under 'visibilityFilter'.

When I added the first todo, it was added to the todos array, inside our state object. The to-do itself, is described by a plain JavaScript script object, saying it was not completed, and the text was saved. Every further change that the app, whether when I was crossing out the todos, or when I changed the visibilityFilter, resulted in this change to this state object, described in our whole application.

Now you know the first principle of Redux: Everything that changes in your application, including the data and the UI state, is contained in a single object, which we call the state or the state tree.
