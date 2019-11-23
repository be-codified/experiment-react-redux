# Experiment React Redux

## Goal

Render a list of articles I’ve been collecting with a news aggregator app. The response from the news database is going be a collection of articles.

## Notes

To change something in the state, you need to dispatch an action.

Example of actions:

```
{ type: 'ADD_TODO', text: 'Go to swimming pool' }
{ type: 'TOGGLE_TODO', index: 1 }
{ type: 'SET_VISIBILITY_FILTER', filter: 'SHOW_ALL' }
```

Finally, to tie state and actions together, we write a function called a `reducer`. Again, nothing magical about it—it’s just a function that takes state and action as arguments, and returns the next state of the app.

Example of reducer:

```
function visibilityFilter(state = 'SHOW_ALL', action) {
  if (action.type === 'SET_VISIBILITY_FILTER') {
    return action.filter
  } else {
    return state
  }
}
```

And we write another reducer that manages the complete state of our app by calling those two reducers for the corresponding state keys:

```
function todoApp(state = {}, action) {
  return {
    todos: todos(state.todos, action),
    visibilityFilter: visibilityFilter(state.visibilityFilter, action)
  }
}
```

This is basically the whole idea of Redux.

## How to run

#### Start server

```
npm run start-dev
```

Go to `http://localhost:8888/`

## Resources

- [Beginner’s guide to react/redux — how to start learning and not be overwhelmed](https://medium.com/netscape/beginners-guide-to-react-redux-how-to-start-learning-and-not-be-overwhelmed-af04353101e)
- [Beginner’s guide to react/redux —painting a mental model](https://blog.cloudboost.io/beginners-guide-to-react-redux-painting-a-mental-model-ed0279d55836)
- [React + Redux: Architecture Overview - MoFed - Medium](https://medium.com/mofed/react-redux-architecture-overview-7b3e52004b6e)
- [Redux core concepts](https://redux.js.org/introduction/core-concepts)
- [Redux cycle](https://res.cloudinary.com/practicaldev/image/fetch/s--VtRaY29J--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/fewc8ez6r2e2agah717y.png)
- [How to setup PostgreSQL on MacOS](https://www.robinwieruch.de/postgres-sql-macos-setup)
