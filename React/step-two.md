# Set up Authentication and Components

Go ahead and install the following packages from your terminal:

```code
npm install auth0-js react-router@3.0.0 jwt-decode axios
```

* **auth0-js** - For authentication 
* **react-router** - For routing within our app
* **jwt-decode** - For decoding the JSON Web Token in our app.
* **axios** - For making network requests.

Open up your `src` directory and create a `components` and `utils` folder. In the `utils` folder, create a file, **AuthService.js** and add the code [here](https://github.com/unicodeveloper/miniflix/blob/master/src/utils/AuthService.js) to it. [I explained how to handle the authentication in this tutorial](https://synd.co/2t8mdj5), so check it out to ensure you are on the right track.

We’ll create 4 components in the **components** folder. _Callback.js_, _Display.js_, _Nav.js_ and _Upload.js_

The **Callback** component basically stores our authentication credentials and redirects back to the upload route in our app.

The **Display** component will be dashboard for viewing all videos.

The **Nav** component will be the navigation that all pages in the app will share.

The **Upload** component will handle uploading of videos by registered users.

Add this piece of code below to **components/Callback.js**:

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



