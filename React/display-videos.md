# Display Videos

You need a dashboard to display all the videos uploaded for users to see at a glance. Here, the [Cloudinary’s react component](https://synd.co/2t8gfP9) will come in handy.


### Step 1

Install the `cloudinary-react` package via the command line

```code
npm install cloudinary-react
```


### Step 2

Open up `components/Display.js` and modify the code to be this below:

```code
import React, { Component } from 'react';
import { Link } from 'react-router';
import Nav from './Nav';
import { isLoggedIn } from '../utils/AuthService';
import { CloudinaryContext, Transformation, Video } from 'cloudinary-react';
import axios from 'axios';

class Display extends Component {

  state = { videos: [] };

  getVideos() {
    axios.get('http://res.cloudinary.com/<cloud-name>/video/list/miniflix.json')
          .then(res => {
            console.log(res.data.resources);
            this.setState({ videos: res.data.resources});
    });
  }

  componentDidMount() {
    this.getVideos();
  }

  render() {

    const { videos }  = this.state;

    return (
      <div>
        <Nav />
        <h3 className="text-center"> Latest Videos on Miniflix </h3>
        <hr/>

        <div className="col-sm-12">
          <CloudinaryContext cloudName="<cloud-name>">
            { videos.map((data, index) => (
                <div className="col-sm-4" key={index}>
                  <div className="embed-responsive embed-responsive-4by3">
                    <Video publicId={data.public_id} width="300" height="300" controls></Video>
                  </div>
                  <div> Created at {data.created_at} </div>

                </div>
              ))
            }
          </CloudinaryContext>
        </div>
      </div>
    );
  }
}

export default Display;
```

> **Info** **Note:** Replace `<cloud-name>` in the code above with your cloud name from [Cloudinary dashboard.](https://cloudinary.com/console).


In the **getVideos **code above, we take advantage of a very slick Cloudinary trick that helps grab all videos with a particular tag, when using just one tag. Check it out again:

```code
http://res.cloudinary.com/<cloud-name>/video/list/miniflix.json
```
> **Info** **Note:** By default, a new account has the resource lists disabled. Enable it in the [security settings page.](https://cloudinary.com/console/settings/security)

So we if had a tag like `vimeo`, our url will end up with `.../vimeo.json.` So in the code below, we got all the videos and stored in the videos state like so:

```code
axios.get('http://res.cloudinary.com/<cloud-name>/video/list/miniflix.json')
          .then(res => {
            console.log(res.data.resources);
            this.setState({ videos: res.data.resources});
    });
```

### Cloudinary React SDK

The Cloudinary React SDK has 4 major components: **Image**, **Video**, **Transformation** and **CloudinaryContext**. We are interested in the **Video** and **CloudinaryContext** for now.  [Christian](https://twitter.com/codebeast) explained [how these components work here](https://synd.co/2tsRQ6f).

In the render method, we simply just looped through the _videos_ state and passed the _public_id_ of each video into the **Cloudinary Video** component. The Video component does the job of resolving the _public_id_ from Cloudinary, getting the video url, and displaying it using HTML5 video on the webpage. An added advantage is this: Cloudinary automatically determines the best video type for your browser. 

Furthermore, it allows the user have the best experience possible by choosing the best from the range of available video types and resolutions.

### Run your app

You should see the list of all videos. It should be similar to this:

![List of Videos on Miniflix](http://res.cloudinary.com/unicodeveloper/image/upload/v1521750255/allvideossnapshot.png)

You can also manipulate your videos on the fly, with the help of Cloudinary via the **Transformation** component.

