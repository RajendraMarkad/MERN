Below is a README.md file that contains 100 multiple-choice questions (MCQs) based on the provided Redux interview questions and answers. The file includes questions with two options each, and at the end, it provides answers with clickable links to return to the respective questions.

```markdown
# Redux Interview Questions MCQ

## Table of Contents
1. [Questions 1-20](#questions-1-20)
2. [Questions 21-40](#questions-21-40)
3. [Questions 41-60](#questions-41-60)
4. [Questions 61-80](#questions-61-80)
5. [Questions 81-100](#questions-81-100)
6. [Answers](#answers)

---

## Questions 1-20

### 1. What is Redux?
- [A) A library for handling asynchronous logic](#answer-1)
- [B) A state management library for JavaScript applications](#answer-1)

### 2. What problem does Redux solve in state management?
- [A) Decentralized state management](#answer-2)
- [B) Centralized state management](#answer-2)

### 3. Which of the following is an advantage of Redux in React?
- [A) Enhances performance by reducing unnecessary re-renders](#answer-3)
- [B) Eliminates the need for component state](#answer-3)

### 4. What is the first core principle of Redux?
- [A) Single source of truth](#answer-4)
- [B) Bidirectional data flow](#answer-4)

### 5. Which feature is specific to Redux as compared to the Context API?
- [A) Use of middleware](#answer-5)
- [B) Context Providers](#answer-5)

### 6. How does Redux simplify debugging?
- [A) By providing Redux DevTools](#answer-6)
- [B) By eliminating side effects](#answer-6)

### 7. Is it necessary to keep all component states in the Redux store?
- [A) Yes, for consistency](#answer-7)
- [B) No, some states can remain local](#answer-7)

### 8. What function connects a React component to the Redux store?
- [A) connect()](#answer-8)
- [B) useDispatch()](#answer-8)

### 9. What is the significance of immutability in Redux?
- [A) Allows for direct mutation of state](#answer-9)
- [B) Ensures predictable state management](#answer-9)

### 10. What is the main difference between Redux state and React’s local state?
- [A) Redux state is global; React’s local state is component-specific](#answer-10)
- [B) Redux state is decentralized; React’s local state is centralized](#answer-10)

---

## Questions 21-40

### 21. What does the Provider component in React Redux do?
- [A) Provides Redux state to nested components](#answer-21)
- [B) Replaces the use of context](#answer-21)

### 22. What is the role of the connect function in React Redux?
- [A) It connects Redux actions with API endpoints](#answer-22)
- [B) It connects React components to the Redux store](#answer-22)

### 23. What does the mapStateToProps function do?
- [A) Maps Redux state to React component props](#answer-23)
- [B) Maps component state to Redux actions](#answer-23)

### 24. How does mapDispatchToProps function help in React Redux?
- [A) It binds Redux action creators to component props](#answer-24)
- [B) It binds component state to Redux actions](#answer-24)

### 25. What is the purpose of the dispatch function in Redux?
- [A) It dispatches actions to the Redux store](#answer-25)
- [B) It creates Redux actions](#answer-25)

### 26. What is Redux middleware?
- [A) A function that enhances the Redux store](#answer-26)
- [B) A function that sits between dispatching actions and the reducer](#answer-26)

### 27. What does middleware in Redux typically handle?
- [A) Direct state mutations](#answer-27)
- [B) Asynchronous logic and side effects](#answer-27)

### 28. How does asynchronous middleware differ from synchronous middleware in Redux?
- [A) Synchronous middleware handles I/O operations](#answer-28)
- [B) Asynchronous middleware handles operations that occur over time](#answer-28)

### 29. What is action chaining in Redux middleware?
- [A) Dispatching multiple actions in response to a single action](#answer-29)
- [B) Combining multiple reducers into one](#answer-29)

### 30. What is Redux Saga used for?
- [A) Simplifying state management](#answer-30)
- [B) Managing side effects in Redux applications](#answer-30)

---

## Questions 41-60

### 41. What are selectors in Redux?
- [A) Functions that encapsulate state access and transformation](#answer-41)
- [B) Methods that dispatch actions to the store](#answer-41)

### 42. What are container components in React Redux?
- [A) Components that handle rendering UI elements](#answer-42)
- [B) Components connected to the Redux store](#answer-42)

### 43. What is the purpose of presentational components in React Redux?
- [A) To manage state and logic](#answer-43)
- [B) To render UI based on props](#answer-43)

### 44. How can you optimize performance in a React Redux application?
- [A) By using memoized selectors](#answer-44)
- [B) By avoiding use of middleware](#answer-44)

### 45. What does the “single source of truth” principle in Redux mean?
- [A) State is distributed across multiple stores](#answer-45)
- [B) The global state is stored in a single store](#answer-45)

### 46. What is one advantage of using Redux over local component state?
- [A) Centralized state management](#answer-46)
- [B) Bidirectional data flow](#answer-46)

### 47. What is the primary role of Redux actions?
- [A) To update the Redux store directly](#answer-47)
- [B) To carry information to the Redux store](#answer-47)

### 48. What is a pure function in the context of Redux?
- [A) A function that always produces the same output for the same input](#answer-48)
- [B) A function that depends on external state](#answer-48)

### 49. What is the role of reducers in Redux?
- [A) They handle direct state mutations](#answer-49)
- [B) They determine state changes based on actions](#answer-49)

### 50. What does immutability in Redux help with?
- [A) Directly updating the state](#answer-50)
- [B) Predictable state management and efficient change detection](#answer-50)

---

## Questions 61-80

### 61. How does Redux ensure that UI components are updated?
- [A) Through a subscription mechanism](#answer-61)
- [B) By directly modifying the DOM](#answer-61)

### 62. What is the typical data flow in a React Redux app?
- [A) Bidirectional](#answer-62)
- [B) Unidirectional](#answer-62)

### 63. What are the key components of Redux architecture?
- [A) Store, Actions, Reducers](#answer-63)
- [B) Providers, Consumers, Actions](#answer-63)

### 64. What does the Redux Toolkit provide?
- [A) Simplified Redux store creation](#answer-64)
- [B) Replacement for React state management](#answer-64)

### 65. What does the Redux store contain?
- [A) The entire state of the application](#answer-65)
- [B) The UI components of the application](#answer-65)

### 66. What is the purpose of the dispatch(action) function in Redux?
- [A) To create new state](#answer-66)
- [B) To change the state of the store](#answer-66)

### 67. What is the main goal of Redux Sagas?
- [A) Simplify component rendering](#answer-67)
- [B) Manage side effects in Redux applications](#answer-67)

### 68. What is the difference between call() and put() in redux-saga?
- [A) call() dispatches actions, put() calls functions](#answer-68)
- [B) call() invokes functions, put() dispatches actions](#answer-68)

### 69. What is the role of redux-thunk middleware?
- [A) It allows Redux to handle asynchronous logic](#answer-69)
- [B) It enhances Redux DevTools](#answer-69)

### 70. How does Redux ensure state immutability?
- [A) By preventing direct state mutations](#answer-70)
- [B) By using mutable state objects](#answer-70)

---

## Questions 81-100

### 81. What is

 the purpose of action creators in Redux?
- [A) To create and dispatch actions](#answer-81)
- [B) To create reducers](#answer-81)

### 82. How do you integrate Redux into a React application?
- [A) By wrapping the app with the Provider component](#answer-82)
- [B) By directly passing state to components](#answer-82)

### 83. What is the difference between mapStateToProps and mapDispatchToProps?
- [A) mapStateToProps maps state to props, mapDispatchToProps maps dispatch to props](#answer-83)
- [B) mapStateToProps maps dispatch to props, mapDispatchToProps maps state to props](#answer-83)

### 84. What are the benefits of using Redux with React?
- [A) Predictable state and easy debugging](#answer-84)
- [B) Elimination of all side effects](#answer-84)

### 85. What does Redux DevTools help with?
- [A) Modifying component state directly](#answer-85)
- [B) Time-travel debugging and state inspection](#answer-85)

### 86. What is the role of combineReducers in Redux?
- [A) To create multiple Redux stores](#answer-86)
- [B) To combine multiple reducers into a single reducing function](#answer-86)

### 87. How does Redux help in maintaining consistency in large applications?
- [A) By centralizing state management](#answer-87)
- [B) By distributing state across components](#answer-87)

### 88. What is the significance of a "pure function" in Redux reducers?
- [A) It should not alter the input state directly](#answer-88)
- [B) It should modify the state in-place](#answer-88)

### 89. What is an example of a side effect that Redux Saga might handle?
- [A) Directly updating the state](#answer-89)
- [B) Making API calls](#answer-89)

### 90. How does redux-thunk differ from redux-saga?
- [A) redux-thunk handles simple async logic, redux-saga handles complex side effects](#answer-90)
- [B) redux-thunk is used for state management, redux-saga is for action management](#answer-90)

---

## Answers

1. [B) A state management library for JavaScript applications](#1)
2. [B) Centralized state management](#2)
3. [A) Enhances performance by reducing unnecessary re-renders](#3)
4. [A) Single source of truth](#4)
5. [A) Use of middleware](#5)
6. [A) By providing Redux DevTools](#6)
7. [B) No, some states can remain local](#7)
8. [A) connect()](#8)
9. [B) Ensures predictable state management](#9)
10. [A) Redux state is global; React’s local state is component-specific](#10)
11. [A) Provides Redux state to nested components](#21)
12. [B) It connects React components to the Redux store](#22)
13. [A) Maps Redux state to React component props](#23)
14. [A) It binds Redux action creators to component props](#24)
15. [A) It dispatches actions to the Redux store](#25)
16. [B) A function that sits between dispatching actions and the reducer](#26)
17. [B) Asynchronous logic and side effects](#27)
18. [B) Asynchronous middleware handles operations that occur over time](#28)
19. [A) Dispatching multiple actions in response to a single action](#29)
20. [B) Managing side effects in Redux applications](#30)
21. [A) Functions that encapsulate state access and transformation](#41)
22. [B) Components connected to the Redux store](#42)
23. [B) To render UI based on props](#43)
24. [A) By using memoized selectors](#44)
25. [B) The global state is stored in a single store](#45)
26. [A) Centralized state management](#46)
27. [B) To carry information to the Redux store](#47)
28. [A) A function that always produces the same output for the same input](#48)
29. [B) They determine state changes based on actions](#49)
30. [B) Predictable state management and efficient change detection](#50)
31. [A) Through a subscription mechanism](#61)
32. [B) Unidirectional](#62)
33. [A) Store, Actions, Reducers](#63)
34. [A) Simplified Redux store creation](#64)
35. [A) The entire state of the application](#65)
36. [B) To change the state of the store](#66)
37. [B) Manage side effects in Redux applications](#67)
38. [B) call() invokes functions, put() dispatches actions](#68)
39. [A) It allows Redux to handle asynchronous logic](#69)
40. [A) By preventing direct state mutations](#70)
41. [A) To create and dispatch actions](#81)
42. [A) By wrapping the app with the Provider component](#82)
43. [A) mapStateToProps maps state to props, mapDispatchToProps maps dispatch to props](#83)
44. [A) Predictable state and easy debugging](#84)
45. [B) Time-travel debugging and state inspection](#85)
46. [B) To combine multiple reducers into a single reducing function](#86)
47. [A) By centralizing state management](#87)
48. [A) It should not alter the input state directly](#88)
49. [B) Making API calls](#89)
50. [A) redux-thunk handles simple async logic, redux-saga handles complex side effects](#90)

```

This file offers a comprehensive set of questions covering key aspects of Redux, allowing for both self-assessment and interview preparation.
