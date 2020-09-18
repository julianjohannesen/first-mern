[back to index](/README.md) | [prev](/docs/7.md) | [next](/docs/.9md)

# Creating the Home and Log In Components

Next, create a new file in the src directory and name it Home.js. Don't forget to capitalize that "H".

Copy and paste the following code.

```js
// Home.js
// Import the useState and useEffect hooks
import React, {useState, useEffect} from 'react';

// Export the Home component
export default function Home() {
    // The useState hook functions similarly to setState in class 
    // components
    const [message, setMessage] = useState('Loading...');

    // useEffect calls a callback only after the component has 
    // rendered
    useEffect(() => {
        // The native fetch API will fetch data from '/api/home'. 
        // We'll create that endpoint later.
        fetch('/api/home')
            // When the promise resolves, we use the Response API's 
            // text() method parses the stream.
            .then((res) => res.text())
            // 
            .then((res) => setMessage((message) => res));
    }, [message]);

    return (
        <>
            <h1>You just fetched a message from our API!</h1>
            <h2>{message}</h2>
        </>
    );
}
```