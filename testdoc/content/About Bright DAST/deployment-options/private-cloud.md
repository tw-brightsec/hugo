---
title: "Private Cloud Deployment"
slug: "private-cloud"
hidden: false
metadata: 
  description: "Unlike the standard SaaS offering that uses a multi-tenant architecture for the databases and static network configurations, the Private Cloud provides a completely separate, configurable cloud environment for your organization."
createdAt: "2021-08-25T07:18:28.156Z"
updatedAt: "2022-09-12T18:27:29.157Z"
---
## Overview

Unlike the standard SaaS offering that uses a multi-tenant architecture for the databases and static network configurations, the Private Cloud provides a completely separate, configurable cloud environment for your organization.

> 📘 Note
> 
> The private cloud instance is hosted on the Bright infrastructure.

The Private Cloud’s separate, non-multi-tenant environment offers the following benefits over a standard SaaS environment: 

- Separate databases at the instance level. Standard SaaS only accommodates some databases at a logical level.
- Full control over network-level configurations, such as:
  - Load handling.
  - Network-level access configurations (IP allow/deny).
  - Options for site-to-site VPN setup.
- Improved security in lateral-movement scenarios.

## How the private cloud deployment works

All relevant components, which may include sensitive information, such as databases, engines and so on, are deployed in a separate cloud instance that is managed by Bright. 

## Deployment platforms

Currently, the Private Cloud is deployed on AWS. Deployment to other cloud vendors can be added, as needed. Bright fully manages the deployment process for you.

If you are interested in other deployment options, contact your sales representative.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9339631-private-cloud_2.png",
        "private-cloud (2).png",
        792
      ],
      "sizing": "80"
    }
  ]
}
[/block]