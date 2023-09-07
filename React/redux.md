# Redux

## Overview

**What is Redux?**
Redux is a state management library primarily used with React but can also be used with other JavaScript frameworks or libraries. It provides a predictable and centralized way to manage the state of your application. Redux follows the Flux architecture pattern and is particularly useful for managing complex, interconnected state in large-scale applications.

**Why use, and where to use Redux?**
Redux is commonly used in scenarios where you have multiple components that need to share and synchronize data. It's especially helpful when you have deeply nested components or when you need to pass data between components that are not directly connected. Redux helps you maintain a single source of truth for your application's state, making it easier to reason about and debug.


# Code

**How to use Redux**
```js
/* store.js */
// setup store
import { createStore } from 'redux';
import rootReducer from './reducers';

const store = createStore(rootReducer);

export default store;
```

```js
/* reducers.js */
// set up reducers (similar to setState functions)
const initialState = {
  todos: [],
};

const todoReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'ADD_TODO':
      return {
        ...state,
        todos: [...state.todos, action.payload],
      };
    case 'REMOVE_TODO':
      return {
        ...state,
        todos: state.todos.filter(todo => todo.id !== action.payload),
      };
    default:
      return state;
  }
};

export default todoReducer;
```

```js
/* actions.js */
// Set up actions (These are for using the reducer safely)
export const addTodo = (text) => ({
  type: 'ADD_TODO',
  payload: { id: Date.now(), text },
});

export const removeTodo = (id) => ({
  type: 'REMOVE_TODO',
  payload: id,
});
```

```js
/* TodoList.js */
// connect components
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { addTodo, removeTodo } from './actions';

function TodoList() {
  const todos = useSelector((state) => state.todos);
  const dispatch = useDispatch();

  const handleAddTodo = (text) => {
    dispatch(addTodo(text));
  };

  const handleRemoveTodo = (id) => {
    dispatch(removeTodo(id));
  };

  return (
    <div>
      <ul>
        {todos.map((todo) => (
          <li key={todo.id}>
            {todo.text}
            <button onClick={() => handleRemoveTodo(todo.id)}>Remove</button>
          </li>
        ))}
      </ul>
      <button onClick={() => handleAddTodo('New Todo')}>Add Todo</button>
    </div>
  );
}

export default TodoList;
```