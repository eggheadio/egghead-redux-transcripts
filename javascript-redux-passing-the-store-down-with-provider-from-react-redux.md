

In the previous session, we implemented the provider component that uses the react advanced context feature to make this tool from the props available to every component in our rev.

If we pass it through the provider, we can read it in any other component from the context, which is really convenient for the container components. In fact, this is so convenient that you don't need to actually write the provider yourself, because it is included in a special library called React-Redux.

Note that it is not the same as Redux. This is a different library. These are react bindings to the Redux library. You can import the provider by destructuring the react-redux global object in JS bin, or if you use Babbel, and something like NPM, you can import provider with the braces, because it's a named expert from React-Redux package. Or if you write ES5 code, you can write var provider equals require react redux, or react redux global.provider.

Just like the provider we wrote before, the provider that comes with react-redux exposes this store you passed through. There's a prop on the context so the components can specify the context types, and then use this context store to subscribe to the store updates and dispatch actions.