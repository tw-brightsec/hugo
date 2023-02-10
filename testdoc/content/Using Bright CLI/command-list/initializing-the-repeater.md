---
title: "Initializing the Repeater"
slug: "initializing-the-repeater"
hidden: false
metadata: 
  description: "The Repeater enables you to run the Nexploit scans on a local compiled application, without exposing your ports externally. This means that you can scan an application without having to deploy it or to generate external reports."
createdAt: "2021-09-15T07:06:34.527Z"
updatedAt: "2022-11-09T10:27:00.810Z"
---
This command initializes the Repeater mode: `nexploit-cli repeater [options]`. When a scan is run in the Repeater mode, all the scan requests are pulled from the cloud through a Repeater (scan proxy) to the local target of the scan.

The Repeater mode enables you to run the Bright scans on a local compiled application, without exposing your ports externally. This means that you can scan an application without having to deploy it or to generate external reports.

The Repeater mode is based on the Bright CLI version. If you have already connected a Repeater, you cannot connect the same Repeater (with the same ID) with a different CLI version. In this case, you first need to install the latest version of the Bright CLI and then proceed to the connection. 

For more details about the Repeater mode, see [Repeater (Scan Proxy)](/docs/on-premises-repeater-local-agent).

**Additional Features**:

- Enables multiple scans to run through a single Repeater.
- Option to add headers to requests locally (for example, authentication cookie), without exposing them to the cloud.

> 🚧 Important
> 
> The Repeater mode requires a working `AUTH_TOKEN` with the scope `repeaters:write`.

## Options

