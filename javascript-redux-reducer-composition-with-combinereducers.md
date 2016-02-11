

In the previous lesson we learned how to use the reducer composition pattern to let different reducers handle different parts of the straight tree, and then combine their results.

This pattern is so common that it's present in most Redux applications. This is why Redux provides a function called combineReducers that lets you avoid writing this code by hand. Instead, it generates the top level reducer for you.

The only argument to combine reducers is an object. This object lets me specify the mapping between the straight field names, and the reducers managing them. The return value of the combineReducer is called a Reducer function, which is pretty much equivalent to the reducer function I wrote by hand previously.

The keys of the object I configure combined reducers with correspond to the fields that the straight object is going to manage. The values of the object I have asked to combineReducer, are the producers we should call to update the correspondence straight fields.

This combineReducer call says that the ToDo's field inside the straight object managers will be updated by the reduce-reducer, and the visibility filter field inside the straight object will be updated by calling the visibility filter reducer. The results will be assembled into a single object. In other words, it behaves pretty much exactly as the function commented down below.

Finally, I will establish a useful convention. I will always name my reducers after the straight keys they manage. Since the key names and the value names are now the same, I can omit the values thanks to the ES6 object literal shorthand notation.

In this lesson, you learned how to generate a simple reducer that calls many reducers to manage parts of its tree by using the combineReducers utility function.