---
title: "Azure Pipelines"
slug: "azure-pipelines"
hidden: false
createdAt: "2022-07-19T14:53:12.672Z"
updatedAt: "2022-12-08T12:44:34.267Z"
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

### Get API key

- In NexPloit Dashboard navigate to the Organization tab and scroll to the Manage your application API keys section.
- Press Create new API key button and enter any suitable name (for example, Azure key)

> 🚧 Important
> 
> Make sure to backup the API key, it cannot be restored.

### Using a prerecorded .HAR file

If you want to start a new scan with an added .HAR file, first upload your .HAR file to the [Bright app](https://app.neuralegion.com) using a simple curl command: 

```bash
$ curl -X POST "https://app.brightsec.com/api/v1/files?discard=true"  \
    -H "Content-Type: multipart/form/data"                       \
    -H "Authorization: Api-Key API_KEY" \
    -f 'har=@//path/to/the/file.har"   
```



The response **id** will then be used during setting a new scan in the pipeline, for example:

```bash
 {"ids":["FILE_ID"]}
```



This id will then be used for the **File ID** field.

When setup is complete, the new scan will start automatically and be visible in your Nexploit account.

## Step-by-step guide

### Opening the integration extension in your pipeline

1. Log in to Azure Pipelines using the GitHub account. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6205f54-1.png",
        "1.png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Create a new project. Click on **+ New Project** and create it with according **Project name** and **Visibility**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d072d55-2.png",
        "2.png",
        640
      ],
      "sizing": "smart"
    }
  ]
}
[/block]



3. Make a new pipeline with starter pipeline settings. On the left pane go to **Pipelines**, then click on the **New Pipeline**. You can create an empty repositorie on GitHub, then select it in the creating new pipeline. On the **Configure your pipeline** stage, select **Starter pipeline**, and it should output code as in the picture.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9cf675d-3.png",
        "3.png",
        1192
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Run the pipeline. After you run the pipeline for the first time, you would experience next error that you need to purchase parallelism in Azure DevOps. You can be granted one if you fill out the form in the error attached.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/11bd452-4.png",
        "4.png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. Using the Nextploit DevOps integration extension configure a scan. After you have successfully made the pipeline, click on it and then click **Edit**. On the right pane, there are tasks. If you downloaded **NexPloit DevOps Integration** successfully from marketplace, in the **Search Tasks** area, typing in **NexPloit** should output these two Tasks. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b34c1c3-5.png",
        "5.png",
        375
      ],
      "sizing": "smart"
    }
  ]
}
[/block]



6. Do one of the following:

- To start a new scan, select the **Nexploit Scan** file.
- To re-run an existing scan, select the **Nexploit Re-run Scan** file. 

### Starting a new scan in your pipeline

To initialize a new scan in your pipeline, follow these steps:

1. In the **Nexploit Scan** section, enter the scan details in the relevant fields and select the settings that you want to apply.  
   For a scan with uploaded .HAR file, additionally enter the response **id** in the **File ID** field.

<img src="https://files.readme.io/2f91924-new-scan.png" width="350" height="490">

       Once you complete the setup, the scan is started automatically.

2. To manage the scanning process and view the results, go to your [Bright app](https://app.neuralegion.com) account.

### Re-Running an existing scan in your pipeline

You can restart a scan that you have already set up and run using the [Bright app](https://app.neuralegion.com). To do that, follow these steps: 

1. In the **Nexploit Re-run Scan** section, enter the scan details in the relevant fields.
2. Copy the ID of your scan in the address bar or the scan report window and paste it in the **Scan ID** field.

<img src="https://files.readme.io/3aa534c-scan-ID.png" width="350" height="490">

       Once you complete the setup, the scan is restarted automatically.

3. To manage the scanning process and view the results, go to your [Bright app](https://app.neuralegion.com) account.

### Starting a scan with the repeater

1. Create a new repository on your GitHub account.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fb0fb83-2-1.png",
        "2-1.png",
        1600
      ],
      "sizing": "smart"
    }
  ]
}
[/block]



2. Create a new branch on the repository which we used for a scan without the repeater and upload an empty YAML file to the created branch.

3. Log in to your Azure DevOps account.

4. Select Pipelines on the left menu and create a New pipeline.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e484849-2-2.png",
        "2-2.png",
        1600
      ],
      "sizing": "smart"
    }
  ]
}
[/block]



5. Under **New pipelines** select GitHub and we will use our repository that we have previously used for a scan without the repeater. It will prompt us to authorize Azure DevOps with our GitHub account.

![](https://files.readme.io/03e5a36-2-3.png "2-3.png")

6. When prompted to Configure your pipeline, we will select **Existing Azure Pipelines YAML file** and select your corresponding branch and correct path to the YAML file.

![](https://files.readme.io/ea86a11-2-4.png "2-4.png")

7. After we have selected the correct YAML file we will be prompted to edit the preconfigured YAML file. Please note, we need to change the following parameters with our own:

- repeater (repeater ID)
- token (your Bright token)

![](https://files.readme.io/d916f8e-8-3.png "8-3.png")

8. Click on **Save and run**.

9. Monitor the scan progress and check the results.

![](https://files.readme.io/7e61a06-8-4.png "8-4.png")

![](https://files.readme.io/81bc3ca-8-5.png "8-5.png")