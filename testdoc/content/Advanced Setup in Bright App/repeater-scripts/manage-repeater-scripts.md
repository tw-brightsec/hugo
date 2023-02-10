---
title: "Managing Repeater Scripts"
slug: "manage-repeater-scripts"
excerpt: "Repeater Scripts allow you to add, change or compute some part of a scan request before it is dispatched to the target."
hidden: false
metadata: 
  description: "Repeater Scripts allow you to add, change or compute some part of a scan request before it is dispatched to the target."
createdAt: "2021-09-06T15:16:45.723Z"
updatedAt: "2022-10-24T19:15:27.100Z"
---
## Creating a script

To create a script, follow these steps:

1. In the **Repeaters** section, click **\<> Repeater Scripts** in the upper right corner.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e218401-repeaters-scripts.png",
        "repeaters-scripts.png",
        1895
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the upper left corner, click **+ New Repeater Script**.
3. In the script dialog box, do the following:
   - In the Name field, enter the name of your script.
   - _(Optional)_ In the **Description** field, enter some descriptive information about your script.
   - In the **Code** field, write the script code or paste it from your external editor. 

> 📘 Note
> 
> The code example given in this field shows how to write a script for calculating a hash message authentication code (HMAC) value.

<img src="https://files.readme.io/30b2c9e-script-code.png" width="420" height="370"> 

## Reviewing all scripts

All the created scripts are displayed in the **AVAILABLE SCRIPTS** section on the **Scripts** page.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/26f6fc1-available-scripts.png",
        "available-scripts.png",
        1907
      ],
      "sizing": "80"
    }
  ]
}
[/block]



In this section, you can use the following options:

- To quickly find a certain script, enter its name, description or ID in the search field in the upper right corner.
- To select the number of scripts that you want to view on one page, select it from the **Items per page** dropdown list at the bottom.
- To switch between the pages of the available scripts, use the navigation buttons in the lower right corner.

## Editing a script

To edit a specific script, do the following:

1. In the **AVAILABLE SCRIPTS** section, select the script you want to change.
2. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the selected script, and then select **Edit**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/db5f267-edit-script.png",
        "edit-script.png",
        1901
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. In the script dialog box, add any changes you need, and then click **Update**.

## Deleting a script

To delete a specific script, do the following:

1. In the **AVAILABLE SCRIPTS** section, select the script you want to delete.
2. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the selected script, and then select **Delete**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7acde70-script-delete.png",
        "script-delete.png",
        1910
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Loading a script to the repeater

To load a script to a specific Repeater, do the following:

1. Go to the **Repeaters** section.
2. From the list of available Repeaters, select the one you need.
3. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the selected Repeater, and then select **Edit**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cf48a32-edit-script.png",
        "edit-script.png",
        1901
      ],
      "sizing": "80"
    }
  ]
}
[/block]



  In the dialog box, do the following:  
  a) Select the type of the script coverage:

- **Single global script** - applied for the requests that should cover all the target hosts. 
- **Host-specific script** - applied for the requests that aim at only one specific host.<br>

> 📘 Note
> 
> If you have loaded a local script using the Bright CLI, loading remote scripts from the cloud is disabled automatically.

<img src="https://files.readme.io/e08ce4f-scripts-type.png" width="350" height="330">

b) From the dropdown list, select the script you want to connect, and then click Update.  
  The uploaded script will be then added to the scan request executed via the specified Repeater.

<img src="https://files.readme.io/931d5d4-select-script.png" width="350" height="410">