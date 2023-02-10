---
title: "GitHub Actions"
slug: "github-actions"
hidden: false
metadata: 
  description: "Your guide to GitHub actions"
createdAt: "2021-09-16T08:18:58.217Z"
updatedAt: "2022-12-08T12:39:03.894Z"
---
In this section, you will learn how to integrate the GitHub actions in to your CI pipeline to trigger a Bright scan on every new commit automatically.

 A full working example of a GitHub Actions pipeline with Bright can be found [here](https://github.com/NeuraLegion/example-actions).


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FcmTaVhQxAyI%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DcmTaVhQxAyI&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FcmTaVhQxAyI%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=cmTaVhQxAyI",
  "title": "Running a Scan as Part of GitHub CI Pipeline",
  "favicon": "https://www.youtube.com/s/desktop/ecd7151d/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/cmTaVhQxAyI/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=cmTaVhQxAyI"
}
[/block]




Bright provides several actions on the [GitHub marketplace](https://github.com/marketplace?type=&verification=&query=Neuralegion+). The actions allow you to run a scan, wait until a security issue is detected, and stop the scan without leaving your development environment. You can configure a .yaml file with the available actions and add the file to your pipeline. Once you make a commit to your GitHub Actions pipeline, a scan will be initiated automatically. 

More information about the Bright GitHub Actions can be found here:

- [github.com/NeuraLegion/run-scan](https://github.com/NeuraLegion/run-scan)
- [github.com/NeuraLegion/stop-scan](https://github.com/NeuraLegion/stop-scan)
- [github.com/NeuraLegion/wait-for](https://github.com/NeuraLegion/wait-for)

You can also integrate the scan results into the “Code Scanning Alerts”. This will significantly facilitate the management of detected issues.

> 📘 Note
> 
> Although it is possible to configure a CI pipeline with our [REST API](https://app.brightsec.com/api/v1/docs/), it is recommended to use our [Bright CLI](/docs/about-bright-cli) for an easier, more robust configuration of your pipeline.

## Integration configuration guide

Here is a sample .yaml file where we have already set the actions in a workflow. 

```curl
on:
  push:
    branches:
      - main

jobs:
  wait_for:
    name: Wait for any issues, gh-int + code_scanning_alerts on
    runs-on: ubuntu-latest
    container: node:16
    steps:
      - name: Scan Start
        id: start
        uses: NeuraLegion/run-scan@release
        with:
          api_token: ${{ secrets.BRIGHT_TOKEN}}
          hostname: app.brightsec.com
          name: Bright Scan - ${{ github.sha }}
          restart_scan: $SCAN_ID
      - name: Wait for breakpoint
        id: wait
        uses: NeuraLegion/wait-for@release
        with:
          api_token:  ${{ secrets.BRIGHT_TOKEN }}
          hostname: app.brightsec.com
          scan: ${{ steps.start.outputs.id }}
          wait_for: any
          code_scanning_alerts: true
          github_token: ${{ secrets.GITHUB_TOKEN }}
          timeout: 600
```



We are using two actions, which are configured as steps. 

### Step 1. Run a scan

The first step runs a scan with a name, an API token and a target hostname. In this example, we are re-runing a previous scan by its ID.

```curl
- name: Scan Start
        id: start
        uses: NeuraLegion/run-scan@release
        with:
          api_token: ${{ secrets.BRIGHT_TOKEN}}
          hostname: app.brightsec.com
          name: Bright Scan - ${{ github.sha }}
          restart_scan: $SCAN_ID
```



The scan ID (`SCAN_ID`), as well as the API token (`BRIGHT_TOKEN`), is taken from the Bright app. These are the basic inputs needed for scan configuration. For a full list of available inputs and expected outputs, check out a specific action on the [GitHub marketplace](https://github.com/marketplace?type=&verification=&query=Neuralegion+).

### Step 2. Poll the scan status and open the detected vulnerabilities as code scanning alerts

Then we proceed to polling the scan status until it returns a detected issue. 

```curl
- name: Wait for breakpoint
        id: wait
        uses: NeuraLegion/wait-for@release
        with:
          api_token:  ${{ secrets.BRIGHT_TOKEN }}
          hostname: app.brightseec.com
          scan: ${{ steps.start.outputs.id }}
          wait_for: any
          code_scanning_alerts: true
          github_token: ${{ secrets.GITHUB_TOKEN }}
          timeout: 600
```



The `wait_for` action allows you to follow the “fail-fast” approach by interrupting the build  with the first issue found. Moreover, you can set the severity of the first issue to wait for. In our example, it is set to `any`, meaning that the build will stop automatically once a low, medium, or high severity issue is found. You will also be able to manage the polling duration by specifying the timeout in seconds. The scan will stop upon the timeout expiration if no issue is detected so far. The GitHub token is a required input for the polling action.

We set the `code_scanning_alerts` to `true` in order to open the detected issue as a “Code Scanning Alert” that can be viewed and managed in the **Security** tab for the target of the scan. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/436e336-code-scanning-alerts.png",
        "code-scanning-alerts.png",
        1840
      ],
      "sizing": "80"
    }
  ]
}
[/block]



After you configure a similar file and add it to your pipeline, it will trigger a scan on every commit made to that pipeline.