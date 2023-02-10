---
title: "Stopping a Scan"
slug: "stopping-a-scan"
hidden: false
metadata: 
  description: "Stopping a Scan"
createdAt: "2021-09-15T06:43:18.531Z"
updatedAt: "2022-12-08T12:42:09.676Z"
---
This command stops a scan by its ID: `nexploit-cli scan:stop [options] <scan id>`.

## Arguments

| Argument    | Description                                      |
| :---------- | :----------------------------------------------- |
| `<scan id>` | The ID of an existing scan that you want to stop |

## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--token=apiKey`, `-t=apiKey`",
    "0-1": "The unique identifier used to authenticate a user. The token (API key) can be issued in your organization’s dashboard.",
    "1-0": "`--config=pathToConfig`",
    "1-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the config in the `package.json` in the root directory of your application or a separate file by a specified name in the working directory. For details, see [Configuration Files](https://docs.brightsec.com/docs/configuration-files) for more information.",
    "2-0": "`--log-level\n=0/1/2/3/4/silent/\n`  \n`error/warn/notice/verbose`",
    "2-1": "Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", and \"verbose\".  \n  \n**Default:** 3",
    "3-0": "`--cluster`",
    "3-1": "Bright cluster (domain name).  \n  \n**Default:**`<https://app.brightsec.com`>",
    "4-0": "`--insecure`",
    "4-1": "Allows the Bright CLI to proceed and operate even if the server connection is considered insecure.",
    "5-0": "`--proxy=socksProxyUrl`",
    "5-1": "SOCKS URL to proxy all traffic.  \n  \n**Note:** SOCKS4, SOCKS5, SOCKS4a, and SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.",
    "6-0": "`--api=clusterUrl`",
    "6-1": "**(Deprecated)**. Set the API endpoint domain, for VPC, use: --api <https://private-domain.brightsec.com>  \n  \n**Default:**` --api <https://app.brightsec.com`>"
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]