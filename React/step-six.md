# Set up your Routes

Lastly, open up **index.js **and add the code below to set up your routes.

```code
import React from 'react';
import ReactDOM from 'react-dom';
import Upload from './components/Upload';
import Display from './components/Display';
import Callback from './components/Callback';
import registerServiceWorker from './registerServiceWorker';
import { Router, Route, browserHistory } from 'react-router';
import { requireAuth } from './utils/AuthService';

const Root = () => {
  return (
    <div className="container">
      <Router history={browserHistory}>
        <Route path="/" component={Display}/>
        <Route path="/upload" component={Upload} onEnter={requireAuth} />
        <Route path="/callback" component={Callback} />
      </Router>
    </div>
  )
}

ReactDOM.render(<Root />, document.getElementById('root'));
registerServiceWorker();
```

With the routes all set up, we can now run our app with `npm start`, you should have views like this:

![](https://cdn.scotch.io/21401/PK6PHHJIRl7WQdtQxnEr_image11.png)

![](https://cdn.scotch.io/21401/GHn86HhjQTium2oID9AC_image14.png)

