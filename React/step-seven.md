# Upload Videos

We need a storage space for the videos our users will upload. **Cloudinary** is a cloud-based service that provides an end-to-end image and video management solution including uploads, storage, administration, manipulation and delivery. Head over to [Cloudinary.com](https://synd.co/2sypmf2) and create an account for free.

Let’s make use of [Cloudinary’s Upload Widget](https://synd.co/2rBWQEz). This widget allows you to upload videos or any type of file from your local computer, facebook, dropbox and Google Photos. And the integration is seamless.

Go ahead and reference the cloudinary widget script in your index.html:

```code
 <script src="//widget.cloudinary.com/global/all.js" type="text/javascript"></script>
```

Now in `Upload.js`, modify the code to look like this:

```code
import React, { Component } from 'react';
import { Link } from 'react-router';
import Nav from './Nav';

class Upload extends Component {

  uploadWidget = () => {
    window.cloudinary.openUploadWidget(
      { cloud_name: 'cloud_name',
        upload_preset: '<unsigned-preset>',
        tags: ['miniflix'],
        sources: ['local', 'url', 'google_photos', 'facebook', 'image_search']
      },
      function(error, result) {
          console.log("This is the result of the last upload", result);
      });
  }

  render() {
    return (
      <div>
        <Nav />
        <h3 className="text-center">Upload Your 20-second Video in a Jiffy</h3>
        <hr/>

        <div className="col-sm-12">
          <div className="jumbotron text-center">
            <button onClick={this.uploadWidget} className="btn btn-lg btn-info"> Upload Video</button>
          </div>
        </div>
      </div>
    );
  }
}

export default Upload;
```



In the code above, we added a third argument, **tags**. Cloudinary provides this for automatic video tagging. Every video that is uploaded to this app will be automatically tagged, _**miniflix**_. In addition, you can provide as many tags as you want. This feature is very useful when you want to search for videos too!

In the **uploadWidget** function, we called the **cloudinary.openUploadWidget** function and attached it to the **“Upload Video”** button. When the user clicks the button, it opens the widget. Replace the `cloud_name` & `upload_preset` values with your credentials from [Cloudinary dashboard](https://synd.co/2tteZFP).

Sign in to your app, head over to the `/upload` route and try uploading a video.

![](https://cdn.scotch.io/21401/hdXhoRncSRaEmKGSAPd7_image6.png)Upload Widget

![](https://cdn.scotch.io/21401/ty6p6MF6SuE7KYpVcej5_image12.png)Uploading the video...

It uploads the video straight to Cloudinary and returns a response object about the recently uploaded video that contains so many parameters such as the unique **publicid**, **secureurl**, **url**, **originalfilename**, **thumbnailurl**, **createdate**, **duration** and [so many others](https://synd.co/2s7tfX3).

