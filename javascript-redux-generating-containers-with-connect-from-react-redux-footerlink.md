

Finally, let's take a look at the filter link container component that renders a link with an active property and a click handler. First, I will write the map state to props function, which I'll call, maps straight to link props," because I have everything in a single file.

It's going to accept the state of the Redux chore and return the props that should be passed to the link. We only have a single such prop called, "active" that determines whether the link displays the current visibility filter.

When I paste this expression from the render method, I see that it references the filter prop of the filter link component. To tell whether a link is active, we need to compare this prop with the visibility filter value from the Redux chore sheet.

It is fairly common to use the container props when calculating the child props, so this is why props are passed as a second argument to "map straight to props." I will rename it to "own props" to make it clear we are talking about the container component's own props and not the props that are passed through the child, which is the return value of "map straight to props."

The second function I'm writing here is "map dispatch to props" or, to avoid name clashes in this JS bin, "map dispatch to link props." The only argument so far is the dispatch function. I'm going to need to look at the container component I wrote by hand to see what props depend on the dispatch function.

In this case, this is just the click handler where I dispatch the set visibility fill direction. The only prop I'm passing down is called, "on click." I declare it as an arrow function with no arguments, and I paste the dispatch code. But it references the props again, so I need to add "on props" as an argument, the second argument, to map dispatch to props function to you.

Finally, I will call the connect function from React Redux library to generate the filter link container component. I pass the relevant "maps straight to props" function as the first argument, the "map dispatch to props" as the second argument, and I call the function again with a link component which should be rendered. Now I can remove the old filter link implementation.

Let's recap the data flow in this example. The photo component renders three filter links, and each of them has a different filter prop that specifies which filter it corresponds to. This prop will be available on the "on props" object that both "map dispatch to props" and "map straight to props" will receive as the second argument.

We pass these two functions through the connect call, which will return a container component called, "filter link." The filter link will take the props that will return from the "map dispatch to props" and "map state to props" and pass them as props to the link component that it wraps.

We can now use the filter link container component and specify just the filter, but the underlying link component will have received the calculated active and on-click values."