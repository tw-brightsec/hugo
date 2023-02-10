---
title: "Adding an Authentication Object to a Scan"
slug: "adding-your-authentication-object-to-a-scan"
hidden: false
metadata: 
  description: "When starting a new scan, you can select any of the authentication objects that you have created previously in the NeuraLegion App."
createdAt: "2021-09-03T09:37:49.129Z"
updatedAt: "2022-09-14T09:21:50.892Z"
---
When [starting a new scan](/docs/creating-a-new-scan), you can select any of the authentication objects that you have created previously in the Bright app. This will allow the Bright engine to perform the re-authentication automatically during the scan.

You can apply either the DAST or Fuzzer module, as well as all the discovery types for the scans with connected authentication objects. 

## Prerequisites

- You have a valid [Authentication Object](/docs/creating-an-authentication-object-in-nexploit) configured.

## Step-by-step guide

1. In the **Application Settings** tab, select **Authentication object**.
2. From the **Authentication** dropdown list, select the required object.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b0c5da3-select-auth-object.png",
        "select-auth-object.png",
        1089
      ],
      "sizing": "80"
    }
  ]
}
[/block]