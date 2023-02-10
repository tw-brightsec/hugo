---
title: "Azure Pipelines Old"
slug: "azure-pipelines-oldy"
hidden: true
metadata: 
  description: "To manage the scanning process and view the results, go to your NeuraLegion account."
createdAt: "2021-09-16T08:45:24.684Z"
updatedAt: "2022-10-11T17:51:25.465Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/b478b0c-azure-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      If you are using Azure DevOps for development automation, you can integrate Bright with your Azure CI pipeline using the <a href=\"https://marketplace.visualstudio.com/items?itemName=Neuralegion.nexploit\">Nexploit DevOps Integration extension</a>. The integration allows you to automate the security testing flow by running the Bright scans on every new build within your development environment.\n    </td>\n  </tr>\n  <tr>\n  <td width=\"65%\">\n    <h2>Prerequisites</h2>\n    </td>\n    </tr>\n</table>\n</body>"
}
[/block]



- You have the [Nexploit DevOps Integration extension](https://marketplace.visualstudio.com/items?itemName=Neuralegion.nexploit)  installed on your Azure DevOps Server. 
- The target of the scan is accessible from the Internet.
- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) with the following scopes:
  - `scans : run`
  - `scan : read`
  - `scans : stop`

## Setup

### Using a pre-recorded HAR file

If you want to start a new scan with an added HAR file, first upload your HAR file to the [Bright app](https://app.neuralegion.com) using a simple curl command: 

```bash
$ curl -X POST "https://app.neuralegion.com/api/v1/files?discard=true"  \
    -H "Content-Type: multipart/form/data"                       \
    -H "Authorization: Api-Key API_KEY" \
    -f 'har=@//path/to/the/file.har"   
```



The response **id** will then be used during setting a new scan in the pipeline, for example:

```bash
 {"ids":["FILE_ID"]}
```



## Step-by-step guide

### Opening the Integration extension in your pipeline

1. In your pipeline, click the **Show assistant** button.

<img src="https://files.readme.io/c095d92-show-assistant.png" width="350" height="160">

2. In the **Tasks** field, enter **nexploit scan**.

<img src="https://files.readme.io/bb609d9-nexploit-scan.png" width="350" height="340">

3. Do one of the following:

- To start a new scan, select the **Nexploit Scan** file.
- To re-run an existing scan, select the **Nexploit Re-run Scan** file. 

### Starting a new scan in your pipeline

To initialize a new scan in your pipeline, follow these steps:

1. In the **Nexploit Scan** section, enter the scan details in the relevant fields and select the settings that you want to apply.  
   For a scan with uploaded HAR file, additionally enter the response **id** in the **File ID** field.

<img src="https://files.readme.io/2f91924-new-scan.png" width="350" height="490">

       Once you complete the setup, the scan is started automatically.

2. To manage the scanning process and view the results, go to your [Bright app](https://app.neuralegion.com) account.

### Rerunning an existing scan in your pipeline

You can restart a scan that you have already set up and run using the [Bright app](https://app.neuralegion.com). To do that, follow these steps: 

1. In the **Nexploit Re-run Scan** section, enter the scan details in the relevant fields.
2. Copy the ID of your scan in the address bar or the scan report window and paste it in the **Scan ID** field.

<img src="https://files.readme.io/3aa534c-scan-ID.png" width="350" height="490">

       Once you complete the setup, the scan is restarted automatically.

3. To manage the scanning process and view the results, go to your [Bright app](https://app.neuralegion.com) account.