# Add Upload Component

The **Upload** component will handle uploading of videos by registered users.

### Step 1

Create a _Upload.js_ file in the `components` folder.

```code
touch Upload.js
```

### Step 2

Add code to the _Upload.js_ file so that it looks like this:

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

Your app will live-reload in the browser. You should have something like this now:





