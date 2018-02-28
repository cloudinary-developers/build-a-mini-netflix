# Style Your App

A number of good css frameworks exist out there. However, you will make use of **bootstrap** in this code lab.

Bootstrap is an open source toolkit for developing with HTML, CSS, and JS. You can quickly prototype your ideas or build your entire app with the Sass variables and mixins, responsive grid system, extensive prebuilt components, and powerful plugins built on jQuery.

### Step 1

Open up `public/index.html` in your text editor. Pull in **bootstrap** and add it just after the favicon link.

```code
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />
```

### Step 2

Open up `src/App.css` and replace it with the styling snippet below:

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

Now, we have all the styling needed for your app.
