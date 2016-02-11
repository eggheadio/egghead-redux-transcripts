So far we have covered the container components, the presentational components, the reducers, and the store. But we have not covered the concept of action creators, which you might see in the Redux talks and examples.

Let's consider the following example. I dispatched the add todo action from inside the button click handler. This is fine. However, it references the next todo ID variable, which added there alongside the add todo component.

Normally, it would be local. However, what if another component wants to dispatch the add todo action? It would need to have the access to next todo ID somehow. While I could make this variable global, it's not a very good idea.

Instead, it would be best if the components dispatching the add todo action did not have to worry about specifying the ID. Because the only information they really pass is the text of the todo being added.

I don't want to generate the ID inside the reducer, because that would make it non-deterministic. However, I can extract this code generating the action object into a function I will call add todo.

I pass the input value to add todo. Add todo is just the function that takes the text of the todo and constructs an action object representing add todo action. It has the type, add todo, it takes care of generating the unique ID and it includes the text.

Although extraction such functions is not required, it is very common pattern in Redux applications to keep them maintainable, so, like all these functions, action creators, and we usually place them separately from components or from reducers.

I will now extract other action creators from the components. I see that I have it set visible to filter the dispatch there, so I will change this to call this set visible the filter action creator with own props filter as the argument and is going to return the action that needs to be dispatched, so I'm declaring this set visible to filter function.

This is what I call an action creator, because it takes the arguments about the action and it returns the action object with the type set visible to filter and the filter itself.

You might think that this kind of code is boilerplate and you'd rather dispatch the action in line inside the component. However, don't underestimate how action creators document your software, because they tell your team what kinds of actions the components can dispatch, and this kind of information can be invaluable in large applications.

I will now scroll down to the last place where I call dispatch with an inline action object. I will now extract that to add toggle todo action creator, to which I pass the ID of the todo as the argument.

I'm now scrolling up to my action creators and I will add a new one that I call toggle todo. It accepts the ID as the argument and it returns the action of the type, toggle todo, and this ID.

Let's take a moment to consider how convenient it is to have all the action creators in a single place so that I can use them from components and tests without worrying about the action's internal structure.

Know that whether you use action creators or not, the data flow is exactly the same, because I just call the action creator to get the action object and then I call dispatch just like I did before, passing the action.