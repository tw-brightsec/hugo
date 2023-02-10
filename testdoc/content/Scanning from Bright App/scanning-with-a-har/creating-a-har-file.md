---
title: "Creating a .HAR file"
slug: "creating-a-har-file"
hidden: false
metadata: 
  description: "An HTTP Archive File (HAR file) is a recorded session of user interaction with an application. The HAR file keeps all the requests and responses between a user and the application you want to target for security scanning."
createdAt: "2021-08-31T14:17:51.106Z"
updatedAt: "2022-10-24T19:13:02.693Z"
---
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FHMpBQ7JkxHI%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DHMpBQ7JkxHI&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FHMpBQ7JkxHI%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/embed/HMpBQ7JkxHI\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture",
  "title": "How to create a HAR file for your application security scan",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/HMpBQ7JkxHI/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/embed/HMpBQ7JkxHI\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture"
}
[/block]




You can use various methods to get a capture of an HTTP session, for example, by using specialized tools, such as [Selenium](https://www.selenium.dev/) or [Fiddler debugging proxy](https://www.telerik.com/fiddler). Alternatively, you can explore network traffic and export it as a .HAR file in many web browsers, such as [Chrome](https://www.google.com/chrome/), [Internet Explorer/Edge](https://www.microsoft.com/en-us/download/internet-explorer.aspx), [Firefox](https://www.mozilla.org/en-US/firefox/new/), and [Safari](https://www.apple.com/safari/). 

> 📘 Note
> 
> The quality of the scan depends directly on the .HAR file quality. The more detailed the .HAR file, the larger the scan scope can be covered by Bright.

## Step-by-step guide

### Creating a .HAR file with Chrome

1. In the browser, open the DevTools panel by selecting the **Inspect** option from the context menu. 
2. Select the **Network** tab.
3. Make sure that the **Preserve log** and **Disable cache** checkboxes are selected. This will allow you to preserve logs between page refreshes and see the page updates. 
4. Leave the DevTools panel open and browse to your web application. All the application requests are then displayed and recorded in the DevTools panel.
5. Interact with the application in the same way as a normal user would. Remember to use all the resources (parts, options) of the application that you want to be covered by the Bright scan.
6. Once you complete the recording, right-click any of the requests in the DevTools panel and select the **Save all as HAR** option.
7. Save the file in your desired location so that you can select it when [defining a new scan](/docs/creating-a-new-scan).

### Creating a .HAR file with Firefox

1. In the browser, open the DevTools panel by selecting the **Inspect** option from the context menu. 
2. Select the **Network** tab.
3. Make sure that the **Preserve log** and **Disable cache** options are enabled. This will allow you to preserve logs between page refreshes and see the page updates. 
4. Leave the DevTools panel open and browse to your web application. All the application requests are then displayed and recorded in the DevTools panel.
5. Interact with the application in the same way as a normal user would. Remember to use all the resources (parts, options) of the application that you want to be covered by a Bright scan.
6. Once you complete the recording, right-click any of the requests in the DevTools panel and select the **Save All As HAR** option.
7. Save the file in your desired location so that you can select it when [defining a new scan](/docs/creating-a-new-scan).

### Creating a .HAR file with Safari

1. Enable the **Develop** menu item:  
   a) Open the Safari’s preferences. For that, press **Command+** or, form the menu, select **Safari > Preferences….**.  
   b) Select the **Advanced** tab, and then select **Show Develop menu item in menu bar**.  
   c) Close the **Preferences** window.
2. Open the Web Inspector. For that, press **Option**+**Command**+**i**, or from the menu, select **Develop** > **Show Web Inspector**.
3. Select the **Network** tab.
4. Make sure that the **Preserve log** and **Disable cache** options are enabled. This will allow you to preserve logs between page refreshes and see the page updates. 
5. Leave the DevTools panel open and browse to your web application. All the application requests are then displayed and recorded in the DevTools panel.
6. Interact with the application in the same way as a normal user would. Remember to use all the resources (parts, options) of the application that you want to be covered by a Bright scan. 
7. Once you complete the recording, right-click any of the requests and select **Export HAR**.
8. Save the file in your desired location so that you can select it when [defining a new scan](/docs/creating-a-new-scan).

### Creating a .HAR file with Fiddler debugging proxy

[Fiddler](https://www.telerik.com/fiddler) is a web debugger tool. It captures HTTP and HTTP(S) network traffic and allows you to examine each request. It also lets you export the requests and responses as a .HAR file.

1. Sign in to Fiddler. If you do not have a Fiddler account yet, create it first.
2. Browse to your web application and interact with it in the same way as a normal user would. Remember to use all the resources (parts, options) of the application that you want to be covered by a Bright scan. Fiddler automatically captures the requests.
3. Once you complete the interaction, right-click any of the requests and, from the context menu, select **Export** > **Selected Sessions**.
4. From the **Choose Format** dropdown menu,  select **HTTPArchive v1.2**.
5. Enter a filename and select **Save**.  
   Fiddler shows a popup message confirming the export has succeeded.

### Reviewing .HAR file content

Before using a .HAR file for a scan we recommend that you verify its formatting and structure using a .HAR file viewer.  
Specified .HAR file viewers can present the content of a .HAR file in a structured way. Several of them are available online. If you would prefer not to upload the .HAR file, you can use a tool installed locally on your machine. 

Tools recommended for reviewing .HAR files include:

- [HAR Viewer](http://www.softwareishard.com/har/viewer/) (online)
- [Google Admin Toolbox HAR Analyzer](https://toolbox.googleapps.com/apps/har_analyzer/) (online)
- [Fiddler](https://www.telerik.com/fiddler) (local)
- [Insomnia API Client](https://insomnia.rest/) (local)

These kinds of files (.HAR and .JSON files) can be also viewed and edited in any text editor, for example, [Visual Studio Code](https://code.visualstudio.com/).