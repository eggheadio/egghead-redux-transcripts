

In the previous lesson, we got rid of the top level chore variable and instead starting passing this chore as a prop to the to-do app component. So every component below receives this chore as a prop. We even have to do this for presentational components because sometimes they contain container components that need this chore to subscribe to the changes.

We have to write a lot of boiler plate code to pass this chore down as a prop. But there is another way, using the advanced React feature called context.

I'm creating a new component called provider. From its render method, it just returns whatever its child is. We can wrap any component in a provider, and it's going to render that component.

I'm changing the render call to render a to-do app inside the provider. I'm moving this tool prop from the to-do app to the provider component. The provider component will use the React advanced context feature to make this chore available to any component inside it, including grandchildren.

To do this, it has to define a special method get child context that will be called by React by using this props tool which corresponds to this chore that is passed to the provider as a prop just once.

This tool will be part of the context that the provider specifies for any its children and grandchildren. The to-do app is going to receive this context, and any component inside to do app is also going to receive this context object with this tool inside it.

However, there is an important condition for the context to work. This condition is that you have to specify child context types on the component that defines get child context. These are just React prop types definition, but unlike prop types, the child context types are essential for the context to be turned on. If you don't specify them, no child components will receive this context.

The container components currently access tool by props, but we're going to change this to read this chore from React context. To do that, we just wrap it to this.context. Similarly, in the render method, I'm also going to read this chore from the context instead of the props.

Finally, the context is opt-in for the receiving components, too, so you have to specify a special field called context types, which are similar to child context type. But, in this case, we are specifying which context we want to receive and not pass down. If you forget to declare the context types, the component will not receive the relevant context, so it is essential to remember to declare them.

What about the functional components that don't have this? It turns out that they also receive the context but as a second argument after the props. I'm destructuring the second argument and getting this chore from there. The second argument is the context.

Just like with the class components, I still have to add a property called, context types" that specifies which context I want to receive. In this case, I want to receive the chore from the provider. If I forget to declare the context types, my functional component will not receive the relevant context as a second argument. It's important to remember to declare them any time you use the context.

Finally, I'm replacing the props with the context when getting this chore for the filter link. I'm adding the context type declaration to the filter link so it receives the relevant context from the provider.

Now that the filter link receives this chore by context, I no longer need to pass it as a prop, so I'm removing its usage. I'm also removing the store prop from the footer because it doesn't need to pass it down anymore. I'm also removing this chore prop from the to-do app component because I no longer need to pass it down to the containers.

Now, instead of explicitly passing this chore down by props, we pass it implicitly by context.

Let's recap how we use the context to pass this chore down. We start by rendering the to-do app inside the provider component we defined above. The provider component just renders whatever you pass through it. In this case, it renders its children or the to do app component. However, it also provides the context to any components inside it including grandchildren.

The context contains just one key called the store. It corresponds to the store we passed as a prop to the provider component.

We pass this chore to the provider component in our render code and make it available to child components by defining the get child context with the store key pointing to that prop.

It is essential that the get child context is matched by child context types where we specify that the store key has prop type of object. Note that the child context types definition is absolutely required if you want to pass the context down the tree.

The benefit is that we don't need to pass this chore through the intermediate components. Instead, we can declare the context types on the container components that need access to the store so that they can retrieve it from the context instead of retrieving it from the props.

The context creates something like a wormhole between the visible to-do list component that reads the context and the provider that provides the context. This wormhole is only enabled because the context types declared on the visible to-do list include this chore that is defined in child context types of the provider component.

The at to-do is another component that needs access to this chore. It also opts into receiving it in the context by specifying the context types. This is why, in addition to props, it receives a second argument, which is the context. I'm using the destruction syntax to grab this chore from the context here.

The context works at any depth, so it is not necessary to put context types on the footer. The filter link is the component that directly uses the context, so this is the component that has to specify the context types so that it can use this chore by reading it from the context.

Context is a powerful feature, but in a way it contradicts the React philosophy of the explicit data flow. The context essentially allows global variables across the component tree. But global variables are usually a bad idea. Unless you're using it for dependency injection, like here when we need to make a single object available to all components, then probably you shouldn't use context.

Finally, the context API is not stable in React. It has changed before, and it is likely to change again. Try your best not to rely on it too much."