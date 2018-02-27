# Share on Twitter

Go ahead and install the _react twitter widget_ component:

```code
npm install react-twitter-widgets
```

In the `components/Display.js` file, import the component at the top:

```code
import { Share } from 'react-twitter-widgets';
...
...
```

Now, add this piece of code just after the div that shows the time the video was created.

```code
...
...
<Share url={`http://res.cloudinary.com/unicodeveloper/video/upload/${data.public_id}.mp4`} />
```

Check your app again. It should be similar to this:

![](https://cdn.scotch.io/21401/ffOV5jKXRRiYc3Y1Rjtz_image10.png)

Now, try to tweet.

![](https://cdn.scotch.io/21401/I3T6C9JRtGY1livEodGQ_image13-2.png)

Simple! It’s really not that hard. The source code for this tutorial is on [GitHub](https://synd.co/2rmm0aR).

