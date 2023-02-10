---
title: "TeamCity"
slug: "team-city"
hidden: false
createdAt: "2022-04-07T13:01:24.247Z"
updatedAt: "2022-10-11T17:33:59.705Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/264ccf1-team-city.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    You can configure your TeamCity CI/CD pipeline to automatically run a Bright scan with every new build. Once a build is made to the pipeline, Bright initiates security tests and provides all the information that developers need to fix the detected vulnerabilities, without having to leave their development environment.\n    </td>\n  </tr>\n<tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    Although it is possible to configure a CI/CD pipeline with the <a href=https://app.neuralegion.com/api/v1/docs/>Bright REST API</a>, it is recommended to use the <a href=/docs/about-nexploit-cli>Bright CLI</a> for an easier, more robust configuration of your pipeline.\n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



## Prerequisites

- You have a valid Bright API key (`env.BrightToken`) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- Register the Repeater in the [Bright app](https://app.neuralegion.com/) and copy the generated `REPEATER_ID`. See [Managing Repeaters](/docs/manage-repeaters) for more information.
- Install and configure the TeamCity CI/CD server and agent.

> 📘 Note
> 
> The Linux Docker deployment of TeamCity is currently not supported — <https://youtrack.jetbrains.com/issue/TW-74746>.

## Step-by-step guide

1. Open the TeamCity **Administration** panel.
2. From the left menu, select **Projects**, and then click **+ Create project**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/72f6744-create-project.png",
        "create-project.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. In the **Name** field, enter a name for your project (for example, "Bright Scan"), and then click **Create**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fe05882-create-bright-project.png",
        "create-bright-project.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. In the upper-right corner of the created project page, click **Project Home**.  

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f2ce630-project-home.png",
        "project-home.png",
        1726
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. Click **Create Build Configuration**, and then select **Manually**.
6. In the **Name** field, enter a name for your build configuration (for example, BrightBuild), and then click **Create**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a7e7b3a-create-build.png",
        "create-build.png",
        1686
      ],
      "sizing": "80"
    }
  ]
}
[/block]



7. The **New VCS Root** form opens. Click **Skip** to proceed to the next step. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a1be02b-skip.png",
        "skip.png",
        1895
      ],
      "sizing": "80"
    }
  ]
}
[/block]



8. From the left menu, select **Parameters**, and then click **+ Add new parameter**. 
9. Create the `endBrightToken` (API key) environment variable:  
   a) In the **Name** field, enter `endBrightToken`.  
   b) In the **Value** filed, enter the value of the token (API key) you have created in the Bright app (see [Prerequisites](/docs/team-city#prerequisites)).  
   c) Click **Save**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a3acaf9-7.png",
        "7.png",
        1885
      ],
      "sizing": "80"
    }
  ]
}
[/block]



10. Create the `REPEATER_ID` environment variable:  
    a) In the **Name** field, enter `REPEATER_ID`.  
    b) In the **Value** filed, enter the ID of the Repeater you have created in the Bright app (see [Prerequisites](/docs/team-city#prerequisites)).  
    c) Click **Save**.
11. From the left menu, select **Build Steps**.
12. On the **New Build Step** page, do the following:  
      a) Set **Runner Type** to `Node.js`.  
      b) Set **Run step within Docker container** to `node: 14.17.1`.  
      c) Set **Shell script** to the following:

```curl
npm install @neuralegion/nexploit-cli
cd node_modules/.bin
./nexploit-cli --version
echo "Starting Repeater"
./nexploit-cli repeater --id %env.REPEATER_ID% --token %env.BrightToken% &
sleep 10
echo "Starting NeuraLegion Scan"
SCAN_ID=$(./nexploit-cli scan:run --token %env.BrightToken% --repeater %env.REPEATER_ID% --name "new scan" --crawler Broken Crystals  --smart)
echo "Scan was started with ID NeuraLegion 
sleep 10
echo "Waiting for issues..."
./nexploit-cli scan:polling --interval 30s --timeout 30m --breakpoint any --token %env.BrightToken% $SCAN_ID
```



[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c35d63c-8.png",
        "8.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



```
 13. Click **Save**. 
```



10. On the top right, click **Run** to run the build.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ddf62f5-run-build.png",
        "run-build.png",
        1887
      ],
      "sizing": "80"
    }
  ]
}
[/block]



11. To check that your build has started, click **Agents**, and then click **Running**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8368b49-running.png",
        "running.png",
        1843
      ],
      "sizing": "80"
    }
  ]
}
[/block]



12. To check the build logs, open the **Build Log** tab.  
      You can see that the Repeater and scan have started, the polling state is also active. You can also monitor the scan progress in the Bright app. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bde1c3a-11.png",
        "11.png",
        1885
      ],
      "sizing": "80"
    }
  ]
}
[/block]