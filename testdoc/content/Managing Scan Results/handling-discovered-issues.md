---
title: "Handling Discovered Issues"
slug: "handling-discovered-issues"
hidden: false
metadata: 
  description: "Review All Discovered Issues"
createdAt: "2021-09-02T10:10:09.044Z"
updatedAt: "2022-10-18T06:40:08.993Z"
---
## Reviewing all discovered issues

1. Select the **Scans** option in the left pane to display the Scans List. Each scan appears as a single row.
2. Click on the row of a scan to display its details.
3. Scroll down to the **DISCOVERED ISSUES** section, which shows a row representing each type of issue (vulnerability) discovered by the scan and the quantity of each. 

> 👍 Tip
> 
> The top of this section provides various options for filtering the discovered issues that are displayed.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cecbc97-issues-tab.png",
        "issues-tab.png",
        1905
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Reviewing discovered issue details

To display the detailed results of each discovered issue:

1. Select the **Scans** option in the left pane to display the Scans List. Each scan appears as a single row.
2. Click on the row of the scan to display its details page.
3. Scroll down to the **DISCOVERED ISSUES** section, which shows a row representing each type of issue (vulnerability) discovered by the scan and the quantity of each. 
4. Click on the issue type row **<span style="color:#FF0000;">(1)</span>** to display a row for each discovered issue of that type.
5. To display details about a specific issue, click on its row **<span style="color:#FF0000;">(2)</span>**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/253c17a-open-issue.png",
        "open-issue.png",
        1897
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Issue overview

This section provides general useful information about the issue:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/406152a-issue-overview.png",
        "issue-overview.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



1. **Status –** Specifies the current status of this specific issue. The status of this issue is **Unresolved** until it is changed in the [project issue configuration](/docs/manage-projects).
2. **Details –** Provides a short description of this issue. It also displays dynamically generated information about what happened at the bottom of the explanation. 
3. **Remedy Suggestions –** Provides a short explanation about how this issue should be fixed.
4. **Possible Exposure –** Provides a brief non-technical explanation about what kind of impact this specific issue might have on the application in case of a malicious breach.
5. **CVSS Scoring –** Provides a [Common Vulnerability Scoring System](https://en.wikipedia.org/wiki/Common_Vulnerability_Scoring_System) score summarizing this specific issue.
6. **CWE-ID –** Provides a [Common Weakness Enumeration](https://cwe.mitre.org/) ID number of this specific issue.
7. **Resources –** Provides references to resources in case more detailed explanations are required.

### Additional information

When relevant, this section provides additional technical information about the specific issue, which includes – database enumeration information, targeted DOM element information and so on.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bbe324b-additional-info.png",
        "additional-info.png",
        1895
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Request

Displays the request info in a diff-like view that shows what was changed in the request in order to execute this type of attack.

> 👍 Tip
> 
> You can use the Copy as CURL button at the top right of the request display in order to execute it manually.

### Response

Provides all the response information.

### Screeenshot

When relevant, shows a screenshot demonstrating the attack execution.

### User comments

The section at the bottom of the page enables you to enter comments and notes describing the discovered issue for yourself or notes for other people in the organization. You can format the comment using markdown or using the provided formatting tools. To mention other users in your organization use the @ symbol. 

After you enter the comment, click the **Preview** button to display it. Click the **Comment** button to post the comment. After a comment has been posted, a new section appears at the bottom called **ALL COMMENTS** showing all previously posted comments.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3aae631-user-comment.png",
        "user-comment.png",
        1899
      ],
      "sizing": "80"
    }
  ]
}
[/block]



To include this comment in the scans report, check the **Include in report** checkbox under the comment.

## Navigating between issues

To quickly navigate between issues click the title of an issue to open a scrollable list of all the issues in this scan.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5a4e849-navigating-issues.png",
        "navigating-issues.png",
        1900
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Downloading an issue script

To download the specific issue details as a .JSON file to be used later click the **Download script** <img src="https://files.readme.io/cb3c586-download-button.png" width="22" height="26"> button.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/84e38ed-download-script.png",
        "download-script.png",
        1905
      ],
      "sizing": "80"
    }
  ]
}
[/block]



Example script:

```json
{
  "method": "GET",
  "url": "https://neuralegion-open-bucket.s3.amazonaws.com/?list-type=2",
  "headers": {
    "Cookie": "bc-calls-counter=1; connect.sid=Mddt-tFZwphRs5j7OfQinnPAZ6AW7piQ.Zpt5j%2F2IZCg2US2k6iALU3%2Fz5mEvh2OyQRBgTI28QE8",
    "User-Agent": "Mozilla/5.0 (X11; Linux x86_64; rv:68.0) Gecko/20100101 Firefox/68.0",
    "Accept-Encoding": "identity"
  }
}
```



## Retesting an issue

Retesting at issue creates a separate scan entity that is a duplicate of the selected scan. Initially, the settings are identical, but can be modified by you without affecting the original scan settings.

To modify and re-test a specific issue by using the script editor:

1. Click the **Modify script** <img src="https://files.readme.io/fb78c20-modify-button.png" width="23" height="26"> button.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/aac260d-modify-script.png",
        "modify-script.png",
        1897
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the script editor, you can edit any request field and retest it (scan it again) by clicking the **Execute** button.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/700e20b-execute-script.png",
        "execute-script.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]