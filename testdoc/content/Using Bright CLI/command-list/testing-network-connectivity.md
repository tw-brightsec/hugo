---
title: "Testing Network Connectivity"
slug: "testing-network-connectivity"
hidden: false
metadata: 
  description: "Testing Network Connectivity"
createdAt: "2021-09-15T07:13:34.710Z"
updatedAt: "2022-11-09T10:31:37.852Z"
---
This command allows you to detect any connectivity problems when scanning a target hosted on your local network: `nexploit-cli configure`. Also, it can be used to diagnose the connectivity when you run a scan via the local Repeater. This enables you to preliminary check if the Repeater can reach all the local targets. You will be able to reveal and fix the connectivity problems before you run a scan.

The command initializes the network testing wizard. Simply follow the wizard instructions to diagnose the communication between the Repeater and your local targets.  
To run the testing, you will need a valid Repeater ID and an API token with the bot scope. You can get them in the [Bright app](https://app.neuralegion.com):

- To create the Repeater, see [Managing Repeaters](/docs/manage-repeaters).
- To create an API key, see [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens).

To find the connectivity test step-by-step guide, see [Troubleshooting](/docs/repeater-troubleshooting).

## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--traceroute`",
    "0-1": "Provides a full IP trace on a specific target. It means that this option returns a list of all the IPs along the route of the request, thus allowing you to detect the connectivity bottlenecks. You simply need to specify the target hostname or IP address to initialize the diagnostics.  \n  \n**Important:**  \n  \n- _(For Windows users)_. Some Windows users might need to allow the ICMP network traffic through a firewall to enable this option. For the configuration instructions, see the Microsoft docs.  \n- _(For Linux users)_. To enable this option on Linux, you need to apply the `CAP_NET_RAW` and `CAP_NET_ADMIN` capabilities to the `nexploit-cli `or node binary. Once these capabilities are applied to the file, non-root users will be able to run this option. To apply the capabilities, you need to issue the following command:  \n`sudo setcap 'cap_net_admin,cap_net_raw=eip' which node.`  \nFor more information, see [here](https://man7.org/linux/man-pages/man7/raw.7.html).  \n\\`\\`\\`",
    "1-0": "`--ping`",
    "1-1": "Enables testing of the network connectivity on single or multiple targets. You are only required to enter the URL(s) of your internal (local) target application(s) to initialize the diagnostics. Multiple URLs should be separated by commas."
  },
  "cols": 2,
  "rows": 2,
  "align": [
    "left",
    "left"
  ]
}
[/block]