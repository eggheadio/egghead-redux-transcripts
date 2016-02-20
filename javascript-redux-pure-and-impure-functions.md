

Before we proceed any further, it's important that you understand the difference between the pure and impure functions. The pure functions are the functions whose returned value depends solely on the values of their arguments.

Pure functions do not have any observable side effects, such as network or database calls. The pure functions just calculate the new value. You can be confident that if you call the pure function with the same set of arguments, you're going to get the same returned value. They are predictable.

Also, pure functions do not modify the values passed to them. For example, a 'squareAll' function that accepts an array does not overwrite the items inside this array. Instead, it returns a new array by using 'items.map()'.

On the opposite, impure functions may call the database or the network, they may have side effects, they may operate on the DOM, and they may override the values that you pass to them. This is going to be an important distinction because some of the functions that you're going to write in Redux have to be pure, and you need to be mindful of that.
