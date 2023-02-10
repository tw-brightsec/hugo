---
title: "CircleCI"
slug: "circleci"
hidden: false
metadata: 
  description: "Although it is possible to configure a CI pipeline with our REST API, it is recommended to use our NeuraLegion CLI for an easier, more robust configuration of your pipeline."
createdAt: "2021-09-16T08:24:41.821Z"
updatedAt: "2022-11-30T07:02:35.659Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/20283ed-circleci-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    You can configure your CircleCI pipeline to automatically run a Bright scan with every new build. Once a build is made to the pipeline, Bright initiates security tests and provides all the information that developers need to fix the detected vulnerabilities, without having to leave their development environment.\n    </td>\n  </tr>\n<tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    Although it is possible to configure a CI pipeline with the <a href=https://app.brightsec.com/api/v1/docs/>Bright REST API</a>, it is recommended to use the <a href=/docs/about-bright-cli>Bright CLI</a> for an easier, more robust configuration of your pipeline.\n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



For this guide, we are using an intentionally vulnerable benchmark application called [Broken Crystals](https://brokencrystals.com/) and a preconfigured YAML file to set up a CircleCI workflow. 

## Prerequisites

To configure security testing for your CircleCI pipeline, you will need to have a few things in place:

- You have an active [GitHub account](https://github.com/).
- You have an active [CircleCI account](https://circleci.com/signup).

## Step-by-step guide

We will run an initial security scan using Bright against the target, where CircleCI will break the build as per our configuration and the results can be viewed for remediation. The [code repository](https://github.com/olga-demidko/example-actions/tree/circleci-project-setup) for this example contains a publicly available CircleCI YAML configuration file. This runs a scan against an intentionally vulnerable benchmark application called [Broken Crystals](https://brokencrystals.com/). You can use this target as a test project. The YAML file contains the configuration for the security scanning and execution steps.

#### Step 1. Configure a workflow

Configure a YAML file in your GitHub repository that will be integrated with your CircleCI project, or create a configuration file directly in the GircleCI project. You can use our CircleCI YAML configuration file as an example.

1. Install the NodeJS and Bright CLI so you can use the Bright API to run, poll status, and stop scans.

```shell
steps:
      - checkout
      - run:
          name: Install NodeJS and bright-cli
          environment:
            DEBIAN_FRONTEND: 'noninteractive'
          command: |
            apt -y update
            apt-get -y install libnode-dev node-gyp libssl-dev
            apt-get -y install nodejs npm
            npm install -g @neuralegion/nexploit-cli --unsafe-perm=true
```



2. Proceed to scanning. The following command starts a scan once a commit is pushed to the pipeline.

```shell
- run:
          name: Start Bright Scan 🏁
          command: |
            SCAN_ID=$(bright-cli scan:run                                                 \
            --test csrf dom_xss xss header_security secret_tokens open_buckets                 \
            --name "💎 BrokenCrystals for CircleCI" \
            --crawler https://brokencrystals.com/  \
            --token $BRIGHT_TOKEN)
            printf "Scan id is: $SCAN_ID"
            echo "export SCAN_ID=\"$SCAN_ID\"" >> $BASH_ENV
            
      - run:
          name: Output scan URL
          command: |
            printf "Scan was started with ID https://app.neuralegion.com/scans/${SCAN_ID}"
```



  You need to give a name for the scan, specify the discovery type (for us, it’s a crawler with the target URL). If you want to use a .HAR file or an OpenAPI schema for the scan, you will need to upload the file to the Bright app storage in advance and copy the generated ID.

  In our configuration, we are also specifying the tests that will be applied to the target and the authorization token that was already set as an environment variable. 

  After the scan is started, the scan ID is generated.  This ID can then be used to re-run the scan as well as to check the scan results in the Bright app.

3. After the scan is started, we need to poll the scan status until it returns a detected issue. This is enabled by the following command:

```shell
- run:
          name: Wait for issues ⏳
          command: |
            nexploit-cli scan:polling               \
            --interval 30s                        \
            --timeout 10m                         \
            --token $BRIGHT_TOKEN               \
            --breakpoint high_issue ${SCAN_ID}
```



  The “Wait for issues” command allows you to follow the “fail-fast” approach by interrupting the build with the first issue found. Moreover, you can set the severity of the first issue to wait for using the `--breakpoint` option. In our example, it is set to `high_issue`, meaning that the build will stop automatically if a high severity issue is found. You will also be able to manage the polling frequency and entire duration by specifying the request interval (for us, it is 30 seconds) and timeout (10 minutes) respectively. The scan will stop upon the timeout expiration if no issue of the specified severity level is detected so far.

#### Step 2.  Integrate GitHub with CircleCI

Probably the most simple process, there are no plugins to install and integration really is out-of-the-box. Simply sign in to CircleCI with your GitHub account, and CircleCI mirrors your GitHub team permissions and privileges, so you can start building right away. CircleCI automatically runs your build and test processes whenever you commit code in GitHub.

#### Step 3. Set environment variables for the CircleCI project

1. In CircleCI, navigate to your **Projects** and select the repository you would like to integrate with automated testing.
2. On the selected project page, click **Project Settings**:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3ff2306-d45372e1-a115-477d-af46-c7cb168bab13.png",
        "d45372e1-a115-477d-af46-c7cb168bab13.png",
        1898
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. From the left menu, select **Environment Variables**, and then click **Add Environment Variable**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3aca85f-d9837d74-3003-4e73-abe5-a6e762946fa4.png",
        "d9837d74-3003-4e73-abe5-a6e762946fa4.png",
        1908
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Add the variables you need for the configuration. For our example, we need the following variables: 

- `BRIGHT_TOKEN` - a token (key) required to use the Bright API. To learn how to get the value of an API key in the Bright app, read [Manage Your Organization](https://docs.neuralegion.com/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [Manage Your Personal Account](https://docs.neuralegion.com/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens).
- `REPEATER` - a local agent that provides a secure connection between the Bright cloud engine and a target on a local network. The value of this variable is the ID generated upon [Creating a Repeater](/docs/manage-repeaters#create-a-new-repeater) in the Bright app.

#### Step 4. Push a commit to initiate a security scan

Your next commit will initiate a workflow and build with CircleCI. Bright will run a security scan against that commit.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/df135e5-running-scan.png",
        "running-scan.png",
        1579
      ],
      "sizing": "80"
    }
  ]
}
[/block]



As specified in the configuration file, the environment is spun up, the environment variables are prepared, a new Bright security scan is started against the target, and we are polling for results.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ad91175-started-polling.png",
        "started-polling.png",
        1544
      ],
      "sizing": "80"
    }
  ]
}
[/block]



After a short time, Bright will find a high-level issue. As we specified in the configuration file when this breakpoint is met, the build fails and the scan is set to stop. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6b3eefe-breakpoint-high.png",
        "breakpoint-high.png",
        1513
      ],
      "sizing": "80"
    }
  ]
}
[/block]



#### Step 5. Check the results

We can now look at the security scan status and results using the Bright dashboard to check the status.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d9a14b9-circleci-scan-status.png",
        "circleci-scan-status.png",
        1901
      ],
      "sizing": "80"
    }
  ]
}
[/block]



The scanner has already detected a number of automatically validated security issues on the target, ready to be fixed, without the need for any manual validation.

The results provide the developers with the information they need to understand the issue, how to replicate it, and how to fix it, with remediation guidelines.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b647f19-issue-overview.png",
        "issue-overview.png",
        1899
      ],
      "sizing": "80"
    }
  ]
}
[/block]