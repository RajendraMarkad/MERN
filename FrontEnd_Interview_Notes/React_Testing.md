#React Testing Cheat Sheet

#### Types of Testing

1. **Unit Testing**
   - **Definition**: Tests individual components or functions in isolation.
   - **Tools**: Jest, React Testing Library.
   - **Example**: Testing a single React component’s rendering logic.

2. **Integration Testing**
   - **Definition**: Tests how multiple units (components/functions) work together.
   - **Tools**: Jest, React Testing Library.
   - **Example**: Testing a form submission process that involves multiple components.

3. **End-to-End (E2E) Testing**
   - **Definition**: Tests the entire application flow from start to finish.
   - **Tools**: Cypress, Selenium, Playwright.
   - **Example**: Testing a user’s journey through a signup process.

4. **Snapshot Testing**
   - **Definition**: Captures the rendered output of components and compares it to previous snapshots to detect changes.
   - **Tools**: Jest.
   - **Example**: Ensuring UI components do not change unexpectedly.

5. **Performance Testing**
   - **Definition**: Tests the performance and speed of the application.
   - **Tools**: Lighthouse, WebPageTest.
   - **Example**: Measuring page load times and responsiveness.

#### Best Practices

1. **Test Naming**:
   - Use descriptive test names to clearly explain what is being tested.
   ```javascript
   test('renders a button with correct text', () => { ... });
   ```

2. **Test Structure**:
   - Arrange: Set up the conditions for the test.
   - Act: Perform the action that triggers the behavior you want to test.
   - Assert: Check the outcome against the expected result.
   ```javascript
   test('increments counter on button click', () => {
     // Arrange
     render(<Counter />);
     const button = screen.getByText('Increment');

     // Act
     fireEvent.click(button);

     // Assert
     expect(screen.getByText('Count: 1')).toBeInTheDocument();
   });
   ```

3. **Mocking and Stubbing**:
   - Use mocks and stubs to simulate dependencies and control their behavior.
   - Example: Mocking API calls with `jest.mock`.
   ```javascript
   jest.mock('axios', () => ({
     get: jest.fn(() => Promise.resolve({ data: { ... } })),
   }));
   ```

4. **Avoid Testing Implementation Details**:
   - Focus on testing the output and behavior of components rather than their internal state or methods.
   ```javascript
   // Good: Testing the rendered output
   expect(screen.getByText('Hello World')).toBeInTheDocument();
   
   // Bad: Testing component state directly
   expect(component.state().text).toBe('Hello World');
   ```

5. **Use `data-testid` for Selectors**:
   - Use `data-testid` attributes to reliably select elements in tests.
   ```javascript
   <button data-testid="submit-button">Submit</button>
   
   // Test
   const button = screen.getByTestId('submit-button');
   ```

6. **Run Tests in Parallel**:
   - Take advantage of Jest’s ability to run tests in parallel to speed up the testing process.
   ```json
   // jest.config.js
   module.exports = {
     maxWorkers: "50%",
   };
   ```

7. **Continuous Integration (CI)**:
   - Integrate tests into your CI pipeline to ensure they run automatically on every push or pull request.

8. **Coverage Reports**:
   - Generate test coverage reports to ensure all parts of your application are adequately tested.
   ```json
   // package.json
   "scripts": {
     "test": "jest --coverage"
   }
   ```

#### Example Test Setup

```javascript
import { render, screen, fireEvent } from '@testing-library/react';
import '@testing-library/jest-dom/extend-expect';
import MyComponent from './MyComponent';

// Unit Test Example
test('renders a button with correct text', () => {
  render(<MyComponent />);
  const button = screen.getByText('Click Me');
  expect(button).toBeInTheDocument();
});

// Integration Test Example
test('submits form successfully', () => {
  render(<MyForm />);
  fireEvent.change(screen.getByLabelText(/name/i), { target: { value: 'John Doe' } });
  fireEvent.click(screen.getByText(/submit/i));
  expect(screen.getByText(/success/i)).toBeInTheDocument();
});
```

