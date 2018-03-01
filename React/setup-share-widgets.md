# Share on Twitter

Go ahead and install the _react twitter widgets_ package via the command line

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

![Latest videos on Miniflix](http://res.cloudinary.com/unicodeveloper/image/upload/v1519925599/labs-miniflix/4En2QtTRXW5YVkoTDF90_image9.png)

Now, try to tweet.
       
![Share tweets](http://res.cloudinary.com/unicodeveloper/image/upload/v1519925594/labs-miniflix/I3T6C9JRtGY1livEodGQ_image13-2.png)

