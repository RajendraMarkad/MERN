Sure, here are some simple interview questions based on actual scenarios you might encounter while working on a React project:

### Basic Questions

1. **State Management**
   - **Scenario**: You have a component that needs to manage a user's input in a form.
   - **Question**: How would you manage the state of this form in React? Explain with a simple example.
   - **Answer**: I would use the `useState` hook to manage the state of the form inputs. For example:
     ```javascript
     const [formData, setFormData] = useState({ name: '', email: '' });

     const handleChange = (e) => {
       setFormData({ ...formData, [e.target.name]: e.target.value });
     };

     return (
       <form>
         <input name="name" value={formData.name} onChange={handleChange} />
         <input name="email" value={formData.email} onChange={handleChange} />
       </form>
     );
     ```

2. **Component Lifecycle**
   - **Scenario**: You need to fetch data from an API when a component mounts.
   - **Question**: How would you handle this in a functional component?
   - **Answer**: I would use the `useEffect` hook to fetch data when the component mounts.
     ```javascript
     useEffect(() => {
       fetch('/api/data')
         .then(response => response.json())
         .then(data => setData(data));
     }, []);
     ```

3. **Conditional Rendering**
   - **Scenario**: Display a loading spinner while data is being fetched.
   - **Question**: How would you implement conditional rendering to show a loading spinner?
   - **Answer**: I would use a state variable to track the loading status and render the spinner conditionally.
     ```javascript
     const [loading, setLoading] = useState(true);
     const [data, setData] = useState(null);

     useEffect(() => {
       fetch('/api/data')
         .then(response => response.json())
         .then(data => {
           setData(data);
           setLoading(false);
         });
     }, []);

     return loading ? <Spinner /> : <DataDisplay data={data} />;
     ```

4. **Error Handling**
   - **Scenario**: You need to handle errors that occur during data fetching.
   - **Question**: How would you implement error handling in your data fetching logic?
   - **Answer**: I would use a try-catch block inside the `useEffect` to handle errors and update the state accordingly.
     ```javascript
     const [error, setError] = useState(null);

     useEffect(() => {
       const fetchData = async () => {
         try {
           const response = await fetch('/api/data');
           const result = await response.json();
           setData(result);
         } catch (err) {
           setError(err.message);
         } finally {
           setLoading(false);
         }
       };

       fetchData();
     }, []);

     return (
       {error ? <div>Error: {error}</div> : loading ? <Spinner /> : <DataDisplay data={data} />}
     );
     ```

### Advanced Questions

5. **State Management with Redux**
   - **Scenario**: You have a complex application state that needs to be accessed and modified by multiple components.
   - **Question**: How would you set up Redux to manage this state?
   - **Answer**: I would create a Redux store, define actions and reducers, and connect the components using `useSelector` and `useDispatch` hooks.
     ```javascript
     // actions.js
     export const increment = () => ({ type: 'INCREMENT' });

     // reducer.js
     const initialState = { count: 0 };
     const counterReducer = (state = initialState, action) => {
       switch (action.type) {
         case 'INCREMENT':
           return { ...state, count: state.count + 1 };
         default:
           return state;
       }
     };

     // store.js
     import { createStore } from 'redux';
     import counterReducer from './reducer';
     const store = createStore(counterReducer);

     // Component.js
     import { useSelector, useDispatch } from 'react-redux';
     const Counter = () => {
       const count = useSelector(state => state.count);
       const dispatch = useDispatch();
       return (
         <div>
           <p>{count}</p>
           <button onClick={() => dispatch(increment())}>Increment</button>
         </div>
       );
     };
     ```

6. **Performance Optimization**
   - **Scenario**: Your React application has performance issues when rendering large lists.
   - **Question**: How would you optimize the rendering of large lists in React?
   - **Answer**: I would use techniques like windowing or virtualization with libraries such as `react-window` or `react-virtualized`.
     ```javascript
     import { FixedSizeList as List } from 'react-window';

     const Row = ({ index, style }) => (
       <div style={style}>
         Row {index}
       </div>
     );

     const MyList = () => (
       <List
         height={150}
         itemCount={1000}
         itemSize={35}
         width={300}
       >
         {Row}
       </List>
     );
     ```

7. **Custom Hooks**
   - **Scenario**: You find yourself repeating the same logic across multiple components.
   - **Question**: How would you create a custom hook to reuse this logic?
   - **Answer**: I would extract the shared logic into a custom hook.
     ```javascript
     const useFetchData = (url) => {
       const [data, setData] = useState(null);
       const [loading, setLoading] = useState(true);
       const [error, setError] = useState(null);

       useEffect(() => {
         const fetchData = async () => {
           try {
             const response = await fetch(url);
             const result = await response.json();
             setData(result);
           } catch (err) {
             setError(err.message);
           } finally {
             setLoading(false);
           }
         };

         fetchData();
       }, [url]);

       return { data, loading, error };
     };

     // Using the custom hook
     const MyComponent = () => {
       const { data, loading, error } = useFetchData('/api/data');

       if (loading) return <Spinner />;
       if (error) return <div>Error: {error}</div>;
       return <DataDisplay data={data} />;
     };
     ```

8. **Context API**
   - **Scenario**: You need to provide global state to multiple components without prop drilling.
   - **Question**: How would you use the Context API to manage global state in your application?
   - **Answer**: I would create a context, provide it at a higher level in the component tree, and consume it in the necessary components.
     ```javascript
     // context.js
     const MyContext = React.createContext();

     const MyProvider = ({ children }) => {
       const [state, setState] = useState(initialState);
       return (
         <MyContext.Provider value={{ state, setState }}>
           {children}
         </MyContext.Provider>
       );
     };

     // Component.js
     import { useContext } from 'react';
     import MyContext from './context';

     const MyComponent = () => {
       const { state, setState } = useContext(MyContext);
       return (
         <div>
           {state.someValue}
           <button onClick={() => setState({ someValue: 'newValue' })}>
             Change Value
           </button>
         </div>
       );
     };
     ```

These questions and scenarios should help you demonstrate your practical experience and understanding of React during an interview.
