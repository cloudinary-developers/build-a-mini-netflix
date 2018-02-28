# Set up Upload route

In order to see how your app works, you need to set up the upload route.

Open up your `src/index.js` where the routes exist.

### Import Upload component

Import the recently created Upload component.

```
...
import Upload from './components/Upload';
...
```

### Set up the Upload route

Add the `/upload` route.

```code
<Route path="/upload" component={Upload} />
```

Your routes should look like the code below.

```code
...
...
const Root = () => {
  return (
    <div className="container">
      <Router history={browserHistory}>
        <Route path="/" component={Display}/>
        <Route path="/upload" component={Upload} />
      </Router>
    </div>
  )
}
```

### Run your app

Your app should live-reload. In your browser, enter the upload route, `http://localhost:3000/upload`.


Your app should look like this now.

![App with upload route](http://res.cloudinary.com/unicodeveloper/image/upload/v1519852542/upload.png)


