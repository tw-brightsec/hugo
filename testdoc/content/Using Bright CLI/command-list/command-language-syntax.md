---
title: "Command Language Syntax"
slug: "command-language-syntax"
hidden: false
metadata: 
  description: "The NeuraLegion CLI accepts a wide variety of configuration options. You can run ```nexploit-cli --help``` command for comprehensive documentation."
createdAt: "2021-09-13T10:30:32.082Z"
updatedAt: "2023-01-04T12:37:10.413Z"
---
The Bright CLI accepts a wide variety of configuration options. You can run `nexploit-cli --help` command for comprehensive documentation. The configuration options and arguments in the command line must be passed after the program command that the Bright CLI is executing.

```bash
 nexploit-cli <command> [option] [<argument>]
```



- Most commands and some options have aliases. Aliases are shown in the syntax statement for each command.
- The option names are prefixed with a double dash (--). The option aliases are prefixed with a single dash (-). Arguments are not prefixed. 
- Support is provided for an array of options of a specific command, separated by a space. For example:

```bash
  nexploit-cli scan:run --token API_KEY --name SCAN_NAME --crawler TARGET_URL --param path query body --test default_login_location dom_xss sqli 
```



The Bright CLI provides the following global options that can affect the behavior of each command:

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--config=pathToConfig`",
    "0-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the config in package.json in the root directory of your application or a separate file by a specified name in the working directory.  \n  \nSee [Configuration Files](https://docs.brightsec.com/docs/configuration-files) for more information.",
    "1-0": "`--log-level\n=0/1/2/3/4/silent/\nerror/warn/notice/verbose`",
    "1-1": "Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", \"verbose\".  \n  \n**Default:** 3",
    "2-0": "`--cluster`",
    "2-1": "Bright cluster (domain name).  \n  \n**Default:**`<https://app.brightsec.com`>",
    "3-0": "`--insecure`",
    "3-1": "Allows the Bright CLI to proceed and operate even if the server connection is considered insecure.",
    "4-0": "`--proxy=socksProxyUrl`",
    "4-1": "SOCKS URL to proxy all traffic.  \n  \n**Note:** SOCKS4, SOCKS5, SOCKS4a, SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.",
    "5-0": "`--version, -v`",
    "5-1": "Shows the Bright CLI version.",
    "6-0": "`--help, -h`",
    "6-1": "Shows the Bright CLI help documentation."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]