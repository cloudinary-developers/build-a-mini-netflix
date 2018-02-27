# Set up the Navigation Component

Add this piece of code to **components/Nav.js:**

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

In the **Nav** component, you must have observed that we imported a `css` file. 

Open the _App.css_ file and add the code below to it:

```code
.navbar-right { margin-right: 0px !important}
.log {
  margin: 5px 20px 0 0;
}
.videos {
  border: 1px solid red;
  height:400px;
}
```

