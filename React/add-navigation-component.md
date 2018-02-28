# Add Navigation Component

The Navigation component will be responsible for the navigation section that all pages in the app will share.

### Step 1

Create a _Nav.js_ file in the `components` folder.

```code
touch Nav.js
```

### Step 2

Add code to the _Nav.js_ file so that it looks like this:

```code
import React, { Component } from 'react';
import { Link } from 'react-router';
import { login, logout, isLoggedIn } from '../utils/AuthService';
import '../App.css';

class Nav extends Component {

  render() {
    return (
      <nav className="navbar navbar-default">
        <div className="navbar-header">
          <Link className="navbar-brand" to="/">Miniflix</Link>
        </div>
        <ul className="nav navbar-nav">
          <li>
            <Link to="/">All Videos</Link>
          </li>
          <li>
            {
             ( isLoggedIn() ) ? <Link to="/upload">Upload Videos</Link> :  ''
            }
          </li>
        </ul>
        <ul className="nav navbar-nav navbar-right">
          <li>
           {
             (isLoggedIn()) ? ( <button className="btn btn-danger log" onClick={() => logout()}>Log out </button> ) : ( <button className="btn btn-info log" onClick={() => login()}>Log In</button> )
           }
          </li>
        </ul>
      </nav>
    );
  }
}
export default Nav;
```

In the **Nav** component, you must have observed that a `css` file was imported. It's to give the navbar some custom styling effects. Furthermore, the `<nav>` component from Bootstrap was used to give the app a basic and functional navbar.

The `isLoggedIn()` function is from the `AuthService`. It basically checks the user's authentication status. If the user is logged in, the `Log out` button is displayed else the `Log In` button is displayed to the user.

In order to see this components work visually, you need to set up routes to render them in the browser.






