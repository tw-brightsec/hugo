---
title: "Checking Scan Status"
slug: "checking-scan-status"
hidden: false
metadata: 
  description: "After a scan launches, it frequently checks the scan status. If the scan finds at least of one issue of medium severity, Nexploit CLI finishes with exit code 50."
createdAt: "2021-09-15T06:35:04.702Z"
updatedAt: "2022-12-08T12:42:59.864Z"
---
This command configures ongoing polling of a scan status, and helps you follow its progress during CI/CD flows: `nexploit-cli scan:polling [options] <scan>`

After a scan launches, it frequently checks the scan status. If the scan finds at least one issue of medium severity, Bright CLI finishes with exit code 50.

## Arguments

| Argument | Description                                        |
| :------- | :------------------------------------------------- |
| `<scan>` | The ID of an existing scan that you want to check. |

## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--token=apiKey`, `-t=apiKey`",
    "0-1": "The unique identifier used to authenticate a user. The token (API key) can be issued in your organization’s dashboard.",
    "1-0": "`--breakpoint=any/ medium_issue/high_issue`,  \n`-b=any/medium_issue/high_issue`",
    "1-1": "A conditional breakpoint that finishes the process with exit code 50 only after fulfilling the predefined condition. The breakpoint option allows you to follow the fail-fast principle when polling the scan results.  \n  \n**Default:** `--breakpoint any`",
    "2-0": "`--interval=milliseconds`",
    "2-1": "The period of time between the end of a timeout period or the completion of a scan status request, and the next request for status. For example, 60, 2min, 10h, or 7d. A numeric value is interpreted in milliseconds.  \n  \n**Default:** `--interval 5000`",
    "3-0": "`--timeout=milliseconds`",
    "3-1": "The maximum time allowed for polling to end normally. For example, 60, 2min, 10h, or 7d. A numeric value is interpreted in milliseconds.",
    "4-0": "`--config=pathToConfig`",
    "4-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the config in the`package.json` in the root directory of your application or a separate file by a specified name in the working directory. For details, see [Configuration Files](https://docs.brightsec.com/docs/configuration-files) for more information.",
    "5-0": "`--log-level\n=0/1/2/3/4/silent/\n`  \n`error/warn/notice/verbose`",
    "5-1": "Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", and \"verbose\".  \n  \n**Default:** 3",
    "6-0": "`--cluster`",
    "6-1": "Bright cluster (domain name).  \n  \n**Default:**`<https://app.brightsec.com`>",
    "7-0": "`--insecure`",
    "7-1": "Allows the Bright CLI to proceed and operate even if the server connection is considered insecure.",
    "8-0": "`--proxy=socksProxyUrl`",
    "8-1": "SOCKS URL to proxy all traffic.  \n  \n**Note:** SOCKS4, SOCKS5, SOCKS4a, and SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.",
    "9-0": "`--api=clusterUrl`",
    "9-1": "**(Deprecated)**. Set the API endpoint domain, for VPC, use: --api <https://private-domain.brightsec.com>  \n  \n**Default:**` --api <https://app.brightsec.com`>"
  },
  "cols": 2,
  "rows": 10,
  "align": [
    "left",
    "left"
  ]
}
[/block]