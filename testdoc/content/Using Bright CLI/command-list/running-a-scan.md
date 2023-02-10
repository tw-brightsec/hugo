---
title: "Running a Scan"
slug: "running-a-scan"
hidden: false
metadata: 
  description: "This command enables you to specify one or more discovery strategies. For example, using the `--crawler` option and/or the generated HAR files, separately or concurrently. This means that you can handle client-side dynamic content, JavaScript and so on."
createdAt: "2021-09-15T06:26:48.661Z"
updatedAt: "2022-12-08T12:43:53.253Z"
---
```
```



This command enables you to specify one or more discovery strategies. For example, using the `--crawler` option and/or the generated .HAR files, separately or concurrently. This means that you can handle client-side dynamic content, JavaScript, and so on.

> 📘 Note
> 
> If the maximum number of scans that can be run simultaneously is exceeded, the scan is placed in the queue. The concurrent scans limitation can be set either for the entire organization or for this particular project in the project settings. The new scan will start as soon as you manually stop another running scan or when the current scan is completed.

## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--token=apiKey`, `-t=apiKey`",
    "0-1": "The unique identifier used to authenticate a user. The token (API key) can be issued in your organization’s dashboard.",
    "1-0": "`--name=scanName`, `-n=scanName`",
    "1-1": "The name of the scan",
    "2-0": "`--archive=fileId`, `-a=fileId`",
    "2-1": "The archive ID, which can be received via the `archive:upload` command.",
    "3-0": "`--crawler=url`, `-c=url`",
    "3-1": "Specifies a list of specific URLs that should be included during crawler discovery. You can see how it works in our [how-to video](https://youtu.be/60EmyIvDPfU).",
    "4-0": "`--repeater=repeaterId`,  \n`--agent=repeaterId` **(Deprecated)**",
    "4-1": "Specifies a list of Repeater UUIDs that should be connected with the scan",
    "5-0": "`--cluster`",
    "5-1": "Bright cluster (domain name)  \n  \n**Default:** `app.brightsec.com`",
    "6-0": "`--project`, `-p`",
    "6-1": "Allows specifying the Bright project for a scan using the project ID. You can find the project ID in the **Projects** section in the [Bright app](https://app.neuralegion.com/scans).",
    "7-0": "`--integration`, `-i`",
    "7-1": "Allows connecting a ticketing service with an associated repository for a scan. It enables you to get the reports on every detected vulnerability in automatically opened tickets/issues of the associated repository. You can see how it works in [our how-to video](https://www.youtube.com/watch?v=ruU5sULY_8o&t=27s).  \n  \n**Note:** You can only connect a ticketing service (system) that was previously integrated with the [Bright app](https://app.neuralegion.com/). Read more about integrating Bright with ticketing systems [here](https://docs.brightsec.com/docs/about-integrations).  \n  \n_Format:_ `-i \"service:repository\"`  \n_Example:_ `-i \"github:example-app\"  `  \nIf you want to connect several repositories for one scan, you can specify them one after another: `-i \"github:example-app\" -i \"jira:example-app\"`  \n  \n**Important:**  \n  \n- To connect a ticketing service and a repository for a scan, the token (API key) that you use for the scan must include the `integration.repos:read` scope.  \n- The `--integration` (`-i`) parameter cannot be used without a valid `--project` (`-p`) parameter (see above). Make sure that you connect a repository associated with the specified project.",
    "8-0": "`--smart`",
    "8-1": "Enables you to use automatic smart decisions, such as parameter skipping, detection phases, and so on to minimize scan time. When set to `false` (turned off), all tests are run on all parameters, which increases the coverage at the expense of scan time.  \n  \n**Default**: `--smart true`",
    "9-0": "`--param=path/query/fragment/`  \n`header/body/artifical-fragment/artifical-query`",
    "9-1": "Defines which part of the request to attack (see [here](https://docs.brightsec.com/docs/advanced-mode) for more details).  \n  \n**Note:** This argument can be passed multiple times in the same command.  \n  \n**Default:** `--parameter body query fragment`.",
    "10-0": "`--module=dast/fuzzer`",
    "10-1": "The DAST module tests for specific scenarios, such as OWASP top 10 and other common scenarios. The fuzzer module generates various new scenarios in order to test for unknown issues, providing automated AI-guided fuzz testing.  \n  \n**Default:** `--module dast`",
    "11-0": "`--host-filter=hostOrIp`, `-F=hostOrIp`",
    "11-1": "The list of specific hosts to be included in the scan.",
    "12-0": "`--header=headerName:headerValue`,  \n`-H=headerName:headerValue`",
    "12-1": "Extra headers to be passed with the archive file. It can also be used to remove a header by providing a name without content. For example, -H \"Host:\".  \n  \n**Warning:** Headers set with this option override the archive headers and are set in all the requests.",
    "13-0": "`--test=testName`",
    "13-1": "Specifies a list of relevant tests to execute during a scan.  \nFor example, `--test default_login_location dom_xss`.",
    "14-0": "`--auth=authObjectID`,  \n`-o=authObjectID`",
    "14-1": "Specifies the ID of the authentication object to be connect to the scan. Find more info about using an authentication object at [Manging Your Authentications](https://docs.brightsec.com/docs/creating-an-authentication-object-in-nexploit).",
    "15-0": "`--config=pathToConfig`",
    "15-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the config in the`package.json` in the root directory of your application or a separate file by a specified name in the working directory. For details, see [Configuration Files](https://docs.brightsec.com/docs/configuration-files) for more information.",
    "16-0": "`--log-level=0/1/2/3/4/silent/`  \n`error/warn/notice/verbose`",
    "16-1": "Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", \"verbose\".  \n  \n**Default:** 3",
    "17-0": "`--insecure`",
    "17-1": "Allows the Bright CLI to proceed and operate even if the server connection is considered insecure.",
    "18-0": "`--proxy=socksProxyUrl`",
    "18-1": "SOCKS URL to proxy all traffic.  \n  \n**Note:** SOCKS4, SOCKS5, SOCKS4a, SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.",
    "19-0": "`--api=clusterUrl`",
    "19-1": "**(Deprecated)**. Set the API endpoint domain, for VPC, use: --api <https://private-domain.brightsece.com>  \n  \n**Default:** `--api <https://app.brightsec.com`>",
    "20-0": "`--exclude`",
    "20-1": "Enables you to manage exclusions from a scan.  \n  \nIf you want to ignore some of the parameter names during the tests, use `exclude-param`. For example, `--exclude-param ID$`.  \n  \n`--exclude-entry-point` A list of JSON strings that contain patterns for entry points you would like to ignore during the tests.  \n  \n**Important:**  \n  \n- To remove default exclusions, pass an empty string.  \n- To apply patterns for all HTTP methods, you can set an empty array to “methods”. For example `{“methods”: [], “patterns”: “users\\\\/?$”}`."
  },
  "cols": 2,
  "rows": 21,
  "align": [
    "left",
    "left"
  ]
}
[/block]