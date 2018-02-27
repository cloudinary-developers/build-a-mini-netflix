# Set up the Upload Component

Add this piece of code to **components/Upload.js:**

```code
import React, { Component } from 'react';
import { Link } from 'react-router';
import Nav from './Nav';

class Upload extends Component {

  render() {

    return (
      <div>
        <Nav />
        <h3 className="text-center">Upload Your 20-second Video in a Jiffy</h3>
        <hr/>

        <div className="col-sm-12">
          <div className="jumbotron text-center">
            <button className="btn btn-lg btn-info"> Upload Video</button>
          </div>
        </div>
      </div>
    );
  }
}

export default Upload;
```

