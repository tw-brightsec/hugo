---
title: "Uploading an Archive"
slug: "uploading-an-archive"
hidden: false
metadata: 
  description: "Uploading an Archive"
createdAt: "2021-09-15T06:48:08.557Z"
updatedAt: "2022-12-08T12:40:19.407Z"
---
If an archive with that name already exists, the following error message displays this message: `The file with that name already exists or the HAR file is corrupted`.

> 🚧 Important
> 
> If you plan to run a scan using an OAS file, you must specify a different discovery option by setting the <br> `--discovery` to OAS.

## Arguments

| Argument | Description                                                                                                                                                                                                                                                       |
| :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <file>   | A collection of your app `http/websockets` logs exported into a .HAR file. Typically, you can use any browser's dev tools, Bright's browser extension, or a Cypress plugin to generate them. In addition, you can use an OAS file that describes your public API. |

## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--token=apiKey`, `-t=apiKey`",
    "0-1": "The unique identifier used to authenticate a user. The token (API key) can be issued in your organization’s dashboard.",
    "1-0": "`--type=har/openapi/postman`,  \n`-t=har/openapi/postman`",
    "1-1": "The specification type, which helps determine the best way to parse passed files.  \n  \n**Default:** `--type har`",
    "2-0": "`--discard`, `-d`",
    "2-1": "When true, removes an archive from the cloud storage after the scan finishes running.  \n  \n**Default:** `--discard true`",
    "3-0": "`--header=headerName:headerValue`,  \n`-H=headerName:headerValue`",
    "3-1": "Extra headers to be passed with the OAS/Postman file. Also, it can be used to remove a header by providing a name without content. For example, `-H \"Host:\"`.  \n  \n**Warning:** Headers set with this option override the archive headers and are set in all requests.",
    "4-0": "`--variable=variableName:variableValue`,  \n`-V=variableName:variableValue`",
    "4-1": "Environment variables passed with the Postman file.",
    "5-0": "`--config=pathToConfig`",
    "5-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the config in the `package.json` in the root directory of your application or a separate file by a specified name in the working directory. For details, see [Configuration Files](https://docs.brightsec.com/docs/configuration-files) for more information.",
    "6-0": "`--log-level\n=0/1/2/3/4/silent/\n`  \n`error/warn/notice/verbose`",
    "6-1": "Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", and \"verbose\".  \n  \n**Default:** 3",
    "7-0": "`--cluster`",
    "7-1": "Bright cluster (domain name).  \n  \n**Default:**`<https://app.brightsec.com`>",
    "8-0": "`--insecure`",
    "8-1": "Allows the Bright CLI to proceed and operate even if the server connection is considered insecure.",
    "9-0": "`--proxy=socksProxyUrl`",
    "9-1": "SOCKS URL to proxy all traffic.  \n  \n**Note:** SOCKS4, SOCKS5, SOCKS4a, and SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.",
    "10-0": "`--api=clusterUrl`",
    "10-1": "**(Deprecated)**. Set the API endpoint domain, for VPC, use: --api <https://private-domain.brightsec.com>  \n  \n**Default:**` --api <https://app.brightsec.com`>"
  },
  "cols": 2,
  "rows": 11,
  "align": [
    "left",
    "left"
  ]
}
[/block]