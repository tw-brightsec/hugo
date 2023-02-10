---
title: "Standard Mode"
slug: "standard-mode"
excerpt: "Start a scan quickly with minimal settings"
hidden: true
metadata: 
  description: "Start a scan quickly with minimal settings"
createdAt: "2021-09-20T06:38:54.203Z"
updatedAt: "2022-09-18T13:03:12.942Z"
---
1. In the **Create scan** dialog box, select the **Standard** tab to create a scan with minimal settings.
2. In the **Attack surface discovery** dropdown list, select one of the following options:

- _(Default)_ **Via automatic crawling (for websites and webapps) -** This is the simplest option. Simply enter a URL (target host) to scan the whole or a part of the specified application. To scan only specific parts of your application or add multiple hosts, click <img src="https://files.readme.io/bad6a00-plus-dark.png" width="22" height="23"> at the right side  of the **Targets** section. 

     Note that some hosts may be unreachable or unauthorized for a direct scan from the cloud:  
      - If a host cannot be reached by the engine, select a running Repeater for the scan in the section below.  
      - If a host is unauthorized for a direct scan from the cloud, either select a running Repeater for the scan or add a `.nex` file to the host root directory (read more information [here](/docs/manage-your-organization#define-the-hosts-authorized-for-scanning)). 

    See [Scanning a website with a crawler](/docs/crawler) for detailed information.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/995817e-crawler-standard.png",
        "crawler-standard.png",
        1557
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Via recorded session .HAR file (for websites and webapps) -** Use a pre-recorded session of your interaction with the application (HAR file), which has been created either manually or automatically (using QA tools, such as Selenium to scan your application). This discovery type enables you to define the scope of a scan and ensures complete coverage of the attack surface.

    See [Creating a HAR File](/docs/creating-a-har-file) to learn how to create a HAR file.

    Note that some hosts may be unreachable or unauthorized for a direct scan from the cloud:  
      - If a host cannot be reached by the engine, select a running Repeater for the scan in the section below.  
      - If a host is unauthorized for a direct scan from the cloud, either select a running Repeater for the scan or add a `.nex` file to the host root directory (read more information [here](/docs/manage-your-organization#define-the-hosts-authorized-for-scanning).

     See [Scanning a website with a HAR file](/docs/scanning-with-a-har) for detailed information.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/69ed745-har-standard.png",
        "har-standard.png",
        1557
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 👍 Tip
> 
> To enjoy both full automation and deeper attack surface analysis, you can combine **Crawling** and **Recording (HAR)** in a single scan.

- **Via API schema (for API endpoints) -** Use an \*.yml file to scan APIs. See [Scanning API endpoints](/docs/scanning-api-endpoints) for detailed information.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/799103a-api-standard.png",
        "api-standard.png",
        1557
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. From the **Repeater** dropdown list, select a Repeater (local agent) to use it for the scan. The list only includes the connected Repeaters created for the selected Project. The Repeater is created in the **Repeaters** tab and serves as a request-proxy between Bright and the target hosted on a local network.  See [On-Premises Repeater (Agent)](/docs/on-premises-repeater-local-agent) for more information. 

3. In the **Scan Name** field, enter a free-text scan name.  
   The scan name is assigned automatically based on the name of the specified host or uploaded HAR file. You can change the suggested name if you want.

4. From the **Project** dropdown list, select the Bright project you want to use for the scan.

> 📘 Note
> 
> You can start a scan ONLY with a project selected. If you do not have any projects in Bright, select the Default one.

5. Once you complete the setup, click **Start Scan** to start scanning.<br>  
   If the maximum number of scans that can be run simultaneously is exceeded, the scan is placed in the queue. The concurrent scans limitation can be set either for the entire organization or for this particular project in the project settings. The new scan will start as soon as you manually stop another running scan or when the current scan is completed.