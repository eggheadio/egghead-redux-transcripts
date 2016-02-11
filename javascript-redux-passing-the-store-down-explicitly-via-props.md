

In the previous lessons, we used this tool to up level variable to refer to the Redux chore. The components that access this chore, such as the container components, read this straight from it, subscribe to this chore, and dispatch actions on this chore using this chore top-level variable.

This approach works fine for JS bin example where everything is in a single file. However, it doesn't scale to real applications for several reasons.

First of all, it makes your container components harder to test because they reference a specific chore, but you might want to supply a different marks chore in the test. Secondly, it makes it very hard to implement universal replications that are rendered on the server, because on the server, you want to supply a different chore instance for every request because different requests have different data.

I'm going to start by moving this chore creation code to the bottom of the file where I render my React components. I'm going to change it slightly. Instead of creating this chore top-level variable, I will pass this chore I create as a prop to the top-level component, so it is completely injectable into it.

Every container component needs a reference to this chore so unfortunately, we have to pass it down to every component as a prop. It's less effort than passing different data through every component, but it's still inconvenient. So, don't worry, we'll find a better solution later, but for now, we need to see the problem.

The problem is that the container components need to have this chore instance to get this straight from a dispatch actions and subscribe to the changes. This time, I'm changing the container component to take this chore from the props using the ES6 destruction syntax, which just means chore equals props does chore."

I'm doing the same here. I'm just taking this chore from the props so I can call dispatch on it.

I need to make similar changes to other container components. In this case, I have this at to-do component, which is not exactly a container component, but it still needs its chore to dispatch the at to-do action, so I added it as a prop. I'm also going to add this chore to the photo component because, unfortunately, filter link needs it.

The photo component renders filter link. This is not convenient, but as I said, we'll figure out a way to avoid this later. For now, we need to pass this chore down so that every container component, such as filter link, can use it to subscribe to the changes, to read this state and to dispatch actions without relying on a top-level variable being available.

I'm changing the render method to read this chore from the props. Now, all containers read this chore instance from the props, and don't rely on a top-level variable that I removed.

Note that this change did not change the behavior or the data flow of this application. The container components subscribe to this chore, just like before, and update their state in response to its changes.

However, what changed is how they access this chore. Previously, they would access a top-level variable, but this approach does not scale to real-world applications. This is why, right now, I'm passing down this chore as a prop, so the container components can subscribe to it.

In the future lessons, we will see how to pass this chore down to the container components implicitly but without introducing the top-level variable."