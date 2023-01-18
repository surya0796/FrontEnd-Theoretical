# Redux ToolKit Notes

First of all with redux toolkit installation process requires:

```
npm install @reduxjs/toolkit react-redux
```
Instead of :

```
npm install redux react-redux redux-thunk
```
Redux toolkit provides redux-thunk and reselect out of the box support.

## What is Redux-Toolkit ?

Redux Toolkit is redux but with less boilerplate code. And the best part is you can even replace old redux logic with Redux Toolkit without breaking anything easily.
Redux Toolikt is bascially a wrapper around all the Redux APIs which automatically handles many tasks that developer had to write with redux. For eg: Adding redux dev tools extension in your project.

## Redux API changes
|                       |Redux            |Redux Toolkit       |
|    ---                |       ---       |       ---          |
|To create store:       |createStore()    |configureStore()    |
|To create reducer:     |Nothing          |createReducer()     |
|To create Actions:     |Nothing          |createActions()     |
|To combine Reducers:   |combineReducer() |No need. But for Nested Reducers use combineReducer()  |


1.  Static Website
2.  Multi Page Apps
3.  Single page App
4.  Server-Side Rendering with Hydration
5.  Static Site Generation with Hydration
6.  Incremental Static Regeneration
7.  Partial Hydration
8.  Islands
9.  Streaming SSR
10.  Resumability
      


 