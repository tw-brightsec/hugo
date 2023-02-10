---
title: "Adding Ticketing Integration to a Project old"
slug: "add-ticketing-integration-to-a-project-old"
hidden: true
metadata: 
  description: "You can integrate one or multiple repositories (projects, channels) of your ticketing systems with a specific NeuraLegion project."
createdAt: "2021-09-16T07:32:22.433Z"
updatedAt: "2022-11-01T13:56:34.516Z"
---
You can integrate one or multiple repositories (projects, channels) of your ticketing systems with a specific Bright project. Therefore, you are able to select any of the repositories available for the specified Bright project when you start a new scan.  

> 🚧 Important
> 
> Only the users with the **Admin** and **Owner** roles have access to integrate a connected ticketing system with a specific project.

## Prerequisites

- Bright is connected to your ticketing systems with the repositories you want to add to a certain project.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d5768b8-issue-severity.png",
        "issue-severity.png",
        1898
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Step-by-step guide

### Configuring the Bright project integration

1. In the **TICKET MANAGEMENT INTEGRATION section**, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the ticketing system you need, and then select **Project Settings**.

<img src="https://files.readme.io/3c3cc4b-project-settings.png" width="490" height="300">

2. In the **Projects Integration Config** dialog box, do the following:

- In the **Project field**, enter or select the Bright project that you want to use for the scan.

> 📘 Note
> 
> You can start a scan only if a project is selected. If you do not have any projects in the Bright app, select the **Default** one.

- From the **Associate repository…** dropdown list, select the repository (project, channel) that you want to use for the scan results within the specified project.  
  The selected repository is automatically added to the **REPOSITORIES** list below. You can add multiple repositories (boards) to this list.
  - To arrange the associated repositories in alphabetical order, hover-over **Name** and click <img src="https://files.readme.io/34858fa-down-arrow.png" width="23" height="26"> next to it. 
  - To make the repositories order free again, hover-over **Name** and click <img src="https://files.readme.io/66a5f7c-up-arrow.png" width="23" height="26"> next to it. 
  - To delete a repository from the list, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the repository and select **Disassociate**.
  - To quickly select the required repository from the list, use the **Find a repository** search field. 
  - To select the number of associated repositories that you can view on one **REPOSITORIES** page, use the **Items per page** dropdown list.
  - To switch between the **REPOSITORIES** pages, use the navigation buttons above **Close**.  

<img src="https://files.readme.io/aab97b3-project-selection.png" width="440" height="400">

3. Once you complete the projects integration configuration, click **Close** at the bottom of the dialog box.  
   The associated repositories will be displayed in the **TICKETING SETTINGS** section on the **Project Settings** page.

### Filtering the severity level of issues to be opened in the integrated services

You can select a certain severity level of issues (findings) to be sent to a repository/channel associated with your  Bright project. For example, if you set the high severity level for the GitHub integration, then only the detected issues of high severity will be displayed in your GitHub repository. 

> 📘 Note
> 
> The option to filter issue severity is only available to the users whose roles include the `integrations.repos:manage` access scope. For more information, see [Manage Access Scopes](/docs/manage-access-scopes).

1. In the left pane, select **Projects**.
2. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the project which is integrated with the required ticketing service, and then select **Settings**.
3. In the **TICKETING SETTINGS** section, use the **Issue severity** dropdown menu to filter the issues that will be sent to the associated repository.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/37b67f1-ticketing-list.png",
        "ticketing-list.png",
        1888
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Selecting repositories for a new scan

When [starting a new scan](/docs/creating-a-new-scan), you can select one or multiple integrated repositories (projects, channels) that you want to use as destinations for the scan reports within the specified Bright project.

1. In the **Advanced** setup mode, select the **Scan Details** tab.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b4a711a-select-integration.png",
        "select-integration.png",
        1084
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. From the **Integrations** dropdown list, select the integrated repositories that you want to use for the scan.