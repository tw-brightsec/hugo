---
title: "Troubleshooting Repeater"
slug: "repeater-troubleshooting"
excerpt: "The purpose of this section is to help you solve common problems that you may encounter while using the Repeater."
hidden: false
metadata: 
  description: "In order to use a Repeater from within a local network, you must first make sure it has a proper access to all the target applications."
createdAt: "2021-09-15T11:18:12.766Z"
updatedAt: "2022-12-08T13:11:40.927Z"
---
## Connectivity test

In order to scan a target on a local network in the Repeater mode, you first need to make sure that a registered (created) Repeater has a proper access to the target.  
You can use the `nexploit-cli configure` command to run a simple connectivity testing process.

### Prerequisites

- The machine on which the Repeater will be run must have the latest version of the [Bright CLI](/docs/installation-options).
- A valid API key (`Repeater API Token`) with the following scopes: `bot`, `scans:run`, `scans:read`, `scans:stop`.  
  You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens).
- A valid `Repeater ID`. To register (create) the Repeater, see [Managing Repeaters](/docs/manage-repeaters).

### Step-by-step guide

1. Run the command `nexploit-cli configure` in your console.  
   The Bright Network Testing wizard is launched.

2. Enter your `Repeater ID` and `Repeater API Token` in the relevant fields.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/54fbe11-Group_1316.png",
        "Group 1316.png",
        1114
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. The CLI runs the first stage of the external communication diagnostics:

   - **Validating that the connection to amq.app.brightsec.com:5672 at port 5672 is open** is required for the Repeater to reach the scan engine.
   - **Validating that the connection to app.brightsec.com at port is open** is required to reach the Bright API endpoints.
   - **Verifying provided Token and Repeater ID** is required to validate the credentials.

   The diagnostics results are provided next to the validation parameters. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/be58f5b-external-diagnostics.png",
        "external-diagnostics.png",
        888
      ],
      "sizing": "80"
    }
  ]
}
[/block]



        Once the external communication diagnostics is completed, the CLI switches to the validation of the Repeater         communication with local target application(s).

4. Enter the target URL(s) to test if the Repeater can reach them.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0b2fe1b-internal-testing.png",
        "internal-testing.png",
        803
      ],
      "sizing": "80"
    }
  ]
}
[/block]



        The internal communication diagnostics starts, and the Repeater tries to reach the specified applications. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/794808e-internal-diagnostics.png",
        "internal-diagnostics.png",
        711
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. Once the diagnostics is completed, you can see how many targets cannot be reached by the Repeater.  
   To exit the wizard, close the console.