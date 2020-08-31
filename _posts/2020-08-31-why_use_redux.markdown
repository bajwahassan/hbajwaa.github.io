---
layout: post
title:      "Why use Redux?"
date:       2020-08-31 15:20:52 -0400
permalink:  why_use_redux
---


## What is Redux?
Redux is a state management tool for JavaScript applications. It’s generally used with React, but can be used with any UI layer or framework, including Angular, Vue, Ember, and vanilla JS. The core idea behind Redux is to store the entire state of an application in one central location.


## Why use Redux?
Managing the state when building complex things was such a pain in the neck until Redux arrived. Each component of an application can have direct access to the state of the application without having to send props down to child components from parent components. This can make the code simpler and, it can also improve rendering performance.
React is awesome, and developing a full application is entirely possible using nothing but react. However, as an application becomes more complex, use of plain old react is often not as straightforward.


## Data flow in redux
We have a store, actions and reducers in redux. Here is the redux data flow and we can provide a decoupled architecture that distinguishes data management from the UI. 
**Actions** can be sent when a user presses a button, load an app, etc. They can contain information that you want to add to the state.
**Reducers** listen for actions. When it hears that an action has been sent to it, it updates the state.
**Store** holds the Redux state and allows access and modifications to it. It’s the middleman between actions and reducers.
![Alt Text](https://res.cloudinary.com/practicaldev/image/fetch/s--m5BdPzhS--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://i.imgur.com/riadAin.gif)

## Example using redux : Showing top 25 movies
When we call listMovies(), GET_MOVIES action will be dispatched which sets the isLoading state to true. As soon as we get the response from the API, depending on the response either GET_MOVIES_SUCCESS or GET_MOVIES_FAIL actions are dispatched. If the API call succeeds the state is updated with the payload or if it fails the state is updated with the error.

```
import axios from 'axios';

export const GET_MOVIES = 'LOAD';
export const GET_MOVIES_SUCCESS = 'LOAD_SUCCESS';
export const GET_MOVIES_FAIL = 'LOAD_FAIL';

export default function reducer(state = { movies: [] }, action) { // setting the initial state
  switch (action.type) {
    case GET_MOVIESS:
      return { ...state, loading: true };
    case GET_MOVIES_SUCCESS:
      return { ...state, loading: false, movies: action.payload.data.feed.entry };
    case GET_MOVIES_FAIL:
      return {
        ...state,
        loading: false,
        error: 'Error while fetching repositories'
      };
    default:
      return state;
  }
}

export function listMovies() {
    return function(dispatch) {
        dispatch({type: GET_MOVIES});
        axios.get(`https://itunes.apple.com/us/rss/topmovies/limit=25/json`)
        .then(response => {
            console.log(response);
            dispatch({
                type: GET_MOVIES_SUCCESS,
                payload: response
            });
        })
        .catch((error) => {
            console.log(error);
            dispatch({type: GET_MOVIES_FAIL});
        })
    }
}
```


## Pros of using Redux
* Central store, any component can access any state from the store, there’s no need of passing props back and forth.
* Another way to look at centralised store, it persists the state of a component even after the component has unmounted.
* Prevents unnecessary re-renders, as when the state changes it returns new state which uses shallow copy.
* Testing will be easy as UI and data management are separated.



## Cons of using Redux
* No encapsulation. Any component can access the data which can cause security issues.
* Boilerplate code. Restricted design.
* As state is immutable in redux, the reducer updates the state by returning a new state every time which can cause excessive use of memory.
