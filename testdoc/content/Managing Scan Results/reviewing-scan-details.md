---
title: "Reviewing Scan Details"
slug: "reviewing-scan-details"
hidden: false
metadata: 
  description: "NeuraLegion allows you to monitor the scan progress, check the setup parameters and runtime notifications, as well as view the scan results. All these options are available for each scan selected on the Scans or Scans History page."
createdAt: "2021-09-02T06:57:30.220Z"
updatedAt: "2023-01-04T09:34:53.483Z"
---
Bright allows you to monitor the scan progress, check the setup parameters and runtime notifications, as well as view the scan results. All these options are available for each scan selected on the **Scans** or **Scans History** page. 

## Monitoring scan progress

You can monitor scan progress in the following sections:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc4f2ea-0.png",
        null,
        ""
      ],
      "sizing": "650px"
    }
  ]
}
[/block]



- **SCAN PROGRESS**  
  Shows the scan duration (till the moment, or overall if completed), the overall progress of the tests run, as well as average scan speed and response time. The overall progress is based on the percentage of completed tests. You can check how many tests have already been completed and how many still remain in the **Progress** tab of the **SCAN INFO** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/351c589-1.png",
        null,
        ""
      ],
      "sizing": "650px"
    }
  ]
}
[/block]



- **COVERAGE**  
  Shows the status of entry-points discovery.

- **Total found issues**  
  Shows the number of detected vulnerabilities grouped by severity.

- **Total requests**  
  Shows the total number of requests sent during the scan.

## Reviewing initial scan settings

You can check the scan settings on create in the **Configuration** tab of the **SCAN INFO** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0d67239-2.png",
        null,
        ""
      ],
      "sizing": "650px"
    }
  ]
}
[/block]



## Reviewing scan results

The **SCAN INFO** section contains detailed information related to the scan results in the following tabs: 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/73d7f39-2a.png",
        null,
        ""
      ],
      "sizing": "650px"
    }
  ]
}
[/block]



- **Issues**  
  Shows all the issues (vulnerabilities) detected during the scan. All the issues are grouped by issue type.  You can open the report on a specific issue by selecting it from the opened issue list. Each report provides detailed information about the detected issue and the guidelines on how to fix and prevent the issue. To find more information about issue reports, see [Handling Discovered Issues](/docs/handling-discovered-issues).  

- **Engine notifications**  
  You can view the notifications sent by the engine during the scan and download them. 

- **Entry-points**  
  Shows all entry-points discovered and scanned by Bright. You can open an overview for each entry-point by selecting it from the table.  The tested scenarios represent the number of compromising requests sent to the application to reveal the vulnerability. The information on the tested scenarios is provided in the engine log that you can generate in the relevant tab.

- **Sitemap**  
  Shows a map representing the scope of the scan (attack surface). This sitemap shows all the parts of the application that Bright has identified and scanned.

- **Network**  
  Shows the response statuses received by Bright from the application during the scan, as well as the number of responses per each status. Check this section to determine whether there may be problems with the scan. For example, if the section shows that Bright receives mostly 404 statuses, it may indicate that Bright is blocked by a WAF, or that there is a problem with authentication (it may have expired).

- **Tech stack**  
  Shows the detected technical stack that is used by the application. For example, which programming language is used, the type of database and/or web server, the front-end stack, and so on.  
  The discovery of the technical stack by Bright may demonstrate to you how easily an external entity can discover it. As a result, you may decide to improve the protection of the technical stack.

- **Engine Log**  
  Allows you to generate the engine logs, which are then can be downloaded via the link sent to your email.

## Adding comments to a scan

The **Comments** tab enables you to add comments and notes describing the scan, notes for yourself, or notes for other members of your organization. You can format the comment using markdown or the provided formatting tools. To mention other users in your organization, use the @ symbol.

After the comment is ready, click **Preview** to check the final view of the comment or **Comment** to post the comment immediately. After the comment has been posted, a new section called **TOTAL COMMENTS** appears at the bottom of the page. This section shows all comments posted previously. To include a comment in the scan report, select the **Include in report** checkbox under the comment.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fa5d4f5-3.png",
        null,
        ""
      ],
      "sizing": "650px"
    }
  ]
}
[/block]