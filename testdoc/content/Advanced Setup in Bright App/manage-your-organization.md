---
title: "Managing Organization"
slug: "manage-your-organization"
excerpt: "The **Organization** option enables Bright administrators to manage organization-level settings and policies"
hidden: false
metadata: 
  description: "The Organization option enables NeuraLegion administrators to manage organization-level settings and policies"
createdAt: "2021-09-20T06:43:37.826Z"
updatedAt: "2022-12-08T07:09:40.018Z"
---
## Viewing the organization dashboard

To view your organization dashboard, in the left pane, select the **Organization** option. 

## Configuring two-factor authentication policy

You can require that all users in your organization use two-factor authentication (2FA). Before applying this policy, we recommend giving your users prior notice so that they have time to enable 2FA for their accounts. 

To apply 2FA to user accounts, select the relevant checkbox in the **ORGANIZATION SETTINGS** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/214653d-2fa.png",
        "2fa.png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



An administrator can see the 2FA status of each user in the organization in the **MEMBERS** section.

> 📘 Note
> 
> An organization-wide 2FA policy cannot be set to mandatory until all the administrative users have set up their own 2FA.  
> When enabling an organization-wide 2FA policy, the users can access their accounts only after they perform 2FA. In this case, an email notification is automatically sent to each affected user.

## Defining hosts authorized for scanning

As a precaution, Bright only allows to scan trusted or authorized hosts.  


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2Fl7vyHGfFsRI%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dl7vyHGfFsRI&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2Fl7vyHGfFsRI%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=l7vyHGfFsRI&feature=youtu.be",
  "title": "How to authorize a host for scanning",
  "favicon": "https://www.youtube.com/s/desktop/01530da7/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/l7vyHGfFsRI/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=l7vyHGfFsRI&feature=youtu.be"
}
[/block]




To add a target host to the list of authorized hosts, follow these steps:

1. Download the `.nex`  file from your Bright organization. For that, click the `.nex` link at the bottom of the **ORGANIZATION SETTINGS** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/439a0f8-Get-Nex-File.png",
        "Get-Nex-File.png",
        1909
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Add the downloaded `.nex`  file to your application root directory.  
   Once added, the .nex file enables Bright to recognize the application, associate it with your organization, and gives Bright permission to scan the target directly, without the need for the Repeater.

> 📘 Note
> 
> - Make sure that the server can serve this file from the webroot (top directory level or just `/` path) along with the other static resources from that location.
> - You can always contact our support team at [support@brightsec.com](mailto:support@brightsec.com) or in the Intercom chart (on the bottom right of your screen) for help in authorizing hosts.

You can reuse this file as many times as needed.

## Viewing your organization plan

The organization **PLAN DETAILS** section displays information about your Bright account, for example, total storage for your organization, number of engines, and the plan expiration date. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f3798de-Plan-Details.png",
        "Plan-Details.png",
        1913
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Manage organization API/CLI authentication tokens


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FW_WdIGPXoUQ%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DW_WdIGPXoUQ&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FW_WdIGPXoUQ%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/embed/W_WdIGPXoUQ%22%20title=%22YouTube%20video%20player%22%20frameborder=%220%22%20allow=%22accelerometer",
  "title": "How to create an API Key (Authentication Token)",
  "favicon": "https://www.youtube.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/W_WdIGPXoUQ/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/embed/W_WdIGPXoUQ%22%20title=%22YouTube%20video%20player%22%20frameborder=%220%22%20allow=%22accelerometer"
}
[/block]




On the **Organization** page, you can obtain and manage authentication tokens (also called API keys) for accessing the Bright API and CLI.

To create a new API/CLI authentication token (API key), follow these steps:

1. Go to the **MANAGE YOUR ORGANIZATION API KEYS** section and click **+ Create API key** .

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f6e3c8e-create-api-key.png",
        "create-api-key.png",
        1903
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Assign the API key a name, select which scope(s) of access to allow it and which type of actions (such as read or write) it is permitted to perform. 

<img src="https://files.readme.io/5ffe4e3-new-api-key-prompt.png" width="400" height="460">

3. Click **Create**.  
   On the popup, copy the generated key and save it to a safe place since as soon as you navigate away from this popup, you will not be able to restore this key.  
   The created keys without the entire values are listed in the **MANAGE YOUR ORGANIZATION API KEYS** section.