<!-- @format -->

[back to index](/README.md) | [prev](/docs/4.md) | [next](/docs/6.md)

# Step 5 - React Routing Part 1 - Adding Routes

The next thing you need to do is to add a couple of simple routes to the React front-end. Specifically, routes to a home page and log in page. 

Don’t worry if you don’t know much about client-side routing. All you need to know right now is that in a React application typing a URL in the address bar or navigating to a page does not always require that the browser send an HTTP request to a server and then wait for a response from the server containing the requested content. Instead, React applications request content up front or in the background, and emulate server-side routing using the browser's History API. From a user's perspective, client-side routing is indistinguishable from server-side routing, except for the fact that client-side routing is often much, much faster.

First, you'll install React Router, a popular routing library for React.

```
 npm i react-router-dom
```

Now, open src/App.js and replace the existing code with the code below.

```js
// App.js

import React from "react";

// Import the methods that you need from 'react-router-dom'
import {BrowserRouter as Router, Switch, Route, Link} from 'react-router-dom';

function App() {
   return (
    // The Router component wraps all of the other components
    <Router>
        <div className="App">
			{/* The Link component enables a user to navigate to a page without triggering a page refresh.  It also ensures that the browser's back and forward buttons will work, by using history.push() to push a new entry to the history stack. */}
            <Link to="/">Home</Link>
            <Link to="/login">Log In</Link>
			{/* The Switch component will only render the first Route that matches the path the user wants to navigate to. Without it, clicking on the Home link above would render both the Home component and the LogIn component on the same page. */}
            <Switch>
				{/* When a user attempts to navigate to a particular route, Route will determine which React component to render. Route takes a path attribute whose value is the route in question. Route can also take a component attribute to indicate what component to render. In this particular case, the component is Route's child node. */}
                <Route exact path="/">
                    <Home />
                </Route>
                <Route exact path="/log-in">
                    <LogIn />
                </Route>
            </Switch>
        </div>
    </Router>
   );
}

// A simple Home component
function Home() {
   return <h2>Welcome to the Home Page!</h2>;
}
// A simple LogIn component
function LogIn() {
   return <h2>You're on the Log In Page!</h2>;
}

export default App;
``` 

Now double check that the front-end is still functioning. Refresh your browser and use the new nav links to visit the Home page and the Log In page. The URL in the address bar and the text on the page should change.
