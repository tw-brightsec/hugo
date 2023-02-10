---
title: "SaaS Deployment"
slug: "saas-deployment"
hidden: false
metadata: 
  description: "Using NeuraLegion’s SaaS deployment option is simple. There is no need to install anything locally. \nSimply log in to the NeuraLegion platform and select the target application to be scanned."
createdAt: "2021-08-25T06:50:26.025Z"
updatedAt: "2022-11-29T08:21:03.974Z"
---
## Overview

Using the Bright SaaS deployment option is simple. There is no need to install anything locally.  
Simply log in to the [Bright app](https://app.brightsec.com) and select the target application to be scanned. 

## How the SaaS deployment works

The Bright cloud engines begin scanning the target for issues. Reports that show identified issues start displaying immediately, with no false positives.  
The standard SaaS solution uses a multi-tenant architecture for the databases and static network configurations.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d83604b-SaaS_2.png",
        "SaaS (2).png",
        791
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Before you begin

Before scanning, ensure that:

- The target application can be accessed from the Internet.
- Bright static IP (see below) is allowlisted by your WAF/firewall (recommended in order to avoid adding into blocked list of Bright solutions).

> 🚧 Important
> 
> Bright has the following public static IPs:  
> **U.S.** – **54.205.119.224**  
> **Europe** – **54.75.37.42**

## Deployment platforms

Currently, deployment is only possible on AWS. Deployment to other cloud vendors can be added, if needed, for specific scenarios. Bright fully manages the deployment process for you.

If you are interested in other deployment options, contact our sales team.