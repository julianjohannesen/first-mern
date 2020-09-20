[back to index](/README.md) | [prev](/docs/7.md) | [next](/docs/.9md)

# Creating the Home and Log In Components

Next, create a new file in the src directory and name it Home.js. Don't forget to capitalize that "H".

Copy and paste the following code.

```js
// Home.js

// Import React and the useState and useEffect hooks
import React, {useState, useEffect} from 'react';

// Export the Home component
export default function Home() {
    // The useState hook functions similarly to setState in class components
    const [message, setMessage] = useState('Loading...');

    // useEffect calls a callback only after the component has rendered
    useEffect(() => {
        // The native fetch API will fetch data from '/api/home'. You'll create that endpoint later.
        fetch('/api/home')
            // When the promise resolves,use the Response API's text() method to parse the stream.
            .then((res) => res.text())
            // Now set the value of message to the parsed response
            .then((res) => setMessage((message) => res));
    // The 2nd argument is an array of variables that useEffect watches for changes. If the value of one of these variables changes as a side-effect of useEffect's callback, a subsequent re-render will not call useEffect again.
    }, [message]);

    return (
        <>
            <h1>You just fetched a message from the API!</h1>
            <h2>{message}</h2>
        </>
    );
}
```