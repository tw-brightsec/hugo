---
title: "Integrating with an On-Premise Ticketing Service"
slug: "integrating-with-a-service"
hidden: false
metadata: 
  description: "Integrating with a Service"
createdAt: "2021-09-15T07:18:03.077Z"
updatedAt: "2022-11-09T11:50:32.681Z"
---
This command that connects Bright with a ticketing service deployed on a local server (currently only the On-Premise Jira is supported): `nexploit-cli integration [options]`. The repositories of the connected service can then be integrated with the Bright projects to be used as endpoints for scan reports (details of detected security vulnerabilities).

For more information about the integration capabilities, see [Ticketing Integrations](/docs/integrate-nexploit-with-your-ticketing-system).

**Script Example**

```shell
nexploit-cli integration --access-key $INTEGRATION_ACCESS_KEY --base-url https://your-cluster.atlassian.net --user $USERNAME --password $PASSWORD --token $API_TOKEN
```



> 📘 Notes
> 
> - Sample variables are marked with a `$`. You must substitute them for your real values.
> - If your Jira username or password includes any special characters (for example, "pa$$word"), enclose the entire username or password in single quotes.

## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--cluster`",
    "0-1": "Bright cluster (domain name).  \n  \n**Default:** `https://app.neuralegion.com`",
    "1-0": "`--access-key=integrationKey`",
    "1-1": "The unique identifier generated in the Jira integration config dialog box in the Bright app.  \nRequired to authorize Bright in the On-Premise Jira (local Jira Server).",
    "2-0": "`--type=jira`",
    "2-1": "Integration service type (currently only JIRA is supported)",
    "3-0": "`--base-url=serviceUrl`",
    "3-1": "Base URL to the Jira instance API",
    "4-0": "`--user=serviceUserName`",
    "4-1": "Your username for a local Jira Server or email for the Atlassian Jira Cloud",
    "5-0": "`--password=serviceUserPassword`",
    "5-1": "Your password for a local Jira Server or Jira API token for the Atlassian Jira Cloud",
    "6-0": "`--token=apiKey`, `-t=apiKey`",
    "6-1": "Bright [organization API key](https://docs.brightsec.com/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](https://docs.brightsec.com/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) with the bot scope.  \nThe botscope enables a connection between Bright and Bright CLI.",
    "7-0": "`--daemon`, `-d`",
    "7-1": "Runs the integration in a daemon mode",
    "8-0": "`--config=pathToConfig`",
    "8-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the configuration in the`package.json` in the root directory of your application or a separate file by a specified name in the working directory. See [Configuration Files](https://docs.brightsec.com/#/guide/np-cli/configuration-files.md) for more information.",
    "9-0": "`--log-level =0/1/2/3/4/silent/  `  \n`error/warn/notice/verbose`",
    "9-1": "Allows setting a level of logs for reports. Bright will only show the logs of a level higher than the one specified. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", and \"verbose\".  \n  \n**Default:** 3",
    "10-0": "`--insecure`",
    "10-1": "Allows the Bright CLI to continue working even if the server connection is considered insecure.",
    "11-0": "`--proxy=socksProxyUrl`",
    "11-1": "SOCKS URL to proxy all traffic.  \n  \n**Note:** SOCKS4, SOCKS5, SOCKS4a, SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.",
    "12-0": "`--bus=eventBusUrl`",
    "12-1": "**(Deprecated)**. Bright event bus URL.  \n  \n**Default:** `--bus amqps://amq.app.neuralegion.com:5672`"
  },
  "cols": 2,
  "rows": 13,
  "align": [
    "left",
    "left"
  ]
}
[/block]