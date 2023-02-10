---
title: "Scanning with a .HAR file"
slug: "scanning-with-a-har"
hidden: false
metadata: 
  description: "You can use a pre-recorded session of a user interaction with the target application (HAR file)  when running a scan.  Using the data contained in the HAR file, NeuraLegion defines the attack surface and ensures complete coverage of the scan scope.  To run a scan using a HAR file, you need to upload the file in the Recording Session section."
createdAt: "2021-08-31T14:10:03.519Z"
updatedAt: "2022-12-08T13:13:34.934Z"
---
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F7sEiHLeeMHI&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D7sEiHLeeMHI&image=http%3A%2F%2Fi.ytimg.com%2Fvi%2F7sEiHLeeMHI%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/embed/7sEiHLeeMHI\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture",
  "title": "YouTube",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "http://i.ytimg.com/vi/7sEiHLeeMHI/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/embed/7sEiHLeeMHI\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture"
}
[/block]




An HTTP Archive File (.HAR file) is a recorded session of user interaction with an application. The .HAR file keeps all the HTTP requests and responses between the web client and web application. 

You can use a pre-recorded .HAR file when running a security scan.  Using the data contained in the .HAR file, Bright defines the attack surface and ensures complete coverage of the scan scope. To run a scan with a .HAR file, in the **Recording Session** section, you need either to upload a file from a disk or use a file previously uploaded to the Bright storage.

![](https://files.readme.io/0b2c135-Screenshot_at_Dec_08_12-40-39.png)



You can create a .HAR file using either specialized tools or common web browsers. See [Creating a HAR File](/docs/creating-a-har-file) to learn how to record an interaction session and review the generated .HAR file.  

> 🚧 Important
> 
> **Authentication coverage** - To ensure complete coverage of the scan, you should configure an authentication object so that the Bright engine can reach the authenticated parts of the target application. See [Managing Your Authentications](/docs/creating-an-authentication-object-in-nexploit) for detailed information.
> 
> **HAR upload limits** - A single .HAR file is limited to 500 Mb, but you can upload multiple files for larger targets.

| **Pros**                                                                                                                                                                                                                                                                                        | **Cons**                                                                                                                                                                                                     |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Deeper coverage**. You can enable Bright to switch between the microservers during scanning if the relative data is recorded in the HAR file. Bright uses all the recorded data to define the attack surface. Therefore, it can reach every part of your application covered by the HAR file. | **Less automation**. You have to create a HAR file on every new part of the application you want to scan. It may be a problem for large development teams where the engagement process is quite complicated. |
| **Scope control**. The scan covers exactly the same scope of the target as recorded in the HAR file (determined by a user). Therefore, Bright can run a scan only for a new part, instead of scanning the whole application on every build.                                                     |                                                                                                                                                                                                              |

> 👍 Tip
> 
> You can combine full automation with complete coverage by applying both the **Crawler** and **Recorded (HAR)** discovery types for a scan.