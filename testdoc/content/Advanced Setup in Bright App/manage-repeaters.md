---
title: "Managing Repeaters"
slug: "manage-repeaters"
hidden: false
metadata: 
  description: "NeuraLegion’s Repeater is a local agent that provides a secure connection between NeuraLegion's cloud engine and a target on a local network."
createdAt: "2021-09-06T12:51:38.700Z"
updatedAt: "2022-10-11T17:17:35.012Z"
---
The Bright Repeater is a scan proxy which provides a secure connection between the Bright cloud engine and a target on a local network. The Repeater mode enables you to securely scan targets on a local network, without having to allowlist the Bright IP address in your firewall for incoming traffic. See [Repeater (Scan Proxy)](/docs/on-premises-repeater-local-agent) for more information.


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FipFkP0od_04%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DipFkP0od_04&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FipFkP0od_04%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/embed/ipFkP0od_04\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture",
  "title": "Connecting a Local Repeater",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/ipFkP0od_04/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/embed/ipFkP0od_04\"%20title=\"YouTube%20video%20player\"%20frameborder=\"0\"%20allow=\"accelerometer;%20autoplay;%20clipboard-write;%20encrypted-media;%20gyroscope;%20picture-in-picture"
}
[/block]




## Creating (registering) a new repeater

To create (register) a new Repeater, follow these steps:

1. Select the **Repeaters** option in the left pane to display the **AVAILABLE REPEATERS** list. 
2. In the upper left corner, click **+ Create Repeater**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fbb0e03-create-repeater.png",
        "create-repeater.png",
        1917
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. In the **Create Repeater** dialog box, do the following:  
   a) In the **Name** field, enter a name for the Repeater.  
   b) _(Optional)_. In the **Description** field, enter a short description of the Repeater.  
   c) In the **Projects** section, select either to create the Repeater for all projects or only for specific ones. If you select the second option, the created Repeater will only be available when configuring scans for the predefined projects.  
   d)  _(Optional)_. In the **Scripts** section, add a script to be used with the created Repeater. The scripts should be created in advance on the **Scripts page**. To learn more, read [Using Repeater Scripts](/docs/repeater-scripts).  
   e) Click **Add**. 

<img src="https://files.readme.io/4e57962-create-repeater.png" width="340" height="540">

## Reviewing all repeaters

To review the list of all existing repeaters, select the **Repeaters** option in the left pane. Each Repeater appears as a single row.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9252b21-repeaters-list.png",
        "repeaters-list.png",
        1906
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Editing repeater details

To edit Repeater details, follow these steps:

1. Click the <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> button next to a Repeater name and then select the **Edit** option.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bf4abfd-edit.png",
        "edit.png",
        1893
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Modifying the Repeater details as you need, and then click **Update**.

## Deactivating the repeater

To deactivate the Repeater, click the <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> button next to the Repeater name, and then select the **Deactivate** option.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4ae5e38-deactivate.png",
        "deactivate.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Activating the repeater

To activate the Repeater, click the <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> button next to the Repeater name, and then select the **Activate** option.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f7d0fc5-activate.png",
        "activate.png",
        1912
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Diagnosing network connection

You can check if a created (registered) Repeater can successfully connect to all target hosts on your local network. The Repeater diagnostics allows you to reveal and fix the network connection problems before you run a scan.

**Prerequisites**

- You have created the Repeater in the [Bright app](https://app.neuralegion.com).
- You have registered the Repeater in your local network using the [Bright CLI](/docs/about-nexploit-cli).

To run the connection diagnostics, follow these **steps**:

1. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the Repeater connected to your network, and then select **Diagnose**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6072c8b-repeater-diagnose.png",
        "repeater-diagnose.png",
        1898
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Under the Repeater name, select one of the following options: 

- **Ping (Multiple URLs)** - Enables testing of the network connectivity on a single or multiple targets. You are only required to enter the URL(s) of your internal (local) target application(s) to initialize the diagnostics. You can add up to 1000 target hosts separated with a newline, semicolon or comma.   
- **Traceroute (Single URL)** - Provides a full IP trace on a specific target. It means that this option returns a list of all the IPs along the route of the request, thus allowing you to detect the connectivity bottlenecks. You simply need to specify the target hostname or IP address to initialize the diagnostics.

<img src="https://files.readme.io/fffd419-Group_1335.png" width="420" height="500"> 

3. In the **Targets** field, specify the URL(s) of the diagnostics target(s).

4. Click **Run tests**.  
   The full results of the diagnostics will be provided in the **Results** section. You can also quickly check if the diagnostics passed successfully or not by the status displayed in the upper-right corner of the \*\*Repeater remote network diagnostics" dialog box. 

## Deleting the repeater

To delete the Repeater, follow these steps:

1. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> to the left of the Repeater name.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d6124e3-delete.png",
        "delete.png",
        1910
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Select the **Delete** option, and then click **Yes**.