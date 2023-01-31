# Terminology

## Store
## Reducers
## Actions
## Payload
## Types
## State Immutability
## Reselect
## Immer
## normalized state

Advantages configureStore: 
-   no need of rootReducers anymore.
-   automatically adds thunk and set up the Redux DevTools Extension connection.
-   in default adds middlewares which validates redux code and points out errors like mutating state.

    
Advantages creatSlice:
-   no more swtich statements to write neither write default case.
-   no need to define action creators that correspond to each case reducer function we provide.To simplify, Redux Toolkit includes a createSlice function that will auto-generate the action types and action creators for you, based on the names of the reducer functions you provide.

There are a couple potential downsides to be aware of when importing and exporting slices.

-   First, Redux action types are not meant to be exclusive to a single slice. Conceptually, each slice reducer "owns" its own piece of the Redux state, but it should be able to listen to any action type and update its state appropriately. For example, many different slices might want to respond to a "user logged out" action by clearing data or resetting back to initial state values. Keep that in mind as you design your state shape and create your slices.

-   Second, JS modules can have "circular reference" problems if two modules try to import each other. This can result in imports being undefined, which will likely break the code that needs that import. Specifically in the case of "ducks" or slices, this can occur if slices defined in two different files both want to respond to actions defined in the other file.If you encounter this, you may need to restructure your code in a way that avoids the circular references. This will usually require extracting shared code to a separate common file that both modules can import and use. In this case, you might define some common action types in a separate file using createAction, import those action creators into each slice file, and handle them using the extraReducers argument.


The only truly necessary part here is the reducer itself. Consider the other parts:

-   We could have written the action types as inline strings in both places
-   The action creators are good, but they're not required to use Redux - a component could skip supplying a mapDispatch argument to connect, and just call this.props.dispatch({type : "CREATE_POST", payload : {id : 123, title : "Hello World"}}) itself
-   The only reason we're even writing multiple files is because it's common to separate code by what it does

CreateReducer: While the Redux Toolkit createReducer function can be really helpful, keep in mind that:

-   The "mutative" code only works correctly inside of our createReducer function
-   Immer won't let you mix "mutating" the draft state and also returning a new state value.


The most common reason to use middleware is to allow different kinds of async logic to interact with the store. This allows you to write code that can dispatch actions and check the store state, while keeping that logic separate from your UI.There are many kinds of async middleware for Redux, and each lets you write your logic using different syntax. The most common async middleware are:

-   redux-thunk, which lets you write plain functions that may contain async logic directly
-   redux-saga, which uses generator functions that return descriptions of behavior so they can be executed by the middleware
-   redux-observable, which uses the RxJS observable library to create chains of functions that process actions

CreateAsyncThunk : Each separate type of request needs repeated similar implementation:

-   Unique action types need to be defined for the three different cases
-   Each of those action types usually has a corresponding action creator function
-   A thunk has to be written that dispatches the correct actions in the right sequence
createAsyncThunk abstracts this pattern by generating the action types and action creators and generating a thunk that dispatches those actions.

Why do we use extraReducer?
The reducers property both creates an action creator function and responds to that action in the slice reducer. The extraReducers allows you to respond to an action in your slice reducer but does not create an action creator function.  You will use reducers most of the time. You would use extraReducers when you are dealing with an action that you have already defined somewhere else. The most common examples are responding to a createAsyncThunk action and responding to an action from another slice.

Extrareducers is actually like reducers with enhancements, but it's been built to handle more options, esecially other actions (like the ones generated in other slices or actions made by createAction or createAsyncThunk).

The builder function in extraReducers also accepts addDefaultCase and addMatcher in which the addDefaultCase acts as the default case in switch statement used by conventional reducers (reducers in the redux without toolkit) and,