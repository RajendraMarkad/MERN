# Redux Toolkit and [Redux-Saga](#saga):

### Redux Toolkit Cheatsheet

1. **Purpose**:
   - Simplifies Redux setup and usage.
   - Provides built-in utilities to manage state easily.

2. **Key Concepts**:
   - **Store**: Central place to hold your app’s state.
   - **Slice**: A reducer and actions bundled together for a feature.
   - **Reducers**: Functions to handle state updates.
   - **Actions**: Payloads of information that send data from your app to your Redux store.
   - **Selectors**: Functions to get specific pieces of state.

3. **Setup**:
   - Use `createSlice` to create actions and reducers.
   - Use `configureStore` to create the store with reducers and middleware.

4. **Async Logic**:
   - Use `createAsyncThunk` for handling asynchronous logic like API calls.

5. **Usage**:
   - `dispatch` actions to update state.
   - Use `useSelector` to read state.
   - Use `useDispatch` to dispatch actions in components.

### Redux-Saga Cheatsheet

1. **Purpose**:
   - Manages side-effects (like API calls) in Redux.
   - Uses generator functions to handle async flows.

2. **Key Concepts**:
   - **Saga**: A function that can pause and resume, handling complex async logic.
   - **Effects**: Instructions to the middleware about what to do (e.g., call a function, put an action).

3. **Setup**:
   - Use `createSagaMiddleware` to create middleware.
   - Use `sagaMiddleware.run` to start your sagas.

4. **Common Effects**:
   - `call`: Executes a function and waits for it to finish.
   - `put`: Dispatches an action to the store.
   - `take`: Waits for a specific action to be dispatched.

5. **Usage**:
   - Write sagas to handle async operations.
   - Use effects to manage async flows and update state based on actions.

Alright! Let’s break it down into simple steps using Redux Toolkit and Redux-Saga. Imagine Redux is like a big toy box, and Redux Toolkit and Redux-Saga are tools that make managing your toys easier.

### Redux Toolkit Basics

#### 1. **What is Redux Toolkit?**
Redux Toolkit is a special toolkit that helps you manage your toy box (state) more easily. It simplifies a lot of the complex work involved in setting up Redux.

#### 2. **Setting Up Redux Toolkit**

1. **Install Redux Toolkit**
   First, you need to install Redux Toolkit. It’s like buying the toolkit from a store.
   ```bash
   npm install @reduxjs/toolkit react-redux
   ```

2. **Create a Slice**
   A slice is like a drawer in your toy box where you keep related toys (state). It has:
   - **State**: The toys (data) you have.
   - **Reducers**: How you can change your toys.

   Here’s how you create a slice for a counter toy:

   ```javascript
   import { createSlice } from '@reduxjs/toolkit';

   const counterSlice = createSlice({
     name: 'counter',
     initialState: { value: 0 },
     reducers: {
       increment: (state) => { state.value += 1; },
       decrement: (state) => { state.value -= 1; }
     }
   });

   export const { increment, decrement } = counterSlice.actions;
   export default counterSlice.reducer;
   ```

3. **Create a Store**
   The store is like the main toy box where all your toys (state) are kept. You need to create it and tell Redux Toolkit which slices to use.

   ```javascript
   import { configureStore } from '@reduxjs/toolkit';
   import counterReducer from './counterSlice';

   const store = configureStore({
     reducer: {
       counter: counterReducer
     }
   });

   export default store;
   ```

4. **Provide the Store to Your App**
   Wrap your app with a `<Provider>` to give all parts of your app access to the toy box.

   ```javascript
   import React from 'react';
   import ReactDOM from 'react-dom';
   import { Provider } from 'react-redux';
   import store from './store';
   import App from './App';

   ReactDOM.render(
     <Provider store={store}>
       <App />
     </Provider>,
     document.getElementById('root')
   );
   ```

5. **Using the State and Dispatching Actions**
   In your components, you can use `useSelector` to get toys from the toy box and `useDispatch` to change them.

   ```javascript
   import React from 'react';
   import { useSelector, useDispatch } from 'react-redux';
   import { increment, decrement } from './counterSlice';

   function Counter() {
     const count = useSelector((state) => state.counter.value);
     const dispatch = useDispatch();

     return (
       <div>
         <h1>Count: {count}</h1>
         <button onClick={() => dispatch(increment())}>Increment</button>
         <button onClick={() => dispatch(decrement())}>Decrement</button>
       </div>
     );
   }

   export default Counter;
   ```

## Redux-Saga Basics <a id='saga'></a>

#### 1. **What is Redux-Saga?**
Redux-Saga is like a magical helper that manages complicated toy arrangements. It helps you handle actions that involve waiting (like fetching data) without making your main toy box messy.

#### 2. **Setting Up Redux-Saga**

1. **Install Redux-Saga**
   Install it to add the magical helper to your toy box setup.
   ```bash
   npm install redux-saga
   ```

2. **Create a Saga**
   A saga is like a guide for managing complicated actions.

   ```javascript
   import { call, put, takeEvery } from 'redux-saga/effects';
   import { increment, decrement } from './counterSlice';

   function* incrementAsync() {
     yield new Promise((resolve) => setTimeout(resolve, 1000)); // Simulate a delay
     yield put(increment());
   }

   function* watchIncrement() {
     yield takeEvery('counter/incrementAsync', incrementAsync);
   }

   export default watchIncrement;
   ```

3. **Create a Saga Middleware and Add It to the Store**
   This tells the store to use the magical helper.

   ```javascript
   import { configureStore } from '@reduxjs/toolkit';
   import createSagaMiddleware from 'redux-saga';
   import counterReducer from './counterSlice';
   import watchIncrement from './counterSaga';

   const sagaMiddleware = createSagaMiddleware();

   const store = configureStore({
     reducer: {
       counter: counterReducer
     },
     middleware: (getDefaultMiddleware) =>
       getDefaultMiddleware().concat(sagaMiddleware),
   });

   sagaMiddleware.run(watchIncrement);

   export default store;
   ```

4. **Dispatch Async Actions**
   You can now dispatch actions that trigger your saga.

   ```javascript
   import React from 'react';
   import { useDispatch } from 'react-redux';
   import { incrementAsync } from './counterSlice';

   function Counter() {
     const dispatch = useDispatch();

     return (
       <div>
         <button onClick={() => dispatch({ type: 'counter/incrementAsync' })}>
           Increment after 1 second
         </button>
       </div>
     );
   }

   export default Counter;
   ```

### Summary
- **Redux Toolkit**: Simplifies setting up and managing your toy box (state) with slices and a store.
- **Redux-Saga**: Handles complicated actions like waiting or fetching data, keeping your toy box clean.

Think of Redux Toolkit as making your toy box easier to organize and Redux-Saga as a special assistant for managing tricky tasks.
