# 1] Basic Web Concepts
# 2] [Real-Time Scenario Usages for a React.js Developer](#realtime)

## 1] Basic Web Concepts
#### a. Page Rendering Cycle 
1. **Request:** Browser requests the webpage from the server.
2. **Response:** Server sends back HTML, CSS, and JavaScript files.
3. **Parsing:** Browser reads (parses) the HTML to build the DOM (Document Object Model).
4. **Styling:** CSS is applied to the DOM elements.
5. **Scripting:** JavaScript is executed, potentially modifying the DOM and CSS.
6. **Rendering:** The browser displays the final webpage to the user.
   - **Example:** Visiting a website like `example.com` starts this cycle.

#### b. HTTP/HTTPS/HTTP2 
- The Hypertext Transfer Protocol (HTTP) is the foundation of the www(World Wide Web), and is used to load webpages using hypertext links. HTTP is an application layer protocol designed to transfer information between networked devices and runs on top of other layers of the network protocol stack
- **HTTP:** Transfers data between a web browser and a server. 
  - **Example:** A request to `http://example.com`.
- **HTTPS:** Same as HTTP, but secure, encrypting data for safe transfer.
  - **Example:** A request to `https://example.com`.
- **HTTP2:** An improved version of HTTP, which loads web pages faster.
  - **Example:** Supports multiplexing (multiple requests in one connection).
