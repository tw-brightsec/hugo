---
title: "Installation Guide"
slug: "installation-options"
hidden: false
metadata: 
  description: "Each major NeuraLegion version release is accompanied by a correlating NeuraLegion CLI version that supports it."
createdAt: "2021-09-13T09:51:53.740Z"
updatedAt: "2022-11-29T07:54:20.576Z"
---
Each major Bright version release is accompanied by a correlating Bright CLI version that supports it. To enjoy the full functionality of the Bright CLI, we recommend that you periodically check for a new version of the CLI and reinstall it if needed. Thus, you will also avoid potential errors that may be caused by some critical changes issued with a release.

To install the Bright CLI for the first time and reinstall it to update the version, use the installation options given below. For release notes describing the changes in each new version, see [here](https://github.com/NeuraLegion/nexploit-cli/releases).

## Technical requirements

To install the Bright CLI, you will need a local machine with the following specifications:

- System: Ubuntu OS / Windows 8+ / MacOS / Docker 20+
- Processor: x86 or x64 1 core (minimum), 2 core (recommended)
- RAM: 512 MB (minimum), 1 GB (recommended)
- Hard disk: up to 512 MB of available space may be required
- The Docker compose or NodeJS (v10+) installed

## Prerequisites

- Make sure you have the proper access rights to install components on your machine. 
- If you are already using the Bright CLI, but you have decided to use another installation option, please remove the initial Bright CLI service first to avoid possible conflicts of the installers.

## Installation options

- If you a new user, you can install the Bright CLI as part of the onboarding procedure:

[block:html]
{
  "html": "<table>\n <tr>\n  <td>\n   <iframe width=\"100%\" src=\"https://www.youtube.com/embed/6_dD77nrkVY\" \n   title=\"Docker install\" frameborder=\"0\" allow=\"accelerometer; autoplay;       \n   clipboard-write; encrypted-media; gyroscope; picture-in-picture\" \n   allowfullscreen></iframe>\n <br>\n Docker install\n  </td>\n\n  <td>\n   <iframe width=\"100%\" src=\"https://www.youtube.com/embed/fqaeqIWrOTE\" \n   title=\"NPM install\" frameborder=\"0\" allow=\"accelerometer; autoplay; \n   clipboard-write; encrypted-media; gyroscope; picture-in-picture\" \n   allowfullscreen></iframe>\n   <br>\n   NPM install\n  </td>\n\n  <td>\n   <iframe width=\"100%\" src=\"https://www.youtube.com/embed/JmsojpJD5uE\" \n   title=\"Windows install\" frameborder=\"0\" allow=\"accelerometer; autoplay; \n   clipboard-write; encrypted-media; gyroscope; picture-in-picture\" \n   allowfullscreen></iframe>\n   <br>\n   Windows install\n   </td>\n </tr>\n</table>"
}
[/block]



- If you have already created an account, but have not got the Bright CLI installed, you can use one of the options below.

> 👍 Tip
> 
> You can always return to the onboarding wizard and complete the initial setup, including installing the CLI and connecting the Repeater. For that, on the top right of the app, click <img src="https://files.readme.io/8ce3221-help-icon.png" width="23" height="23">, and then select **Repeater setup wizard**.

## Docker

A preconfigured **Repeater Docker** version is available on <https://hub.docker.com/r/neuralegion/repeater> <img src="https://files.readme.io/cb6cc0f-docker.png" width="40" height="40">

> 🚧 Important
> 
> There is a temporary issue when apps started from the Docker containers don't have access to ports of the physical PC where the Docker is started. So as a result the “CONNECTION_ERR” message appears because the Repeater is trying to link by the virtual port, where are no started apps.

There are two ways to interact with the Repeater started from the Docker container, and target apps running on the local machine:

- **The target app is running in a Docker container**  
  In this way, an extra parameter `--network` host should be added. The whole command for launching the dockerized Repeater should be:  
  `docker run -it --network host neuralegion/repeater repeater --id iT2VXTu2W2mqgfAU78bbKr --token YOUR_TOKEN --cluster YOUR_CLUSTER`.
- **The target app is running on a physical port of the local machine outside of the Docker container**  
  To avoid this situation, use the`http://host.docker.internal` target URL Instead of specifying `http://localhost`.



## NPM

> 🚧 Important
> 
> Currently the supported versions of NodeJS are between 10.x and 14.x (included).

To install the CLI using [<img src="https://files.readme.io/8f4b3de-npm.png" width="50" height="23">](https://www.npmjs.com/), run the following command:

```bash
npm install -g @neuralegion/nexploit-cli
```



> 📘 Note
> 
> The installation command may not be supported by some Linux distributions. In this case, you need to download the [installation package](https://github.com/NeuraLegion/nexploit-cli/releases/download/v8.7.0/nexploit-cli-linux-x64) from GitHub and deploy it manually.

More information can be found on [our npm page](https://www.npmjs.com/package/@neuralegion/nexploit-cli).

## Windows installer

To install the CLI using a Windows installer:

1. Go to the [installation page](https://github.com/NeuraLegion/nexploit-cli/releases/latest).
2. Under **Assets**, download the `nexploit-cli.msi` file.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/17e609f-cli-install.png",
        "cli-install.png",
        1763
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Follow the instructions given in the installation wizard.