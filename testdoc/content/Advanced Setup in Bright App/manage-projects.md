---
title: "Managing Projects"
slug: "manage-projects"
hidden: false
metadata: 
  description: "If your organization has multiple groups that work on the development of several applications simultaneously, the best way to separate and manage the scanning flows is to create different NeuraLegion projects."
createdAt: "2021-09-06T12:42:27.530Z"
updatedAt: "2022-12-24T14:49:27.294Z"
---
If your organization has multiple groups that work on the development of several applications simultaneously, the best way to separate and manage the scanning flows is to create different Bright projects. You can manage which user groups get access to a project, and have full control over certain permissions and associated ticketing repositories.

In addition, you can limit the number of concurrent engines (scans) for each project so that each team has equal access to the organization engines. Let’s imagine that your organization has 10 engines and 2 projects, and there is no limitation on concurrent engines for these projects. It means that one project team can run all available engines at once and block the other team from scanning. To prevent such situations, you can, for example, set up the maximum number of concurrent engines to 5 per team, so that each team will be able to run 5 scans simultaneously without blocking each other. If a team decides to run more than 5 scans at once, the scans that exceed the limit will be queued. 

If you have integrated Bright with the ticketing tool a project team uses, the relative repositories (projects, channels) can be associated with a specific project. The integration configuration allows teams of different projects to select the repository associated with their project when creating a new scan. As a result, all the discovered issues will be opened as tickets or messages automatically in the selected repository.  

You can find more information about Bright integration with ticketing systems [here](https://docs.brightsec.com/docs/integrate-bright-with-your-ticketing-system).

> 📘 Note
> 
> A project is required for the configuration of a new scan, so if you do not have any custom projects, you need to select the default one.

## Creating a project

To create a project, follow these steps:

1. In the left pane, select **Projects** and click **+ Create Project**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/eb01ab9-create-project.png",
        "create-project.png",
        1912
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **Create project** dialog box, enter a project name and select the groups that can access the project.

<img src="https://files.readme.io/0979fe2-project-popup.png" width="360" height="470">

3. Click **Save**.  
   A successfully created project appears in the **MY PROJECTS** table.

## Viewing the project scans

You can view the scans run within each particular project as well as retest, edit and delete them.  To view and manage project scans, click the raw with the project you need in the **MY PROJECTS** table. 

> 👍 Tip
> 
> You can open a project or a project scan in a new tab by a middle-mouse click or a Ctrl + left-mouse click.

Most features of the scans, such as retesting, stopping, editing, exporting, and deleting, are the same as on the **Scans** page. Find more information [here](/docs/reviewing-scans). 

## Setting a maximum number of concurrent scans for a project

To set a limit for scans that can be run simultaneously by one project team, do the following:

1. In the **MY PROJECTS** table, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the project where you want to set a limit to concurrent scans, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/75a4f9d-project-settings.png",
        "project-settings.png",
        1907
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **PROJECT SETTINGS** section, select the check box next to **Limit number of concurrent scans**.
3. In the **Max. concurrent scans** field, enter the number of engines that can be run concurrently for this project.  
   Please make sure that the number you set does not exceed the total  number of engines available for the entire organization.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/09452e5-limit-conc-scans.png",
        "limit-conc-scans.png",
        1899
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. At the top right of the **Project Settings** page, click **Save**.

## Reviewing the project issue details

You can view the information about all issues detected during the project scans, as well as check the parent scans. The information includes the issue type, HTTP method, number of times reported, and link to a vulnerable source.

To view the details and parent scans of a specific issue, you simply need to select this issue from the **PROJECT ISSUES** table on the **Project page**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2a61a17-project-issue-details.png",
        "project-issue-details.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Configuring an issue and assign it to a project user

You can set a status and severity for all project issues to treat them as tasks and assign them to different members of your project team. 

To configure an issue and assign it to a project user, follow these steps:

1. On the **Project** page, scroll down to the **PROJECT ISSUES** table and select the issue you want to configure.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8dd0ea0-issues-table.png",
        "issues-table.png",
        1895
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **ISSUE CONFIGURATION** section, select the status, severity and assignee for the issue.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3bf12f3-project-issue-configuration.png",
        "project-issue-configuration.png",
        1884
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Adding a group to project

To add a group to the project, follow these steps:

1. In the **MY PROJECTS** table, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the project where you want to delete a group, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/215b36f-project-settings.png",
        "project-settings.png",
        1907
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the upper-right corner of the **GROUP MANAGEMENT** section, select the group to be added to the project from the **Add group** dropdown list.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a183793-add-group-project.png",
        "add-group-project.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Deleting a group from project

To delete a group from a project, follow these steps:

1. In the **MY PROJECTS** table, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the project where you want to delete a group, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/64922c5-project-settings.png",
        "project-settings.png",
        1907
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **GROUP MANAGEMENT** table, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the group you want to delete, and then select **Delete**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0afa790-delete-group-priject.png",
        "delete-group-priject.png",
        1903
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Managing project API keys

You can create and manage project-level API keys (also called authentication tokens ) for accessing the Bright API and CLI.

To create a new API key, follow these steps:

1. In the **MY PROJECTS** table, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the project for which you want to create an API key, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2918cc7-project-settings.png",
        "project-settings.png",
        1907
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Scroll down to the **MANAGE YOU PROJECT API KEYS** and click **+ Create API Key**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ae2e817-create-key.png",
        "create-key.png",
        1907
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Assign the API key a name, select which scope(s) of access to allow it and which type of actions (such as read or write) it is permitted to perform. 

<img src="https://files.readme.io/9f8ff9f-key-popup.png" width="400" height="460">

4. Click **Create**.  
   On the popup, copy the generated key and save it to a safe place since as soon as you navigate away from this popup, you will not be able to restore this key.  
   The created keys without the entire values are listed in the **MANAGE YOUR ORGANIZATION PROJECT API KEYS** section.

## Deleting a project

To delete a  custom project, do the following:

1. In the **MY PROJECTS** table, click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the project you want to delete, and then select **Delete**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2a12ac8-delete-project.png",
        "delete-project.png",
        1904
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. On the popup, click **Yes, delete**.  
   By deleting a project, all the associated scans will be deleted along with their history and detected issues. This data cannot be restored after deletion.