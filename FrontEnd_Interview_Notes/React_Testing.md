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

This cheat sheet should help you quickly recall the key aspects of testing in React and best practices during your interview preparation.
