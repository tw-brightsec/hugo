---
title: "Scanning with a Crawler"
slug: "crawler"
hidden: false
metadata: 
  description: "NeuraLegion can crawl your web application to define the attack surface. This option does not require any details that might get you tangled."
createdAt: "2021-08-31T12:22:07.030Z"
updatedAt: "2022-12-08T08:33:02.685Z"
---
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FvCA0DwjLXyM%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DvCA0DwjLXyM&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FvCA0DwjLXyM%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/embed/vCA0DwjLXyM\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture\"%20allowfullscreen",
  "title": "How to run a security scan using a crawler",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/vCA0DwjLXyM/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/embed/vCA0DwjLXyM\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture\"%20allowfullscreen"
}
[/block]




Bright can crawl your web application to define the attack surface. This option does not require any details that might get you tangled. To run a security scan using a crawler, you simply need to specify the target URL in the **URL** field. 

You can scan either the whole application or its parts. To scan only specific parts of your application, click **+ Add target** to add multiple URLs. In this case, only the specified sections of the application and everything downstream from them will be scanned.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1544960-Screenshot_at_Dec_08_12-31-04.png",
        null,
        null
      ]
    }
  ]
}
[/block]



> 🚧 Important
> 
> To ensure complete coverage of the scan, you should configure an authentication object so that the crawler can reach the authenticated parts of the target application. See [Managing Your Authentications](/docs/creating-an-authentication-object-in-nexploit) for detailed information.

| **Pros**                                                                                                                             | **Cons**                                                                                                                                                                                                                                         |
| :----------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Simple usage**. You simply need to specify the target host. The crawler will define the attack surface (scan scope) automatically. | **Less coverage**. The crawler cannot get through some user-specific forms or provide the required input. It means that the attack surface may be defined incompletely, and Bright will not cover such parts of the application during scanning. |
| **Full automation**. By default, the crawler automatically covers all the application parts that it can reach.                       | **Limited coverage level**. The crawler is applicable only to web pages of the target application and the microservices connected to the application directly. Crawling between the microservices is disabled.                                   |

> 👍 Tip
> 
> You can combine full automation with complete coverage by applying both the **Crawler** and **Recorded (.HAR)** discovery types for a scan.

# Setting coverage exclusions

For setting coverage exclusions when scanning with a crawler, see [Defining Scan Targets](https://docs.brightsec.com/docs/advanced-mode#defining-scan-targets).