### React Testing Library Interview Questions

1. **Basic Rendering Test**
   - **Question**: How would you test if a React component renders correctly with React Testing Library?
   - **Answer**:
     ```javascript
     import { render, screen } from '@testing-library/react';
     import MyComponent from './MyComponent';

     test('renders MyComponent with correct text', () => {
       render(<MyComponent />);
       const element = screen.getByText('Hello World');
       expect(element).toBeInTheDocument();
     });
     ```

2. **Event Handling**
   - **Question**: How do you test a button click event that changes the component's state?
   - **Answer**:
     ```javascript
     import { render, screen, fireEvent } from '@testing-library/react';
     import Counter from './Counter';

     test('increments counter on button click', () => {
       render(<Counter />);
       const button = screen.getByText('Increment');
       fireEvent.click(button);
       const counter = screen.getByText('Count: 1');
       expect(counter).toBeInTheDocument();
     });
     ```

3. **Form Submission**
   - **Question**: How would you test form submission and validate if the form data is processed correctly?
   - **Answer**:
     ```javascript
     import { render, screen, fireEvent } from '@testing-library/react';
     import MyForm from './MyForm';

     test('submits form with correct data', () => {
       render(<MyForm />);
       fireEvent.change(screen.getByLabelText(/name/i), { target: { value: 'John Doe' } });
       fireEvent.click(screen.getByText(/submit/i));
       expect(screen.getByText(/submission successful/i)).toBeInTheDocument();
     });
     ```

4. **Mocking API Calls**
   - **Question**: How can you mock an API call in a React component test?
   - **Answer**:
     ```javascript
     import { render, screen, waitFor } from '@testing-library/react';
     import axios from 'axios';
     import MyComponent from './MyComponent';

     jest.mock('axios');

     test('fetches and displays data from API', async () => {
       axios.get.mockResolvedValue({ data: { message: 'Hello World' } });
       render(<MyComponent />);
       const element = await waitFor(() => screen.getByText('Hello World'));
       expect(element).toBeInTheDocument();
     });
     ```

5. **Testing Component Props**
   - **Question**: How do you test a component that receives props and renders content based on those props?
   - **Answer**:
     ```javascript
     import { render, screen } from '@testing-library/react';
     import Greeting from './Greeting';

     test('renders greeting message based on props', () => {
       render(<Greeting name="John" />);
       const element = screen.getByText('Hello, John!');
       expect(element).toBeInTheDocument();
     });
     ```

6. **Snapshot Testing**
   - **Question**: How would you implement a snapshot test for a React component?
   - **Answer**:
     ```javascript
     import { render } from '@testing-library/react';
     import MyComponent from './MyComponent';

     test('matches snapshot', () => {
       const { asFragment } = render(<MyComponent />);
       expect(asFragment()).toMatchSnapshot();
     });
     ```

7. **Conditional Rendering**
   - **Question**: How do you test a component that conditionally renders content based on its state?
   - **Answer**:
     ```javascript
     import { render, screen, fireEvent } from '@testing-library/react';
     import ToggleComponent from './ToggleComponent';

     test('toggles content on button click', () => {
       render(<ToggleComponent />);
       const button = screen.getByText('Show Details');
       fireEvent.click(button);
       const details = screen.getByText('Here are the details...');
       expect(details).toBeInTheDocument();
     });
     ```

8. **Testing Async Functions**
   - **Question**: How do you test a component that includes async operations, such as fetching data from an API?
   - **Answer**:
     ```javascript
     import { render, screen, waitFor } from '@testing-library/react';
     import MyComponent from './MyComponent';

     test('displays data after async operation', async () => {
       render(<MyComponent />);
       const dataElement = await waitFor(() => screen.getByText('Loaded Data'));
       expect(dataElement).toBeInTheDocument();
     });
     ```

These questions and answers will help you demonstrate practical knowledge of React Testing Library in an interview, showcasing your ability to write and understand tests for various scenarios in React projects.