[block:parameters]
{
  "data": {
    "h-0": "Option",
    "h-1": "Description",
    "0-0": "`--id=repeaterId`,  \n`--agent=repeaterId` **(Deprecated)**",
    "0-1": "The ID of an existing Repeater that you want to use",
    "1-0": "`--token=apiKey`,  \n`-t=apiKey`",
    "1-1": "Allows specifying the Bright project for a scan using the project ID. You can find the project ID in the **Projects** section in the [Bright App](https://app.neuralegion.com/scans).  \nGlobal Repeaters are available for every project. You can also connect a Repeater created for the specified project. But if you try to use a Repeater created specifically for some other Bright project, you will get an error message.",
    "2-0": "`--header=headerName:headerValue`,  \n`-H=headerName:headerValue`",
    "2-1": "Extra headers to be passed with each request. Also, it can be used to remove a header by providing a name without content. For example, `-H \"Host:\"`.  \n  \n**Warning:** Headers set with this option override the original headers and are set in all requests.",
    "3-0": "`--headers=json`",
    "3-1": "JSON string that contains a header list, which is initially empty and consists of zero or more name and value pairs.  \n  \n**Warning:** Headers set with this option override the original headers and are set in all requests.",
    "4-0": "`--timeout=milliseconds`",
    "4-1": "Time to wait for a server to send response headers (and start the response body) before aborting the request.  \n  \n**Default:** 30000 ms",
    "5-0": "`--daemon`, `-d`",
    "5-1": "Initializes the Repeater as a local daemon service.  \n  \n**Note:** If you run this command while a service is already running, it will first stop and delete the running service, and then restart it with the new repeater settings.  \n  \n**Note:** Currently supported operating systems include windows (wscm) and Linux (systemd).",
    "6-0": "`--remove-daemon`,  `--remove`,  \n`--rm`",
    "6-1": "Stops and deletes the running repeater service",
    "7-0": "`--scripts=json`, `-S=json`",
    "7-1": "Loads scripts to the Repeater from a JSON of `{\"host\": \"filepath\"}`.  \n  \n**Note:** Wildcards are also supported, for example: `--scripts '{\"\": \"./hmac.js\"}` for a global script for all target hosts, or `--scripts '{\"_.domain.com\": \"./hmac.js\"}` for all target hosts on sub-domains.  \n  \nIf you have loaded a local script to the Repeater using this CLI command, loading remote scripts from the [Bright App](https://app.neuralegion.com/) is disabled automatically.  \n  \nSee [Repeater Scripts](https://docs.brightsec.com/docs/manage-repeater-scripts) for more information about how the Repeater Scripts work.",
    "8-0": "`--cacert=pathToCACerts`",
    "8-1": "You may require to authorize Bright to your network server by providing valid TLS/SSL certificates. This option allows you to load a file with multiple CA certificates to the Repeater that you use for the scan, for example:  \n`nexploit-cli repeater --cacert /etc/ssl/certs/ca-certificates.crt`  \n  \nYou can load certificates from the “Trusted Root Certification Authorities Certificate Store” (Windows only):  \n`nexploit-cli repeater --cacert true`  \n  \nThe Bright CLI also supports autodiscovery from the following files:  \n`/etc/ssl/certs/ca-certificates.crt` // Debian/Ubuntu/Gentoo etc.  \n`/etc/pki/tls/certs/ca-bundle.crt` // Fedora/RHEL 6  \n`/etc/ssl/ca-bundle.pem `// OpenSUSE  \n`/etc/pki/tls/cacert.pem` // OpenELEC  \n`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem `// CentOS/RHEL 7  \n`/etc/ssl/cert.pem `// Alpine Linux  \n`nexploit-cli repeater --cacert true`  \n  \n**Important:** Currently, the Bright’s insecure TLS configuration test is limited to cloud-based scans and is not available for scans run in the Repeater mode. In this case, you need to manually check if the ciphers and encryption applied to the TLS certificates are strong enough, to ensure a high level of security of your application. To simplify the check, you can use open-source TLS/SSL testers, for example:  \n  \n<https://github.com/drwetter/testssl.sh>  \n<https://testssl.sh>  \n  \nNeither of the tools requires installation or an internet connection.  \nFor more information about the TLS configuration issue, see the[ Vulnerability Guide](https://docs.brightsec.com/docs/vulnerability-guide).",
    "9-0": "`--cert=json`",
    "9-1": "You can load a certificate file per host. The file must contain a certificate in the PKCS or PEM format.  \n  \n_Format:_ `--cert \"{\"hostname\": \"example.com\", \"path\": \"./example.pem\", \"passphrase\": \"pa$$word\"}\"`  \n  \n**Example:** `nexploit-cli repeater --cert \"{\\\"path\\\": \\\"/home/user/example.pfx\\\", \\\"hostname\\\": \\\"example.com\\\", \\\"passphrase\\\": \\\"pa$$word\\\"}\"`  \n  \nThe passphrase is optional.",
    "10-0": "`--config=pathToConfig`",
    "10-1": "Specifies the path to the configuration file. By default, the CLI tries to discover the config in the`package.json` in the root directory of your application or a separate file by a specified name in the working directory. For details, see [Configuration Files](https://docs.brightsec.com/docs/configuration-files) for more information.",
    "11-0": "`--log-level =0/1/2/3/4/silent/ `  \n`error/warn/notice/verbose`",
    "11-1": "Allows setting the level of logs to report. Any logs of a higher level than the one specified are shown. The options to select : 0, 1, 2, 3, 4, \"silent\", \"error\", \"warn\", \"notice\", and \"verbose\".  \n  \n**Default:** 3",
    "12-0": "`--cluster`",
    "12-1": "Bright cluster (domain name).  \n  \n**Default:** `https://app.neuralegion.com`",
    "13-0": "`--insecure`",
    "13-1": "Allows the Bright CLI to proceed and operate even if the server connection is considered insecure",
    "14-0": "`--proxy=socksProxyUrl`",
    "14-1": "SOCKS URL to proxy all traffic. SOCKS4, SOCKS5, SOCKS4a, SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.  \n  \n**Note:**` --proxy is mutually exclusive with --proxy-external and --proxy-internal`",
    "15-0": "`--proxy-internal`",
    "15-1": "SOCKS URL to only proxy the traffic applied to the scan-related communication between the Repeater and the target. SOCKS4, SOCKS5, SOCKS4a, SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.  \n  \n**Note:** `--proxy is mutually exclusive with --proxy-external and --proxy-internal`",
    "16-0": "`--proxy-external`",
    "16-1": "SOCKS URL to only proxy the traffic applied to the scan-related communication between the Repeater and the Bright engine. SOCKS4, SOCKS5, SOCKS4a, SOCKS5h are currently supported. By default, if you specify `SOCKS://<URL>`, then SOCKS5h is applied.  \n  \n**Note:** `--proxy is mutually exclusive with --proxy-external and --proxy-internal`",
    "17-0": "`--bus=eventBusUrl`",
    "17-1": "**(Deprecated)**. Bright event bus URL.  \n  \n**Default:**`--bus amqps://amq.app.neuralegion.com:5672`"
  },
  "cols": 2,
  "rows": 18,
  "align": [
    "left",
    "left"
  ]
}
[/block]