# Configure Auth Service

Let's configure the authentication service needed to authenticate users in your app. As mentioned in the previous steps, we are employing [Auth0](http://auth0.com). 

You'll need an [Auth0](https://auth0.com) account to manage authentication. [To sign up for a free account, you can follow this link](https://auth0.com/signup). Next, set up an Auth0 client app and API so Auth0 can interface with your app.

### Setting Up a Client App

1. Go to the [**Auth0 Dashboard**](https://manage.auth0.com/#/) and click the [create a new client](https://manage.auth0.com/#/clients/create) button.
2. Give your app a name and select **Single Page Web Applications**.
3. In the **Settings** for your new Auth0 client app, add `http://localhost:3000/callback` to the **Allowed Callback URLs**.

### Setup an API

Go to [**APIs**](https://manage.auth0.com/#/apis) in your Auth0 dashboard and click on the **Create API** button. Enter a name for the API. Set the **Identifier** to your API endpoint URL. In this example, this is `http://localhost:3001/api`. The **Signing Algorithm** should be `RS256`.


You're now ready to implement Auth0 authentication in your app.

> **Info** **Note:** As we want the best security available, we are going to rely on the [Auth0 login page](https://auth0.com/docs/hosted-pages/login). This method consists of redirecting users to a login page hosted by Auth0 that is easily customizable right from the [Dashboard](https://manage.auth0.com/).

Navigate to your `src` directory and create a `utils` folder. In the `utils` folder, create a file, **AuthService.js** and add this code to it.

```code
import decode from 'jwt-decode';
import { browserHistory } from 'react-router';
import auth0 from 'auth0-js';
const ID_TOKEN_KEY = 'id_token';
const ACCESS_TOKEN_KEY = 'access_token';

const CLIENT_ID = 'QHJHV3fmrMOxeJ1Vx2ETDkkClvv8qR7C';
const CLIENT_DOMAIN = 'kabiyesi.auth0.com';
const REDIRECT = 'https://localhost:3000/callback';
const SCOPE = 'full:access';
const AUDIENCE = 'http://localhost:3001/api';

var auth = new auth0.WebAuth({
  clientID: CLIENT_ID,
  domain: CLIENT_DOMAIN
});

export function login() {
  auth.authorize({
    responseType: 'token id_token',
    redirectUri: REDIRECT,
    audience: AUDIENCE,
    scope: SCOPE
  });
}

export function logout() {
  clearIdToken();
  clearAccessToken();
  browserHistory.push('/');
}

export function requireAuth(nextState, replace) {
  if (!isLoggedIn()) {
    replace({pathname: '/'});
  }
}

export function getIdToken() {
  return localStorage.getItem(ID_TOKEN_KEY);
}

export function getAccessToken() {
  return localStorage.getItem(ACCESS_TOKEN_KEY);
}

function clearIdToken() {
  localStorage.removeItem(ID_TOKEN_KEY);
}

function clearAccessToken() {
  localStorage.removeItem(ACCESS_TOKEN_KEY);
}

// Helper function that will allow us to extract the access_token and id_token
function getParameterByName(name) {
  let match = RegExp('[#&]' + name + '=([^&]*)').exec(window.location.hash);
  return match && decodeURIComponent(match[1].replace(/\+/g, ' '));
}

// Get and store access_token in local storage
export function setAccessToken() {
  let accessToken = getParameterByName('access_token');
  localStorage.setItem(ACCESS_TOKEN_KEY, accessToken);
}

// Get and store id_token in local storage
export function setIdToken() {
  let idToken = getParameterByName('id_token');
  localStorage.setItem(ID_TOKEN_KEY, idToken);
}

export function isLoggedIn() {
  const idToken = getIdToken();
  return !!idToken && !isTokenExpired(idToken);
}

function getTokenExpirationDate(encodedToken) {
  const token = decode(encodedToken);
  if (!token.exp) { return null; }

  const date = new Date(0);
  date.setUTCSeconds(token.exp);

  return date;
}

function isTokenExpired(token) {
  const expirationDate = getTokenExpirationDate(token);
  return expirationDate < new Date();
}
```

In the code above, we invoked the `auth0` library. And we have methods for storing the tokens returned from Auth0, decoding them and getting the expiry date.

> **Danger** **Note:** Replace the `CLIENT_ID` and `CLIENT_DOMAIN` with the values from your Auth0 dashboard.







