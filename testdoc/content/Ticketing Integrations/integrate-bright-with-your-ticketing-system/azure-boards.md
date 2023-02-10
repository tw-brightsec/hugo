---
title: "Azure Boards"
slug: "azure-boards"
hidden: false
metadata: 
  description: "To integrate a certain NeuraLegion project with your Azure project(s), follow these steps."
createdAt: "2021-09-16T14:43:46.576Z"
updatedAt: "2022-10-11T17:43:23.375Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n     \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/c2b2140-Integration_logo_template02.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      You can connect your Azure board to a Nexploit scan to get all the discovered issues on automatically created Azure tickets. Bright opens each new ticket for one specific issue and provides the following information:\n      <ul>\n        <li>Issue severity level</li>\n        <li>Details of discovery</li>\n        <li>Possible exposure</li>\n        <li>Remediation suggestions </li>\n      </ul>\n      For each new scan, you can select any of multiple boards connected to the account of your Azure DevOps organization.\n    </td>\n  </tr>\n  <tr><td></td></tr>\n</table>\n</body>"
}
[/block]



## Step-by-step guide

### Connecting Bright to your Azure DevOps organization

1. Go to the [Bright app](https://app.neuralegion.com).
2. In the left pane, select **Organization**. 
3. On the **Organization** page, scroll down to the **TICKET MANAGEMENT INTEGRATION** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/94a9edd-ticketing-management-integration.png",
        "ticketing-management-integration.png",
        1349
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to **Azure**, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6dbdad1-azure-settings.png",
        "azure-settings.png",
        543
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the dialog box, click **Activate Azure Boards**.
6. In the dialog box, select your Azure DevOps organization from the dropdown list, and then click **Save**.

The Bright integration with Azure is enabled.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/41e0bd0-enabled.png",
        "enabled.png",
        1346
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Configuring Bright integration with Azure projects

After you have connected Bright to your Azure DevOps organization, you need to integrate one or multiple Azure projects with the Bright project to be used for a scan. The integration allows Bright to automatically provide the scan reports on the associated Azure boards. Moreover, you can select a certain severity level of issues (findings) to be sent to the boards associated with your Bright project.

To integrate a certain Bright project with your Azure project(s), follow [these steps](/docs/add-ticketing-integration-to-a-project).