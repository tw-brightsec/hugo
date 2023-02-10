---
title: "GitHub"
slug: "github"
hidden: false
metadata: 
  description: "To integrate a certain NeuraLegion project with your GitHub repository(ies), follow these steps"
createdAt: "2021-09-16T13:31:20.355Z"
updatedAt: "2022-12-08T13:25:05.508Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n    <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/416b140-gh-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      You can connect your GitHub repository to Bright to automatically open the details of all detected vulnerabilies as GitHub issues and code scanning alerts. The details contain the following information:\n      <ul>\n        <li>Issue severity level</li>\n        <li>Details of discovery</li>\n        <li>Possible exposure</li>\n        <li>Remediation suggestions </li>\n      </ul>\n      </td>\n  </tr>\n<tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    For each new scan, you can select any of your GitHub repositories integrated with your Bright projects.\n    </td>\n  </tr>\n  <tr><td></td></tr>\n</table>\n</body>"
}
[/block]



For more information about the Bright Integration with GitHub, see <a href="https://github.com/marketplace/nexploit-app">https\://github.com/marketplace/nexploit-app</a>.

## Prerequisites

- The **Issues** feature is enabled in your GitHub repository settings.  

## Step-by-step guide

### Connecting Bright to your GitHub repository

1. Go to the [Bright app](https://app.brightsec.com).
2. In the left pane, select **Organization**. 
3. On the **Organization** page, scroll down to the **TICKET MANAGEMENT INTEGRATION** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7e09bd7-ticketing-management-integration.png",
        "ticketing-management-integration.png",
        1349
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to **GitHub**, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/dbf10e9-github-settings.png",
        "github-settings.png",
        777
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the dialog box, click **Activate GitHub**.
6. On the **nexploit.app** page, select the repositories to which Bright should have access, and then click **Install**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/88f1b11-gh-install-app.png",
        "gh-install-app.png",
        2243
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- You need to install the nexploit.app only if you connect Bright to a certain GitHub account for the first time. At further connections to the same GitHub account, you will be asked to confirm the access by entering the password. 

- At further Bright connections to the same GitHub account, on the **nexploit.app** web page,  you will be able to change the **Repositories access** settings and save them by clicking **Save**.

The Bright integration with GitHub is enabled.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c113bdf-github-enabled.png",
        "github-enabled.png",
        761
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Configuring GitHub integration with Bright projects

After you have connected Bright to your GitHub account, you need to integrate a specific Bright project with your GitHub repository(ies) to be used for a scan. The integration allows Bright to automatically open the details of all detected vulnerabilities both as issues and code scanning alerts in the associated GitHub repositories.  
Moreover, you can select a certain severity level of issues (findings) to be sent to the repositories associated with your Bright project.

To integrate a certain Bright project with your GitHub repository(ies), follow [these steps](/docs/add-ticketing-integration-to-a-project).