-[Explaination](https://www.geeksforgeeks.org/explain-working-of-https/)

#### c. CORS 
- **CORS (Cross-Origin Resource Sharing):** its a permission given to web servers to specify who can access their resources.
  - **Example:** A webpage at `example.com` making a request to `api.otherdomain.com`.
  - [Explaination](#cors)

#### d. Local Storage/Session Storage
- **Local Storage:** Stores data with no expiration. 
  - **Example:** Saving a user's preferences that persist after closing the browser.
- **Session Storage:** Stores data for the duration of the page session. 
  - **Example:** Shopping cart data that is cleared when the tab is closed.
- [Explaination](https://www.geeksforgeeks.org/localstorage-and-sessionstorage-web-storage-apis/)

#### e. Web Vitals
- Metrics that help ensure a good user experience.
  - **LCP (Largest Contentful Paint):** Time until the largest content element is visible.
  - **FID (First Input Delay):** Time from user interaction to browser response.
  - **CLS (Cumulative Layout Shift):** Measures unexpected layout shifts.
  - **Example:** Tools like Google PageSpeed Insights provide these metrics.
  - [Explaination](https://www.freecodecamp.org/news/how-to-track-and-analyze-web-vitals-to-improve-seo/)

#### f. Cookie
- **Cookie:** Small pieces of data stored by the browser to remember information about the user.
  - **Example:** Storing a user's login state so they don’t need to log in again.
  Here's a comparison table between Cookies and Local Storage:

| **Aspect**               | **Cookies**                                             | **Local Storage**                                    |
|--------------------------|---------------------------------------------------------|------------------------------------------------------|
| **Data Size**            | ~4KB per cookie                                         | 5-10MB per origin                                    |
| **Expiration**           | Can be set to expire at a specific time or on session end | Persists until explicitly deleted                    |
| **Accessibility**        | Accessible on both client and server sides              | Accessible only on the client side                   |
| **Data Sent with Requests** | Sent with every HTTP request                          | Not sent with HTTP requests                          |
| **Use Case**             | Session management, tracking, storing small data        | Storing larger amounts of client-side data, preferences, caching |
| **Security**             | Can be secured with `HttpOnly` and `Secure` flags       | More vulnerable to XSS attacks; cannot be secured with flags |
| **Typical Use**          | Authentication tokens(logged in), session IDs, tracking info       | User preferences, settings(theme), cached data              |


#### g. JWT
- **JWT (JSON Web Token):** A secure way to transmit information between parties as a JSON object.
- The token is mainly composed of header, payload, signature: ``` [header].[payload].[signature] ```
  - **Example:** Token used to authenticate a user’s login session. https://www.codejava.net/images/articles/frameworks/springboot/jwt-auth/JWT_request_response.png

#### h. XHR
- **XHR (XMLHttpRequest):** A way to send HTTP requests from JavaScript to load data without refreshing the page.
  - **Example:** Fetching new comments on a blog post without reloading the page.

#### i. Micro Frontend
##### Micro Frontend:
- **Definition**: An architectural approach where a frontend application is split into smaller, independent, and self-contained units (micro frontends) that are developed, deployed, and managed by separate teams.
- **Use Case**: Ideal for large, complex applications where multiple teams need to work on different parts of the UI independently, allowing for greater scalability and modularity.

##### Macro Frontend:
- **Definition**: A traditional monolithic frontend architecture where the entire UI is built as a single cohesive application, typically managed by one team or closely coordinated teams.
- **Use Case**: Suitable for smaller applications or those requiring tight integration and uniformity across the entire UI, offering simpler management and development processes.

### Summary:
- **Micro Frontend**: Decentralized, modular, suitable for large-scale applications.
- **Macro Frontend**: Centralized, monolithic, suitable for smaller or less complex applications.
#### j. REST/GraphQL/Socket Connection
- **REST:** Uses standard HTTP methods (GET, POST, PUT, DELETE) for API communication.
  - **Example:** `GET /users` to fetch users.
- **GraphQL:** Allows clients to request specific data and get exactly what they ask for.
  - **Example:** `query { user(id: 1) { name } }` to get the user's name.
- **Socket Connection:** Real-time, two-way communication channel.
  - **Example:** Chat applications using WebSockets for instant messaging.

#### k. Browser Concepts
- **DOM (Document Object Model):** The structure of a webpage.
  - **Example:** HTML tags like `<div>` and `<p>` form the DOM.
- **CSSOM (CSS Object Model):** The structure of CSS styles.
  - **Example:** CSS rules like `body { color: black; }`.
- **Rendering Engine:** Converts HTML and CSS into pixels on the screen.
  - **Example:** Blink in Chrome, WebKit in Safari.

#### l. Debugging Application
- **console.log():** Prints messages to the browser console.
  - **Example:** `console.log('Hello, world!')` outputs "Hello, world!".
- **Breakpoints:** Pause code execution to inspect variables.
  - **Example:** Setting a breakpoint in Chrome DevTools to debug a function.
- **Dev Tools:** Browser tools to inspect and debug code.
  - **Example:** Using the Elements tab to modify HTML/CSS live.

#### m. Chrome Dev Tool Features
- **Elements:** Inspect and edit HTML/CSS.
  - **Example:** Changing the color of a heading in the Elements tab.
- **Console:** Run JavaScript and view messages.
  - **Example:** Testing small snippets of code.
- **Sources:** Debug JavaScript with breakpoints.
  - **Example:** Pausing execution to check variable values.
- **Network:** Monitor network requests.
  - **Example:** Checking if an API call was successful.
- **Performance:** Analyze how the webpage performs.
  - **Example:** Identifying slow-loading resources.
- **Application:** Inspect storage (cookies, local storage).
  - **Example:** Viewing and editing cookies.


### 2] Basic Web Concepts with Real-time Scenarios in React.js Projects <a id='realtime'></a>

#### a. Page Rendering Cycle
**Scenario:** When a user navigates to a React application (e.g., a dashboard), the browser requests the HTML file. React then takes over to render components, apply styles, and execute JavaScript, making the page interactive.

#### b. HTTP/HTTPS/HTTP2
**Scenario:** Your React app fetches data from an API using `fetch()` or `axios` over HTTPS to ensure data is encrypted. HTTP/2 can be leveraged for faster loading by allowing multiple requests in a single connection.

#### c. CORS
**Scenario:** Your React app requests data from an external API (e.g., `api.example.com`). The server must allow CORS requests from your domain (`yourapp.com`) to access the data.

#### d. Local Storage/Session Storage
**Scenario:** Storing user preferences (e.g., theme settings) in local storage so that preferences persist even after closing the browser. Using session storage to temporarily store form data during a session.

#### e. Web Vitals
**Scenario:** Using tools like Lighthouse to measure and optimize LCP, FID, and CLS to improve user experience in your React app by lazy-loading images, reducing JavaScript execution time, and minimizing layout shifts.

#### f. Cookie
**Scenario:** Storing JWT tokens in cookies for user authentication. When a user logs in, the server sends a token stored in a cookie to maintain the session.

#### g. JWT
**Scenario:** After a user logs into your React app, a JWT token is generated and stored (in local storage or cookies). This token is sent with every subsequent API request to authenticate the user.

#### h. XHR
**Scenario:** Using `axios` or `fetch()` in React components to make asynchronous HTTP requests to your backend API, loading data without refreshing the entire page.

#### i. Micro Frontend
**Scenario:** Developing a large application where different teams work on different parts, such as the user profile, shopping cart, and product listings, which are integrated into a single React app.

#### j. REST/GraphQL/Socket Connection
**Scenario:** 
- **REST:** Fetching user data using `GET /users` API.
- **GraphQL:** Fetching specific user data (name and email) using a GraphQL query.
- **Socket Connection:** Implementing a real-time chat feature using WebSockets.

#### k. Browser Concepts
**Scenario:** Manipulating the DOM using React hooks like `useEffect`, and understanding how CSSOM and DOM interact to apply styles dynamically.

#### l. Debugging Application
**Scenario:** Using `console.log()` to debug state changes in React, setting breakpoints in the Sources tab of Chrome DevTools to step through component lifecycle methods.

#### m. Chrome Dev Tool Features
**Scenario:** 
- **Elements:** Inspecting and modifying the structure of React components.
- **Console:** Running small JavaScript snippets to test component functions.
- **Sources:** Setting breakpoints to debug asynchronous operations in React.
- **Network:** Monitoring API calls to ensure data is being fetched correctly.
- **Performance:** Profiling the app to find performance bottlenecks.
- **Application:** Checking local storage, session storage, and cookies for correct data storage.


### Explanation of CORS (Cross-Origin Resource Sharing) <a id='cors' />

**CORS** stands for **Cross-Origin Resource Sharing**. It is a security feature implemented by browsers to restrict how resources on a web page can be requested from another domain. 

#### **How CORS Works:**
- **Same-Origin Policy:** By default, browsers enforce a security mechanism called the **Same-Origin Policy**. This means that a web page can only request resources from the same origin (same domain, protocol, and port).
  
- **CORS:** CORS allows servers to specify who can access their resources and how via HTTP headers. When a request is made to a server from a different origin (cross-origin), the server can include specific headers in its response to indicate that it allows access from the requesting origin.

#### **Key Concepts:**
- **Origin:** Combination of the protocol, domain, and port.
  - Example: `https://example.com:8080`
  
- **Preflight Request:** For non-simple requests (e.g., those with custom headers or methods like `PUT` or `DELETE`), the browser sends a preflight request (an `OPTIONS` request) to the server to check if the actual request is allowed.

- **CORS Headers:**
  - `Access-Control-Allow-Origin`: Specifies which origins are permitted to access the resource.
  - `Access-Control-Allow-Methods`: Specifies which HTTP methods are allowed (e.g., `GET`, `POST`).
  - `Access-Control-Allow-Headers`: Specifies which headers can be used in the actual request.
  - `Access-Control-Allow-Credentials`: Indicates whether credentials (cookies, HTTP authentication) can be sent with the request.

Here are two basic real-time scenarios involving CORS (Cross-Origin Resource Sharing) issues in a React application:

### Scenario 1: Fetching Public Data from an External API

**Scenario:**
You're building a React application that displays public data, like a list of movies from a third-party API such as `https://api.movies.com`. Your React app is running on `http://localhost:3000`.

**Problem:**
When you try to fetch data from `https://api.movies.com`, the browser blocks the request and displays a CORS error because `https://api.movies.com` is a different origin than `http://localhost:3000`.

**Solution:**
- **API Configuration:** The third-party API server needs to allow cross-origin requests by adding a `Access-Control-Allow-Origin: *` header, permitting any domain to access its resources.
- **Proxy Setup (Development Mode):** Alternatively, you can set up a proxy in your React app's `package.json`:
  ```json
  "proxy": "https://api.movies.com"
  ```
- **Example Code:**
  ```javascript
  fetch('/movies')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
  ```

### Scenario 2: Sending Data to an External API

**Scenario:**
You're developing a React application where users submit a form, and the data is sent to an external API hosted on `https://api.example.com`.

**Problem:**
When the form data is submitted, the browser blocks the request due to CORS issues since the API server doesn’t allow requests from `http://localhost:3000`.

**Solution:**
- **API Configuration:** The API server should include CORS headers such as `Access-Control-Allow-Origin: http://localhost:3000` to allow requests from your React app.
- **Frontend Configuration:** No additional setup is needed in React; just ensure that your fetch request is properly structured.
- **Example Code:**
  ```javascript
  fetch('https://api.example.com/submit', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ name: 'John', email: 'john@example.com' })
  })
  .then(response => response.json())
  .then(data => console.log('Success:', data))
  .catch(error => console.error('Error:', error));
  ```

These scenarios highlight the basics of how CORS can affect your React app when interacting with external APIs and the simple solutions to address these issues.
