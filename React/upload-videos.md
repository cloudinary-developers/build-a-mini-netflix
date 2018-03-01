# Upload Videos

You need a storage space for the videos that users will upload. 

**Cloudinary** provides cloud storage and an awesome upload widget that allows users to upload videos or any type of file from their local computer, facebook, dropbox, Google Drive and Instagram.

<p data-height="513" data-theme-id="0" data-slug-hash="ddaNvZ" data-default-tab="js,result" data-user="Cloudinary" data-embed-version="2" data-pen-title="Upload Widget" class="codepen">See the Pen <a href="https://codepen.io/team/Cloudinary/pen/ddaNvZ/">Upload Widget</a> by Cloudinary (<a href="https://codepen.io/Cloudinary">@Cloudinary</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

> **Note:** Head over to [Cloudinary.com](https://synd.co/2sypmf2) and create an account for free.

### Integrate Cloudinary Upload Widget

Open up your `public/index.html` file and include Cloudinary's widget script.


```code
 <script src="//widget.cloudinary.com/global/all.js" type="text/javascript"></script>
```

### Update Upload Component

Head over to `src/components/Upload.js`. You'll modify the code to have an `uploadWidget` function.


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
        sources: ['local', 'url', 'facebook', 'image_search']
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

The upload widget takes in [several parameters](https://cloudinary.com/documentation/upload_widget). However, we used the following: `cloud_name`, `upload_preset`, `sources` and `tags` in this code lab. 

In the code above, we added a third argument, **tags**. Cloudinary provides this for automatic video tagging. Every video that is uploaded to this app will be automatically tagged, _**miniflix**_. In addition, you can provide as many tags as you want. This feature is very useful when you want to search for videos too!

In the **uploadWidget** function, we called the **cloudinary.openUploadWidget** function and attached it to the **“Upload Video”** button. When the user clicks the button, it opens the widget.

The `sources` parameter accepts an array of string values defining the tabs to add to the upload widget, where each source defines a new upload tab within the widget. 

> **Note:** Replace the `cloud_name` & `upload_preset` values with your credentials from the [Cloudinary dashboard](https://synd.co/2tteZFP).

Head over to the `/upload` route and try uploading a video.

![](https://cdn.scotch.io/21401/hdXhoRncSRaEmKGSAPd7_image6.png)Upload Widget

![](https://cdn.scotch.io/21401/ty6p6MF6SuE7KYpVcej5_image12.png)Uploading the video...

It uploads the video straight to Cloudinary and returns a response object about the recently uploaded video that contains so many parameters such as the unique **publicid**, **secureurl**, **url**, **originalfilename**, **thumbnailurl**, **createdate**, **duration** and [so many others](https://synd.co/2s7tfX3).



