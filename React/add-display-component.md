# Add Display Component

The **Display** component will be the dashboard for viewing all the uploaded videos on your app.

### Step 1

Create a _Display.js_ file in the `components` folder.

```code
touch Display.js
```

### Step 2

Add code to the _Display.js_ file so that it looks like this:

```code
import React, { Component } from 'react';
import { Link } from 'react-router';
import Nav from './Nav';
import { isLoggedIn } from '../utils/AuthService';
import axios from 'axios';

class Display extends Component {

  render() {

    return (
      <div>
        <Nav />
        <h3 className="text-center"> Latest Videos on Miniflix </h3>
        <hr/>

        <div className="col-sm-12">

        </div>
      </div>
    );
  }
}

export default Display;
```

  





