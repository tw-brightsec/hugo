---
title: "JFrog"
slug: "jfrog"
hidden: false
metadata: 
  description: "A Git repository is given as a JFrog resource, so you can use this repository for any events, such as pushing a new commit or as a trigger to run a security scan"
createdAt: "2021-09-16T07:52:15.810Z"
updatedAt: "2022-12-08T13:21:57.035Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/dcce3bb-jfrog-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    If you are using JFrog  Pipelines for development automation, you can integrate it with Bright to run security scans on every new build as part of your SDLC.\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n   For this example, we use a sample vulnerable application in a public <a href=\"https://github.com/neuralegion/jfrog-example\">GitHub repository</a>. The repository also contains the corresponding JFrog Pipeline YAML file. You can use this application for a test project.\n    </td>\n  </tr>\n  <tr>\n  <td>\n    <h3>Prerequisites</h3>\n    </td>\n    </tr>\n</table>\n</body>\n"
}
[/block]



- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
  <p>

### YAML File Breakdown

#### Resources and Pipelines Configuration

The YAML file contains configuration for security scanning and the pipeline itself, with details of the repository and execution steps.

```bash
resources:
  - name: jfrognexploit
    type: GitRepo
    configuration:
      gitProvider: GH
      path: NeuraLegion/jfrog-example

pipelines:
  - name: nexploit
    steps:
      - name: nexploit
        type: Bash
        configuration:
          integrations:
            - name: Nexploit
          inputResources:
            - name: jfrognexploit
```



A Git repository is given as a JFrog resource, so you can use this repository for any events, such as pushing a new commit or as a trigger to run a security scan.

#### Execution Steps

The execution steps are the following:

1. Setting up the environment (NodeJS).
2. Installing the [Bright CLI](/docs/about-nexploit-cli) utility. Using the Bright CLI commands, you can run, poll status and stop scans directly from your pipeline.

```bash
execution:
          onExecute:
            - sudo apt update
            - sudo chmod 1777 /tmp
            - sudo apt update
            - sudo apt install nodejs npm
            - sudo apt install --fix-broken
            - sudo npm install -g @neuralegion/nexploit-cli --unsafe-perm=true
            - |
```



#### Scan Setup

The scan setup includes the following details:

1. A crawler will be used on the target to define the attack surface and optimize the security tests.
2. BRIGHT_TOKEN (API key) is required to use the Bright CLI.
3. Interval of polling the scan results (detected issues).
4. The length of the scan (timeout).
5. When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command. The scan stops automatically once a high severity issue is detected.  See the [Bright CLI command list](/docs/command-list) for a full list of commands you can use for a scan.

```bash
 SCAN_ID=$(nexploit-cli scan:run                                                \
                  --name "💎 Broken Crystals for a #${res_jfrognexploit_commitSha} #${run_id}" \
                  --crawler https://brokencrystals.com                                         \
                  --token $BRIGHT_TOKEN)
            - printf "Scan was started with ID https://app.neuralegion.com/scans/$SCAN_ID"
            - |
              nexploit-cli scan:polling               \
                --interval 30s                        \
                --timeout 12m                         \
                --token $BRIGHT_TOKEN  \
                --breakpoint high_issue $SCAN_ID
          onComplete:
            - nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
```



### Step-by-Step Guide

#### Step 1: Set up an Automatic Scan in JFrog

On the **Node Pools** page, click **Add Node Pool** and configure.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/52e3ded-add-node-pool.png",
        "add-node-pool.png",
        1137
      ],
      "sizing": "80"
    }
  ]
}
[/block]



#### Step 2: Integrate GitHub with JFrog

1. Get a GitHub token.  In GitHub, select **Settings** > **Developer Settings** > **Personal Access Tokens** > **Generate New Token**.
2. Copy the generated token.
3. In JFrog, select **Integrations** > **Add an integration**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0c50956-add-integration.png",
        "add-integration.png",
        1159
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Give the integration a name, select the type and paste the token.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bcbfe69-add-new-integration.png",
        "add-new-integration.png",
        564
      ],
      "sizing": "80"
    }
  ]
}
[/block]



#### Step 3: Integrate NeuraLegion with JFrog

1. Generate an API key (`BRIGHT_TOKEN`) in the [Bright app](https://app.brightsec.com).  Go to **User Settings** > **Create New API Key** > **Select All** > create and copy the token. 
2. In JFrog, select **Integrations** > **Add an integration**.
3. Give the integration a name, select the type and paste the token.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/284efd0-integrate-with-nexploit.png",
        "integrate-with-nexploit.png",
        964
      ],
      "sizing": "80"
    }
  ]
}
[/block]



#### Step 4: Add YAML Pipeline Source

1. In JFrog, select **Pipeline Sources** > **Add Pipeline Source** > **From YAML**.
2. Select your GitHub integration for SCM provider integration, and enter the repository name with JFrog configuration and the branch.
3. Select **Create Source**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4050523-add-source.png",
        "add-source.png",
        667
      ],
      "sizing": "80"
    }
  ]
}
[/block]



You are now ready to build and run a new scan!

#### Step 5: Run a New Scan

In JFrog, select **Pipelines** > **nexploit** > **nexploit** > **Trigger this step**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4548b0e-trigger-this-step.png",
        "trigger-this-step.png",
        1011
      ],
      "sizing": "80"
    }
  ]
}
[/block]



You will then get a view of your current CI process.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c0d8eef-polling-results.png",
        "polling-results.png",
        778
      ],
      "sizing": "80"
    }
  ]
}
[/block]



In the image above, you can see the security scan has started and the results are being polled.

You can now view the security scan status and results in the dashboard in the [Bright app](https://app.brightsec.com). 

On detection of a high severity issue, the build is failed and the scan is stopped automatically.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/551d3d5-breakpoint.png",
        "breakpoint.png",
        1109
      ],
      "sizing": "80"
    }
  ]
}
[/block]



The scanner is set to automatically scan every time there is a change committed in the repository, enabling developers to run an automated, comprehensive and accurate security scan on every commit.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0a02ba4-automatic-scan.png",
        "automatic-scan.png",
        1135
      ],
      "sizing": "80"
    }
  ]
}
[/block]