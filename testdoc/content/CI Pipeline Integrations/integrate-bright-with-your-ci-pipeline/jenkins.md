---
title: "Jenkins"
slug: "jenkins"
hidden: false
metadata: 
  description: "You can run fast scans of the application which is currently under development within your pipeline."
createdAt: "2021-09-16T09:12:27.205Z"
updatedAt: "2022-12-08T13:23:58.749Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n     \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/d789574-jenkins-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n    <p>If you are using the Jenkins pipeline for development automation, you can integrate it with Bright to run security scans on every new build within your development environment.<p></p>\n    Depending on the use case, you can apply multiple options for running scans from your CI pipeline. \n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



## Use cases

### Scanning a target in a private environment

You can run fast scans of the application which is currently under development within your pipeline. Bright allows you to follow the fail-fast principle by interrupting a scan automatically at the first detected vulnerability. Using this option, you are able to quickly and timely find and fix the security issues at the build level without delaying the whole development process.

As the scan target is closed within your pipeline, the Bright engine cannot access it directly from the cloud. In this case, you can use a [Repeater](/docs/on-premises-repeater-local-agent) which serves as a request-proxy between Bright and a scan target inside your private environment.  You should first register (create) the Repeater in the [Bright app](https://app.brightsec.com), and then connect it to your pipeline using the generated Repeater ID. 

To run scans directly from your pipeline, you need to install the Bright CLI. It provides an easy-to-use interface and multiple [commands](/docs/command-list) you can use in your Jenkins flow. 

You can either run the Bright CLI with a Repeater using the NPM or by installing the Bright's Docker image inside your pipeline.  

  Find the examples here: 

- [Scanning in the Repeater  using the NPM](/docs/jenkins-integration-examples#example-2-scanning-via-a-repeater-using-the-nexploit-cli-npm-installation)
- [Scanning in the Repeater mode using the Docker image](/docs/jenkins-integration-examples#example-3-scanning-via-a-repeater-using-the-nexploit-cli-docker-installation)

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



<img src="https://files.readme.io/6b876c4-jenkins-npm.png" width="480" height="410">

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



### Scanning a target in public environment

 Upon a release of a new build, you can run an overall complete scan of the target in the production or public pre-production environment. In this case, long scans will not interfere with the development process as compared to scanning in a private environment.  

 Depending on the access to the deployed target, you can run a scan using multiple options.

- If the scan target is accessible from the Internet:<br>  
  <img src="https://files.readme.io/cc0813a-1.png" width="36" height="30"> Directly from the [Bright app](https://app.brightsec.com)  
  <img src="https://files.readme.io/112f601-2.png" width="34" height="30"> From your pipeline using the Bright CLI (NPM). Find the example [here](/docs/jenkins-integration-examples#example-1-direct-scanning-using-the-nexploit-cli-npm-installation). 

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
        "https://files.readme.io/4f239fd-jenkins-direct_1.png",
        "jenkins-direct (1).png",
        1701
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



- If the scan target has private access (or if you want to scan specific local microservices), you can use a [Repeater](/docs/on-premises-repeater-local-agent) (scan proxy) to ensure secure communication between the Bright engine and the scan target. In this case, you can only control scanning via the Bright CLI which can be installed using either <img src="https://files.readme.io/baaa6c4-3.png" width="36" height="30"> the NPM or <img src="https://files.readme.io/133d01b-4.png" width="36" height="29"> the Docker image.

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



<img src="https://files.readme.io/f18a509-jenkins-docker_2.png" width="410" height="410">

[block:html]
{
  "html": "<p>&nbsp;</p>"
}
[/block]



Find the examples here:

- [Scanning in the Repeater mode using the NPM](/docs/jenkins-integration-examples#example-2-scanning-via-a-repeater-using-the-nexploit-cli-npm-installation)
- [Scanning in the Repeater mode using the Docker image](/docs/jenkins-integration-examples#example-3-scanning-via-a-repeater-using-the-nexploit-cli-docker-installation)