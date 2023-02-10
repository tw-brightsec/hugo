---
title: "Configuring Recorded Browser-Based Form Authentication (Internal Copy)"
slug: "configuring-recorded-browser-based-form-authentication-internal-copy"
hidden: false
createdAt: "2022-08-11T08:57:24.763Z"
updatedAt: "2022-09-14T09:20:04.360Z"
---
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FbpEE7Q5jJhk%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DbpEE7Q5jJhk&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FbpEE7Q5jJhk%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=bpEE7Q5jJhk&feature=youtu.be",
  "title": "Configuring Recorded Browser-Based Form Authentication",
  "favicon": "https://www.youtube.com/s/desktop/1c192ebe/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/bpEE7Q5jJhk/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=bpEE7Q5jJhk&feature=youtu.be"
}
[/block]




- **Recorded browser-based form authentication** is a quick and visual way of creating authentication flows. It allows uploading an authentication flow which was prerecorded with the Chrome recorder and using it as authentication with Bright.

## Recording an authentication flow

To record a session using Google Chrome Recorder, follow the steps below.

1. In the Chrome browser, open the target URL in a separate tab.
2. Open DevTools.

> 📘 Note
> 
> **Opening DevTools**
> 
> - In Chrome's main menu: Click the three dots menu (**Customize and control Google Chrome**) and then select **More Tools** **Developer Tools**.
>   - On Windows: Press **Ctrl+Shift+J**.
>   - On Mac: **Ctrl+Option+J**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a47eaf9-1.png",
        "1.png",
        761
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Click the three dots menu (**More options**) and then select **More tools** > **Recorder**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dcbda00-2.png",
        "2.png",
        581
      ],
      "sizing": "smart"
    }
  ]
}
[/block]



3. Click the **Start New Recording** button. The browser will display the **Start a New Recording** pane. 
4. In the **Recording Name** field, enter a name for your recording. 
5. At the bottom of the page, click the **Start a New Recording** button.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/10f9ebe-3.png",
        "3.png",
        822
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. Record your login session and click the **End Recording** button to stop the recording.

> 📘 Note
> 
> To add post-login check:
> 
> 1. Select the three dots against the last step and then click **Add Step After**.  
> 2. Expand the new step.  
> 3. Click a small icon against selectors and then select an element in the page to update selector (see screenshot below).

![](https://files.readme.io/75599b5-4.png "4.png")



![](https://files.readme.io/c26df34-5.png "5.png")



6. Log out.
7. At the top of the developer tools pane, click the **Replay** button. If the record cannot be replayed, repeat steps 4-5 until the record is replayed successfully.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b7483d4-6.png",
        "6.png",
        820
      ],
      "sizing": "80"
    }
  ]
}
[/block]



8. Select **Export as a JSON file** and save the record on your PC.

> 📘 
> 
> If you use the Incognito mode in Chrome to make the recording and have more than 1 Incognito windows running, clicking the logout is not enough to clean the credentials. Additionally, you will need to close all the Incognito windows.

> 📘 Note
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via the Repeater.

## Uploading recorded file to Bright

> 📘 Note
> 
> This topic describes only how to fill in fields specific for recorded browser-based form authentication (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/configuring-authentication).

1. From the **Authentication type** drop-down list, select **Recorded Browser-Based Form Authentication**. The  **Upload Recorded File (Json)** link will appear at the bottom of the dialog window. 

2. Click the **Upload Recorded File (Json)** link and upload the recording.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2b73a71-7.png",
        "7.png",
        1258
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 📘 Note
> 
> Bright allows testing a scan before saving it. For details, see the [Testing Authentication](https://docs.brightsec.com/docs/configuring-authentication#testing-authentication).