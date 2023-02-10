---
title: "monday.com"
slug: "mondaycom"
hidden: true
createdAt: "2021-09-16T14:53:51.355Z"
updatedAt: "2022-10-11T17:52:25.668Z"
---
> 🚧 Disclaimer
> 
> The integration with [monday.com](https://monday.com) is currently under development and is not available to customers yet. Contact us at [support@neuralegion.com](mailto:support@neuralegion.com) to learn more.

[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      <h1></h1>\n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/b337334-Integration_logo_template14.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      You can integrate your <b>monday.com</b> board with the NeuraLegion App to automtically create tickets with the reports of detected issues. The integration is configured on the <b>monday.com</b> side, via the NeuraLegion integration app available on the <b>monday.com</b> markeplace. Any changes on the NeuraLegion App side are disabled.<br></br>  You simply need to add the app to your board to enable the integration configuration. Each ticket with an issue report will include the following information:\n      <ul>\n        <li>Issue severity level</li>\n        <li>Details of discovery</li>\n        <li>Possible exposure</li>\n        <li>Remediation suggestions </li>\n</ul>\n    </td>\n  </tr>\n  <tr><td></td></tr>\n</table>\n</body>"
}
[/block]



The NeuraLegion integration app allows you to integrate different <b>monday.com</b> boards with different NeuraLegion projects. This means that the results of the scan run under a particular project will be provided on a separate board. 

## Prerequisites

- You are an active user in the [NeuraLegion App](https://app.neuralegion.com). 

## Step-by-step guide

### Connect your monday.com domain to Bright organization

To enable the integration, you need to connect your NeuraLegion organization to your **monday.com** domain first: 

1. Go to the NeuraLegion App.
2. In the left pane, select **Organization**. 
3. On the **Organization** page, scroll down to the **TICKET MANAGEMENT INTEGRATION** section.
4. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to **monday.com**, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0611c51-monday-settings.png",
        "monday-settings.png",
        1898
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the dialog box, enter your **monday.com** domain and click **Connect**.  
   You are redirected to the **monday.com** marketplace. You need to close the marketplace window, since the integration is configured for a specific board. 

### Integrate your monday.com board with Bright

1. From the **Workspaces**, select the board that you want to integrate with NeuraLegion.
2. In the board header, click **Integrate**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6996559-integrate.png",
        "integrate.png",
        1908
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. From the apps list, select the **NeuraLegion integration** app and add it to your board.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d332e1-nl-recipe.png",
        "nl-recipe.png",
        1815
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. On the **monday.com** web page,  click **Authorize**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3dd8129-monday-authorize.png",
        "monday-authorize.png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. Set the recipe according to which the tickets for detected issues will be created on the board.  
   The **item** configuration allows you to adjust the default board columns based on the issue information. For example, you can set a severity level to be displayed in a separate column, or next to the issue title in the **Title** column.  The recommended board setup is the following:
   - Set **Name** to **Title** to create a separate column for an issue title.
   - Set **Status** to **Severity** to create a separate column for an issue severity level.
   - Set **Item Update** to **CWE ID**, **ID**, **CVSS**, **Description**, and **Remedy** to get a complete issue report as a comment to the issue item. You can customize this field by excluding the information that might be redundant for you.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d2647d3-item-setup.png",
        "item-setup.png",
        1804
      ],
      "sizing": "80"
    }
  ]
}
[/block]



6. Click **Done**, and then click **Add to board**.  
   The integration is enabled. This is also indicated in the **TICKET MANAGEMENT INTEGRATION** section in the NeuraLegion App. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/47e8b66-monday-enabled.png",
        "monday-enabled.png",
        1899
      ],
      "sizing": "80"
    }
  ]
}
[/block]



 Now you can run a scan from the NeuraLegion App under the selected project and check the detected issues on the integrated board.

### Edit the integration

You can only edit the integration configuration on the **monday.com** side. To do that, follow these steps:

1. Select the board integrated with NeuraLegion.
2. In the board header, click **Integrate**, and then open the **Board Integrations** tab.
3. In the upper-right corner of the NeuraLegion integration, click the settings icon, and then select **Edit Integration**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/27e2769-edit-integration.png",
        "edit-integration.png",
        1815
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Make the required changes to the integration configuration and click **Update Integration**. 

### Delete the integration

You can only delete the integration configuration on the **monday.com** side. To do that, follow these steps:

1. Select the board integrated with NeuraLegion.
2. In the board header, click **Integrate**, and then open the **Board Integrations** tab.
3. In the upper-right corner of the NeuraLegion integration, click the settings icon, and then select **Delete Integration**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/129fa86-delete-integration.png",
        "delete-integration.png",
        1808
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Confirm the deletion by clicking **Delete permanently**.