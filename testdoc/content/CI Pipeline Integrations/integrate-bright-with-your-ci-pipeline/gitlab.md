---
title: "GitLab"
slug: "gitlab"
hidden: false
metadata: 
  description: "You can run fast scans of the application which is currently under development within your pipeline. NeuraLegion allows you to follow the fail-fast principle by interrupting a scan automatically at the first detected vulnerability."
createdAt: "2021-09-16T11:10:22.123Z"
updatedAt: "2022-10-11T17:33:41.919Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/2736cff-gitlab-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    If you are using the GitLab pipeline for development automation, you can integrate it with Bright to run security scans on every new build within your development environment.</p>\n       </td>\n  </tr>\n<tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    Depending on the use case, you can apply multiple options for running scans from your CI pipeline.\n    </td>\n  </tr>\n  </table>\n</body>"
}
[/block]



## Use Cases

### Scanning a target in private environment

You can run fast scans of the application which is currently under development within your pipeline. Bright allows you to follow the fail-fast principle by interrupting a scan automatically at the first detected vulnerability. Using this option, you are able to quickly and timely find and fix the security issues at the build level without delaying the whole development process.

As the scan target is closed within your pipeline, Bright engine cannot access it directly from the cloud. In this case, you can use a [Repeater](/docs/on-premises-repeater-local-agent) which serves as a request-proxy between Bright and a scan target inside your private environment.  You should first register (create) the Repeater in the [Bright app](https://app.neuralegion.com), and then connect it to your pipeline using the generated Repeater ID. 

To run scans directly from your pipeline, you need to install the Bright CLI. It provides an easy-to-use interface and multiple [commands](/docs/command-list) you can use in your Travis flow. 

You can either run the Bright CLI with a Repeater using the NPM or by installing the Bright's Docker image inside your pipeline. 

Find the examples here: 

- [Scanning in the Repeater mode using the NPM](/docs/gitlab-integration-examples#example-2-scanning-via-a-repeater-using-the-nexploit-cli-npm-installation)
- [Scanning in the Repeater mode using the Docker image](/docs/gitlab-integration-examples#example-3-scanning-via-a-repeater-using-the-nexploit-cli-docker-installation)

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



<img src="https://files.readme.io/c17f0ae-gitlab-repeater_2.png" width="470" height="410">

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



### Scanning a target in public environment

 Upon a release of a new build, you can run an overall complete scan of the target in the production or public pre-production environment. In this case, long scans will not interfere with the development process as compared to scanning in the private environment.  

 Depending on the access to the deployed target, you can run a scan using multiple options.

- If the scan target is accessible from the Internet:<br>  
   <img src="https://files.readme.io/cc0813a-1.png" width="34" height="30"> Directly from the [Bright app](https://app.neuralegion.com)  
  <img src="https://files.readme.io/112f601-2.png" width="32" height="30"> From your pipeline using the Bright CLI (NPM). Find the example [here](/docs/gitlab-integration-examples#example-1-direct-scanning-using-the-nexploit-cli-npm-installation). 

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
        "https://files.readme.io/4123439-gitlab-direct_2.png",
        "gitlab-direct (2).png",
        1435
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



- If the scan target has a private access (or if you want to scan specific local microservices), you can use a [Repeater](/docs/on-premises-repeater-local-agent) to ensure secure communication between Bright and the target. In this case, you can control scanning  only via the Bright CLI which can be installed using either <img src="https://files.readme.io/baaa6c4-3.png" width="36" height="30"> the NPM or <img src="https://files.readme.io/133d01b-4.png" width="36" height="29"> the Docker image.

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



<img src="https://files.readme.io/7360695-gitlab-docker_1.png" width="470" height="410">

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



Find the examples here:

- [Scanning in the Repeater mode using the NPM](/docs/gitlab-integration-examples#example-2-scanning-via-a-repeater-using-the-nexploit-cli-npm-installation)
- [Scanning in the Repeater mode using the Docker image](/docs/gitlab-integration-examples#example-3-scanning-via-a-repeater-using-the-nexploit-cli-docker-installation)