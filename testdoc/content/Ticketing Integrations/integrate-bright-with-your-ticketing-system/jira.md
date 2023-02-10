---
title: "Jira"
slug: "jira"
hidden: false
metadata: 
  description: "To integrate a specific NeuraLegion project with your Jira project(s), follow these steps"
createdAt: "2021-09-16T13:06:47.449Z"
updatedAt: "2023-01-04T09:35:38.510Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/aa51ba2-jira-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      You can connect your Jira project board to a Bright scan, for tickets to be automatically opened for each security vulnerability detected. Each ticket contains the following information:\n      <ul>\n        <li>Issue severity level</li>\n        <li>Details of discovery</li>\n        <li>Possible exposure</li>\n        <li>Remediation suggestions </li>\n      </ul>\n      <p></p>\n      For each new scan, you can select different Jira projects integrated with your Bright projects.\n    </td>\n  </tr>\n  <tr><td></td></tr>\n</table>\n</body>"
}
[/block]



> 🚧 Warning
> 
> If your Jira project sets any required fields for all tickets (for example, components), then Bright will not be able to open tickets for detected issues. Please check your project settings and change them if necessary.

## Prerequisites

- The Bright connection to the On-Premise Jira is enabled via the Bright CLI. For that, you need to have the Bright CLI installed on your machine.  See the installation instructions [here](/docs/installation-options). 

## Step-by-step guide

### Connecting Bright to your Jira account, cloud or on-premise

1. Go to the [Bright app](https://app.brightsec.com).
2. In the left pane, select **Organization**. 
3. On the **Organization** page, scroll down to the **TICKET MANAGEMENT INTEGRATION** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d49e14-ticketing-int.png",
        "ticketing-int.png",
        1901
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to **Jira**, and then select **Settings**.

<img src="https://files.readme.io/913a897-tick-settings.png" width="450" height="280"> 

5. In the **Jira integration config** dialog box, do one of the following:

<img src="https://files.readme.io/a868027-on-premise.png" width="360" height="380">

- If you are using the Atlassian Jira Cloud, select the **Cloud Jira** radio button. Enter your Jira details and API token in the relevant fields, and then click **Save**.

> 🚧 Important
> 
> For security purposes, make sure to use the API token of a specific Jira profile (not the Admin/Organization level).

The Bright connection to Jira is enabled, which is indicated in the **Enabled** column. The **Connectivity**  column is designed to indicate a local Jira Server connection status, which is irrelevant in this case.  

<img src="https://files.readme.io/5cf1c0c-jira-enabled.png" width="450" height="230">

- If you are using Jira on a local server, do the following:  
  a) Select the **On-Premise Jira** radio button.  
  b) In the **Access Key** field, copy an automatically generated `INTEGRATION_ACCESS_KEY`. You will need it to run the CLI command that enables connection to your On-Premise Jira account.  
  c) Open your console and run the following CLI command: 

```shell
nexploit-cli integration --access-key $INTEGRATION_ACCESS_KEY --base-url https://your-cluster.atlassian.net --user $USERNAME --password $PASSWORD --token $API_TOKEN
```



> 📘 Notes
> 
> - Sample variables are marked with a `$`. You must substitute them for your real values.
> - If your Jira username or password includes any special characters (for example, "pa$$word"), enclose the entire username or password in single quotes.

This is the basic configuration of the command that connects Bright to an On-Premises Jira account. For more information about the command and its options, see [Integrating with an On-Premise Ticketing Service](/docs/integrating-with-a-service).

Once you connect Bright to the On-Premise Jira via the Bright CLI, the **Connectivity** status in the **TICKET MANAGEMENT INTEGRATION** section changes to **Connected**. The **Enabled** column indicates the Cloud Jira connection status, which is irrelevant in this case.

<img src="https://files.readme.io/e55aa6f-jira-connectivity.png" width="450" height="200">

### Configuring Jira integration with Bright projects

After you have connected Bright to your Cloud or On-Premise Jira, you need to integrate one or multiple Jira projects with the Bright project to be used for a scan. The integration allows Bright to automatically open tickets with the detected issue details on the associated Jira boards. Moreover, you can set a certain severity level for issue tickets to be opened.

To integrate a specific Bright project with your Jira project(s), follow [these steps](/docs/add-ticketing-integration-to-a-project).