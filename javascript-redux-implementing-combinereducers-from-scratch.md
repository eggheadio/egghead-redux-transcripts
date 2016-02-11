

In the previous lesson, we learned to use the combine reducer function, which comes with Redux and generates one reducer from several other reducers, delegating to them paths of the state tree.

To gain a deeper understanding of how exactly combined reducers works, we will implement it from scratch in this lesson.

Combine reducers is a function, so I'm writing a function declaration. Its only argument is the mapping between the state keys and the reducers, so I'm just going to call it Reducers.

The return value is supposed to be a reducer itself, so this is a function that returns another function. The signature of the return function is a reducer signature. It has the state and the action.

Now, I'm calling the object key's method, which gives me all the keys of the reducer's object. In our example, this is todos and the visibility filter.

Next, I'm calling the reduce method on the keys, because I want to produce a single value, such as the next state, by accumulating over every reducer key and calling the corresponding reducer.

Each reducer passed through the combine reducers function is only responsible for updating a part of the state. This is why I'm saying that the next state by the given key can be calculated by calling the corresponding reducer by the given key with the current state by the given key and the action.

The [inaudible 1:46] reduce wants me to return the next accumulated value from the call back, so I'm returning the next state. I'm also specifying an empty object as the initial next state, before all the keys are processed.

There we have it. This is a working reimplementation of combined reducers utility from Redux.

Let's briefly recap how it works. I'm calling combined reducers with an object whose values are the reducer functions and keys are the state field they manage. Inside the generated reducer, I'm retrieving all the keys of the reducers I passed to combine reducers, which is an array of strings, todos and visibility filter.

I'm starting with an empty object for my next state and I'm using the reduce operation of these keys to fill it gradually.

Notice that I'm mutating the next state object on every iteration. This is not a problem, because it is the object I created inside the reducer. It is not something passed from outside, so reducer stays a pure function.

To calculate the next state for a given key, it calls the corresponding reducer function, such as todos or visibility filter.

The generated reducer will pass through the child reducer only if part of its state by the key. If its state is a single object, it's only going to pass the relevant part, such as todos or visibility filter, depending on the current key, and save the result in the next state by the same key.

Finally, we use the array reduce operation with the empty object as the initial next state, that is being filled on every iteration until it is the return value of the whole reduce operation.

In this lesson, you learned how to implement the combined reducers utility that comes with Redux from scratch.

It is not essential to use in Redux, so it is fine if you don't fully understand how it works yet. However, it is a good idea to practice functional programming and understand functions can take other functions as arguments and return other functions, because knowing this will help you get more productive in Redux in the long term.