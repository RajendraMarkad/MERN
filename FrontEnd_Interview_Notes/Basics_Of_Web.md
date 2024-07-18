# Basic Web Concepts
# [Real-Time Scenario Usages for a React.js Developer](#realtime)

## Basic Web Concepts
#### a. Page Rendering Cycle
1. **Request:** Browser requests the webpage from the server.
2. **Response:** Server sends back HTML, CSS, and JavaScript files.
3. **Parsing:** Browser reads (parses) the HTML to build the DOM (Document Object Model).
4. **Styling:** CSS is applied to the DOM elements.
5. **Scripting:** JavaScript is executed, potentially modifying the DOM and CSS.
6. **Rendering:** The browser displays the final webpage to the user.
   - **Example:** Visiting a website like `example.com` starts this cycle.

#### b. HTTP/HTTPS/HTTP2 
- The Hypertext Transfer Protocol (HTTP) is the foundation of the World Wide Web, and is used to load webpages using hypertext links. HTTP is an application layer protocol designed to transfer information between networked devices and runs on top of other layers of the network protocol stack
- **HTTP:** Transfers data between a web browser and a server. 
  - **Example:** A request to `http://example.com`.
- **HTTPS:** Same as HTTP, but secure, encrypting data for safe transfer.
  - **Example:** A request to `https://example.com`.
- **HTTP2:** An improved version of HTTP, which loads web pages faster.
  - **Example:** Supports multiplexing (multiple requests in one connection).

#### c. CORS
- **CORS (Cross-Origin Resource Sharing):** Allows web servers to specify who can access their resources.
  - **Example:** A webpage at `example.com` making a request to `api.otherdomain.com`.

#### d. Local Storage/Session Storage
- **Local Storage:** Stores data with no expiration. 
  - **Example:** Saving a user's preferences that persist after closing the browser.
- **Session Storage:** Stores data for the duration of the page session. 
  - **Example:** Shopping cart data that is cleared when the tab is closed.

#### e. Web Vitals
- Metrics that help ensure a good user experience.
  - **LCP (Largest Contentful Paint):** Time until the largest content element is visible.
  - **FID (First Input Delay):** Time from user interaction to browser response.
  - **CLS (Cumulative Layout Shift):** Measures unexpected layout shifts.
  - **Example:** Tools like Google PageSpeed Insights provide these metrics.

#### f. Cookie
- **Cookie:** Small pieces of data stored by the browser to remember information about the user.
  - **Example:** Storing a user's login state so they don’t need to log in again.

#### g. JWT
- **JWT (JSON Web Token):** A secure way to transmit information between parties as a JSON object.
  - **Example:** Token used to authenticate a user’s login session.

#### h. XHR
- **XHR (XMLHttpRequest):** A way to send HTTP requests from JavaScript to load data without refreshing the page.
  - **Example:** Fetching new comments on a blog post without reloading the page.

#### i. Micro Frontend
- **Micro Frontend:** An approach to building web applications where a single app is split into smaller, independent parts.
  - **Example:** An e-commerce site with separate components for the shopping cart, product listing, and user profile.

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


### Basic Web Concepts with Real-time Scenarios in React.js Projects <a id='realtime'></a>

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
