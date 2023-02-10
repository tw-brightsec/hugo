---
title: "Travis CI"
slug: "travis-ci"
hidden: false
createdAt: "2022-07-14T19:49:22.041Z"
updatedAt: "2022-12-08T13:19:03.266Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n    <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/47244d6-travis-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    Travis CI is a Continuous Integration / Continuous Delivery (CI/CD) platform that enables developers to quickly and easily build, test and deploy code. The easy-of-use and flexibility offered by Travis CI is core to software development as part of a modern DevOps toolchain. Travis CI supports the development process by automatically building and testing code changes in smaller increments, providing immediate feedback on the success of the change.</p>\n     </td>\n  </tr>\n <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    Depending on the use case, you can apply multiple options for running scans from your CI pipeline.\n    </td>\n  </tr>\n  </table>\n<body>"
}
[/block]



## To get started with Travis CI using Github

1. Go to [Travis CI](https://www.travis-ci.com) and Sign up with Github.   
2. Click on your profile picture on top right corner, click Settings and then Activate green button. After that choose GitHub repositories you want to use with Travis CI or select all repositories.
3. Add a .travis.yml file to your repository to tell Travis CI what to do.

## Configure and build a scan

**Prerequisites:**

1. Make a valid organization or personal **API key** (NEXPLOIT_TOKEN) with all or following scopes: **bot, scans : run, scans : read, scans : stop.** 

2. Create NEXPLOIT_TOKEN variable on your Travis CI machine:  
   \_More options > Settings > Add Environment Variables._

![](https://files.readme.io/01dc18a-1.png "1.png")

Configure a .travis.yml file:

![](https://files.readme.io/4b2db15-2.png "2.png")

Add the .travis.yml file to your repository branch and commit to trigger a Travis CI build:

![](https://files.readme.io/d1f8b2a-3.png "3.png")

 The scan is configured to stop when a medium issue is detected.

 Monitoring the scan progress and checking issues:

![](https://files.readme.io/aaaeafc-4.png "4.png")

## Configure and build a scan with the repeater

**Prerequisites:**

1. Make a valid organization or personal **API key** (NEXPLOIT_TOKEN) with all or following scopes: **bot, scans : run, scans : read, scans : stop.**

2. Make the Repeater with a valid ID “REPEATER”.

3. Create the NEXPLOIT_TOKEN and REPEATER variable on your Travis CI machine: \_More options > Settings > Add Environment Variables._

![](https://files.readme.io/2c06476-5.png "5.png")

Configure the .docker-compose.yml file.  
Add a .docker-compose.yml file to your repository on another branch and commit the file:

![](https://files.readme.io/605c7a0-6.png "6.png")

Configure .travis.yml file:

![](https://files.readme.io/37bc8e4-7.png "7.png")

Add the .travis.yml file to your same repository branch and commit to trigger a Travis CI build:

![](https://files.readme.io/849c604-8.png "8.png")

Monitoring the scan progress and checking issues:

![](https://files.readme.io/b2831d0-9.png "9.png")

The scan is configured to stop when a medium issue is detected.

## Use Cases

### Scanning a target in private environment

You can run fast scans of the application which is currently under development within your pipeline. Bright allows you to follow the fail-fast principle by interrupting a scan automatically at the first detected vulnerability. Using this option, you are able to quickly and timely reveal and fix the security issues at the build level without delaying the whole development process.

As the scan target is closed within your pipeline, the Bright engine cannot access it directly from the cloud. In this case, you can use a [Repeater](/docs/on-premises-repeater-local-agent) which serves as a request-proxy between Bright and a scan target inside your private environment.  You should first register (create) the Repeater in the [Bright app](https://app.brightsec.com), and then connect it to your pipeline using the generated Repeater ID. 

To run scans directly from your pipeline, you need to install the Bright CLI. It provides an easy-to-use interface and multiple [commands](/docs/command-list) you can use in your Travis flow.   

You can either run the Bright CLI with the Repeater using the NPM or by installing the Bright's Docker image inside your pipeline. 

Find the examples here: 

- [Scanning in the Repeater mode using the NPM](/docs/travis-ci-integration-examples#example-2-scanning-via-a-repeater-using-the-nexploit-cli-npm-installation)
- [Scanning in the Repeater mode using the Docker image](/docs/travis-ci-integration-examples#example-3-scanning-via-a-repeater-using-the-nexploit-cli-docker-installation)

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



<img src="https://files.readme.io/64d3f1d-travis-repeater_2.png" width="480" height="410">

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



### Scanning a target in public environment

 Upon a release of a new build, you can run a complete scan of the target in the production or public pre-production environment. In this case, long scans will not interfere with the development process as compared to scanning in the private environment.  

 Depending on the access to the deployed target, you can run a scan using multiple options.

- If the scan target is accessible from the Internet:<br>  
  <img src="https://files.readme.io/cc0813a-1.png" width="36" height="30"> Directly from the [Bright app](https://app.brightsec.com)  
  <img src="https://files.readme.io/112f601-2.png" width="34" height="30"> From your pipeline using the Bright CLI (NPM implementation). Find the example [here](/docs/travis-ci-integration-examples#example-1-direct-scanning-using-the-nexploit-cli-npm-installation).

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/353711e-travis-direct_1.png",
        "travis-direct (1).png",
        1827
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



- If the scan target has a private access (or if you want to scan specific local microservices), you can use a [Repeater](/docs/on-premises-repeater-local-agent) (scan proxy) to ensure secure communication between Bright and the scan target. In this case, you can only control scanning via the Bright CLI, which can be installed using either <img src="https://files.readme.io/baaa6c4-3.png" width="36" height="30"> the NPM or <img src="https://files.readme.io/133d01b-4.png" width="36" height="29"> the Docker image.

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



<img src="https://files.readme.io/80692b8-travis-repeater_3.png" width="480" height="410">

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



Find the examples here:

- [Scanning in the Repeater mode using the NPM](/docs/travis-ci-integration-examples#example-2-scanning-via-a-repeater-using-the-nexploit-cli-npm-installation)
- [Scanning in the Repeater mode using the Docker image](/docs/travis-ci-integration-examples#example-3-scanning-via-a-repeater-using-the-nexploit-cli-docker-installation)