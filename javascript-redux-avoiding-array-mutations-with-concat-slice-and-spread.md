

In this lesson, I use Expect Library to make test assertions, and deepFreeze to make sure that my code is free of mutations.

Let's say that I want to implement a count release application. I would need to write a few functions that operate on its [?] trait, and its trait is an array of JavaScript numbers representing the individual counters.

The first function I want to write is called Add Counter, and all it should do is to append a zero at the end of the past array.

At first, I use the array push method to add a new item at the end of the array, and it works. However, we need to learn to avoid mutations in Redux, and I'm enforcing this by calling deepFreeze on the original array.

Now my attempt to push does not work. It cannot add a new property to a frozen object. Instead of push, I'm going to use the concat method, which does not modify the original array.

Now the tests pass without mutations, and I can also use the new ES6 erase spread operator to write the same code in a more concise way.

My next function is called Remove Counter, and it accepts two arguments, an array of numbers, and the index of the number to skip from the array.

If I've got three numbers and I'm passing one as the second argument, I expect to receive an array with two numbers with the second item skipped in the result array.

Usually, to delete an item from the array, I would use the splice method. However, splice is a mutation method, so you can't use it in Redux.

I'm going to deepFreeze the array object, and now I need to figure out a different way to remove an item from the array without mutating it.

I'm using a method called slice here, and it doesn't have anything to do with splice. It is not mutating, and it gives me a part of the array from some beginning to some end index.

What I'm doing is that I'm taking the parts before the index I want to skip and after the index I want to skip, and I concatenate them to get a new array.

Finally, instead of writing it as a method chain with concat calls, I can use the ES6 erase spread operator to write it more concisely.

Now that we implemented adding and removing counters, let's implement increment in the counter. The increment counter function takes your arguments, the array and the index of the counter that should be incremented, so the return value has the same count of items, but one of them is incremented.

Directly setting the array value at index works, but this is a mutation. If we add a deepFreeze call, it's not going to work anymore, so how do we replace a single value in the array without mutating it?

It turns out that the answer is really similar to how we remove an item. We want to take the slice before the index, concat it with a single item array with a new value, and then concat it with the rest of the original array.

Finally, with the ES6 spread operator, we can spread over the left part of the array, specify the new item, and then spread over the right part of the original array, and this looks much nicer.

In this lesson, you learned how to use the concat method or the spread operator, and the slice method to add, remove, and change items in arrays without mutating them, and how to protect yourself with deepFreeze from mutation in your tests.