# Redux style guide

Redux is a library that we use for managing application state. Vanilla React supports managing component level state whereas Redux is used to manage the whole application state so Redux should only be used if you believe your application's state needs to be manage globally.

#### 1.Formatting
- Create a file to hold type names to so they are reusable.

```js
// constants.js
export const ADD_ITEM = "ADD_ITEM";
export const REMOVE_ITEM = "REMOVE_ITEM";
export const EDIT_ITEM = "EDIT_ITEM";
```

- Component actions should have the prefix action (e.g. ItemActions.js) in their filename, and the same with reducers (e.g. ItemReducer.js).

- We use the [redux-thunk](https://github.com/reduxjs/redux-thunk) middleware to control the dispatch of an action, allowing us to dispatch an action if certain conditions are met. This is useful for populating the state only after an api call has returned data, or can be used to chain multiple actions together.

```js

// ComponentActions.js
export default function getData(compID) {
  return dispatch =>
    fetch(API_ENDPOINT)
      .then(response => response.json())
      .then(payload => {
        dispatch({ type: GET_DATA, payload });
      });
}
```

- Initial states can be added as functions if necessary.

```js
// ComponentActions.js
 
 
function initialState() {
  return {
    todos: {},
    categories: {}
    errors: false
  }
}
 
export default function(state = initialState(), action) {
  switch (action.type) {
    ...
  }
}
```

- Using spread operator or object assign to not mutate state data

```js
// Good
case ADD_ITEM:
    return {
        ...state,
        todo_list:{
            ...state.list,
            ...action.payload
        }
    };
 
 
// Bad (unless the new payload has data from the previous state)
case ADD_ITEM:
    return {
        todo_list:{
            ...action.payload
        }
    };
```
