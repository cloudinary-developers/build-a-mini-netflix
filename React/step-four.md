# Set up the Display Component

Add this piece of code to **components/Display.js**:

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

  





