# Add Callback Component

React apps are made up of components. Create a **components** folder in your `src` directory.

You'll need four components in your app. The first component to define is the **Callback** component.

### Step 1

Create a _Callback.js_ file in the `components` folder.

```code
touch Callback.js
```

The **Callback** component basically stores our authentication credentials and redirects back to the upload route in our app.

### Step 2

Add code to the _Callback.js_ file so that it looks like this:

```code
import { Component } from 'react';
import { setIdToken, setAccessToken } from '../utils/AuthService';

class Callback extends Component {

  componentDidMount() {
    setAccessToken();
    setIdToken();
    window.location.href = "/";
  }

  render() {
    return null;
  }
}

export default Callback;
```

The `componentDidMount()` function is a React lifecycle hook that is invoked immediately after a component is mounted. Other lifecycle hooks are [well explained in this article](https://reactjs.org/docs/react-component.html)

