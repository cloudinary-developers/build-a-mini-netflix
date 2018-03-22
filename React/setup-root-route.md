# Set up Root route

In order to see how your app works with these components, you need to set up some routes.

Open up your `src/index.js`. You'll define the routes here.

### Import components

Import `react`, `react-dom`, service worker and the display component.

```
import React from 'react';
import ReactDOM from 'react-dom';
import Display from './components/Display';
import registerServiceWorker from './registerServiceWorker';
import { Router, Route, browserHistory } from 'react-router';
```

### Set up the route

```code
const Root = () => {
  return (
    <div className="container">
      <Router history={browserHistory}>
        <Route path="/" component={Display}/>
      </Router>
    </div>
  )
}

ReactDOM.render(<Root />, document.getElementById('root'));
registerServiceWorker();
```

### Run your app

Run the `npm start` command in your terminal to start up the app.

```code
npm start
```

Your app should look like this now.

![App with navbar](http://res.cloudinary.com/unicodeveloper/image/upload/v1519851688/navbar.png)


