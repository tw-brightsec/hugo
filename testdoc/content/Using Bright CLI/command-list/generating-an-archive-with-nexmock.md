---
title: "Generating an Archive with NexMock"
slug: "generating-an-archive-with-nexmock"
hidden: false
metadata: 
  description: "Supports the latest NexMock API and provides additional features to help you generate HAR files during CI/CD workflows with ease."
createdAt: "2021-09-15T07:01:39.299Z"
updatedAt: "2022-11-09T10:06:18.062Z"
---
Supports the latest NexMock API and provides additional features to help you generate HAR files during CI/CD workflows with ease.

In addition, this command has the ability to split NexMock files in to multiple .HAR files. For this purpose, you can specify the `--split` option, which accepts the number of pieces in to which to split.

For example:

```bash
nexploit-cli archive:generate --output archive.har --target url-tested-application --header "Authorization: Bearer my-jwt-authentication-token" --split 4 .nexmock 
```



The command above creates four .HAR files that comply with following pattern: `<basename>(_<number>)?.<extension>`. For example, `archive.har`, `archive_2.har` and so on.

## Arguments

| Argument     | Description                                                               |
| :----------- | :------------------------------------------------------------------------ |
| `<mockfile>` | A NexMock file is obtained from the NextMock Reporters. See to E2E Guide. |



## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--output=newArchivePath`,  \n`-f=newArchivePath`",
    "0-1": "The path where the new archives are created, relative to the new workspace root.",
    "1-0": "`-target=hostnameOrIp`,  \n`-T=hostnameOrIp`",
    "1-1": "The target hostname or IP address.",
    "2-0": "`--header=headerName:headerValue`,  \n`-H=headerName:headerValue`",
    "2-1": "Extra headers to be passed with the NexMock file, which can also be used to remove a header by providing a name without content. For example, `-H \"Host:\"`.  \n  \n**Warning:** Headers set with this option override the archive headers and are set in all requests.",
    "3-0": "`--pool=size`, `-p=size`",
    "3-1": "The size of the worker pool. Indicates how many requests Bright CLI can perform in parallel.  \n  \n**Default: **`--pool 250`",
    "4-0": "`--timeout=milliseconds`",
    "4-1": "The time to wait for a server to send response headers (and start the response body) before aborting the request.  \n  \n**Default:** `--timeout 5000`",
    "5-0": "`--split=numberPieces`,  \n`-s=numberPieces`",
    "5-1": "The number of the HAR pieces. Enables you to split a NexMock file in to multiple .HAR files.  \n  \n**Default:** `--split 1`",
    "6-0": "`--config=pathToConfig`",
    "6-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the config in package.json in the root directory of your application or a separate file by a specified name in the working directory. For details, see [Configuration Files](https://docs.brightsec.com/docs/configuration-files) for more information.",
    "7-0": "`--log-level =0/1/2/3/4/silent/  `  \n`error/warn/notice/verbose`",
    "7-1": "Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", and \"verbose\".  \n  \n**Default:**`3`"
  },
  "cols": 2,
  "rows": 8,
  "align": [
    "left",
    "left"
  ]
}
[/block]