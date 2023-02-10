---
title: "Slack"
slug: "slack"
hidden: false
metadata: 
  description: "For more information about NeuraLegion Integration with Slack channels, see NeuraLegion in the Slack App directory"
createdAt: "2021-09-16T14:33:43.382Z"
updatedAt: "2023-01-04T12:35:50.370Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n\n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/0b1e923-slack-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      You can configure the Bright app to automatically send messages about detected issues to your selected Slack channels. Each message is a report which includes the following information:\n      <ul>\n        <li>Issue severity level</li>\n        <li>Details of discovery</li>\n        <li>Possible exposure</li>\n        <li>Remediation suggestions </li>\n      </ul>\n      For each new scan, you can select any of your Slack channels integrated with your Brigth projects. \n    </td>\n  </tr>\n  <tr><td></td></tr>\n</table>\n</body>"
}
[/block]



For more information about Brigtht Integration with Slack channels, see [BrightSec in the Slack App directory](https://slack.com/apps/APTQSHNES-nexploit).

## Prerequisites

- You have the Slack channel(s) to which Bright can post the scan results.

## Step-by-step guide

### Connecting Bright to your Slack channel

1. Go to the [Bright app](https://app.brightsec.com).
2. In the left pane, select **Organization**. 
3. On the **Organization** page, scroll down to the **TICKET MANAGEMENT INTEGRATION** section.

![](https://files.readme.io/d266b5b-.png)



4. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to **Slack**, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8de4fee-slack-settings.png",
        "slack-settings.png",
        760
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the dialog box, click **Activate Slack**.
6. On the Slack web page, allow Bright to access your Slack workspace with the specified access scope. For that, click **Allow**.  
   The Bright connection to Slack is enabled.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b527a03-slack-enabled.png",
        "slack-enabled.png",
        762
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Configuring Slack integration with Bright projects

After you have connected Bright to Slack, you need to integrate a specific Bright project with your Slack channel(s) to be used for a scan. The integration allows Bright to automatically provide the scan reports in the associated Slack channels. Moreover, you can select a certain severity level of issues (findings) to be sent to the channels associated with your Bright project.

To integrate a certain Bright project with your Slack channel(s), follow [these steps](/docs/add-ticketing-integration-to-a-project).