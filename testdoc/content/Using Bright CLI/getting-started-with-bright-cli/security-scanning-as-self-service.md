---
title: "Security Scanning as Self-Service"
slug: "security-scanning-as-self-service"
hidden: false
createdAt: "2022-02-21T21:05:22.087Z"
updatedAt: "2023-01-04T12:40:55.988Z"
---
This guide is designed to match the needs of the following users: 

- Users who decided to try the Bright CLI for the first time and want to run a simple scan to see how it works.
- Developers who need to run security scans against a target on their own local machine. There is no need for deployment, they can scan whenever they need it, throughout the development process.

If you have not found your situation in the list above, please check out other use cases in the [Getting Started](/docs/getting-started-with-nexploit-cli) section. You can also reach out to us at [support@brightsec.com](mailto:support@brightsec.com) or join our [discord channel](https://cmnbp04.na1.hubspotlinks.com/Btc/W1+113/cMnBp04/VVpmWg3C6Ft7W6qmJKp6mcW4FW8_npSB4DtSmXN2jjSxk3q905V1-WJV7CgLN-W6G6Zb21vL4dSW52pMws4_v10bVqz4CH6wnL-5W6K7Yst8FPtdxW2fCWJP2F3LJQW3TsF_C1TCytsW3bLtV12gc722W2dWwlL5nSP_ZW8vdHvH9dM7P-M3LNg6YV4CPN879WmM15R7lW4Vqcz_76RsjKN7VpcL08xMfXW1FWS3v7DGLkYW6n_dhw93YFJ8W1Wr6FD2rpH1cW4l4Fxz5k1vQ_W6dXyKx5H89QnW4NtqpT5VxN0GVdX6fn2-vdPRW1q-YlT3wfCVNN31WkC9CczFTN6qvfY13XkSZW2J2xn63xZ5W0388n1) to ask your questions directly.

For more information about the Bright CLI purpose and features, see [About Bright CLI](/docs/getting-started-with-nexploit-cli).

Below you can find the following examples of running scans via the Bright CLI:

- [Running a simple scan with a crawler (works for websites and web applications)](/docs/security-scanning-as-self-service#run-a-simple-scan-with-a-crawler)
- [Scanning specific interactions, pages, or features using a .HAR file (works for websites, web applications and APIs)](/docs/security-scanning-as-self-service#scan-specific-interactions-pages-or-features-using-a-har-file)
- [Scanning API endpoints directly from a schema (for example, OpenAPI, Postman)](/docs/security-scanning-as-self-service#scan-api-endpoints-based-on-a-schema)
- [Scanning applications behind your firewall, from cloud, in the Repeater mode](/docs/security-scanning-as-self-service#scan-applications-behind-your-firewall-from-the-bright-cloud-in-the-repeater-mode)

# Runinging a simple scan with a crawler


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2F60EmyIvDPfU%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D60EmyIvDPfU&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F60EmyIvDPfU%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=60EmyIvDPfU&feature=youtu.be",
  "title": "Running a Scan with a Crawler via CLI",
  "favicon": "https://www.youtube.com/s/desktop/1b170d1d/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/60EmyIvDPfU/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=60EmyIvDPfU&feature=youtu.be"
}
[/block]




Bright can crawl your web application to define the attack surface of the target and optimize the selected security tests. For that, you simply need to specify the URL of the target to start mapping from. 

If you want to run a scan with a crawler using the Bright app, read [here](/docs/crawler). 

## Prerequisites

- You have installed the [Bright CLI](/docs/installation-options).
- You have a valid `AUTH_TOKEN` (API key) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- You have copied the `Project ID` under which you want to run a scan. A project ID is required. If you do not have any custom projects, use the Default project ID.

## Step-by-step guide

1. Start a new scan with a crawler:

```shell
nexploit-cli scan:run --token $AUTH_TOKEN --name "Bright Scan" --project $PROJECT_ID --crawler "https://www.example.com" --cluster https://app.brightsec.com --smart
```



> 📘 Note
> 
> Sample variables are marked with a `$`. You must substitute them for your real values.

This command initializes a new scan engine in the cloud, which starts scanning the target. The crawler discovery type is used as an example. 

> 👍 Tips
> 
> - If you are using the Bright app on a private cloud, ensure you specify the custom cluster instead of `<https://app.brightsec.com`>.
> - To optimize the scan coverage and time, we are using the `--smart` option. This enables you to use automatic smart decisions, such as parameter skipping, detection phases and so on.

2. View the scan results.  
   You can follow the scan status in the [Bright app](https://app.neuralegion.com/) or by using the [Bright CLI polling command](/docs/checking-scan-status).

# Scanning specific interactions, pages, or features using a .HAR file


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FZ_fa__2hT-8%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DZ_fa__2hT-8&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FZ_fa__2hT-8%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=Z_fa__2hT-8&feature=youtu.be",
  "title": "Running a Scan Using a HAR File via the CLI",
  "favicon": "https://www.youtube.com/s/desktop/1b170d1d/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/Z_fa__2hT-8/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=Z_fa__2hT-8&feature=youtu.be"
}
[/block]




Bright uses data recorded in .HAR files to define the scope of the security scan and optimize the selected security tests. Using a .HAR, you can easily run a scan on a specific part of your application, instead of testing the entire target, perfect to test a new feature, specific entry-point or flow in your application. This will greatly reduce the scope of the testing, resulting in significantly shorter scan times.

If you want to run a scan with a .HAR file using the Bright app, read [here](/docs/scanning-with-a-har).

## Prerequisites

- You have installed the [Bright CLI](/docs/installation-options).
- You have uploaded the .HAR file to your Bright storage and copied the generated ID (`FILE_ID`). See [Creating a HAR file](/docs/creating-a-har-file) to learn how to create a HAR file.
- You have a valid `AUTH_TOKEN` (API key) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- You have copied the `Project ID` under which you want to run a scan. A project ID is required. If you do not have any custom projects, use the Default project ID.

## Step-by-step guide

1. Start a new scan with the .HAR file uploaded to your Bright storage:

```shell
nexploit-cli scan:run --token $AUTH_TOKEN --name "Bright Scan" --project $PROJECT_ID --archive $FILE_ID --cluster https://app.brightsec.com --smart
```



> 📘 Note
> 
> Sample variables are marked with a `$`. You must substitute them for your real values.

This command initializes a new scan engine in the cloud, which starts scanning the target. The crawler discovery type is used as an example. 

> 👍 Tips
> 
> - If you are using the Bright app on a private cloud, ensure you specify the custom cluster instead of `<https://app.brightsec.com`> (for example,  `<https://my-cluster.brightsec.com`>).
> - To optimize the scan coverage and time, we are using the `--smart` option. This enables you to use automatic smart decisions, such as parameter skipping, detection phases and so on.
> - You can also set the crawler to scan only specific hosts using the  `--host-filter` option. For example:  
> 
> ```bash
> nexploit-cli scan:run --token $AUTH_TOKEN --name "Bright Scan" --project $PROJECT_ID --crawler "https://www.example.com" --host-filter "https://www.host-1.com" "https://www.host-2.com"--cluster https://app.brightsec.com --smart
> ```

2. Viewing the Scan Results.  
   You can follow the scan status in the [Bright app](https://app.neuralegion.com/) or by using the [Bright CLI polling command](/docs/checking-scan-status).

# Scanning API endpoints based on a schema


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2Fvsk2TpeTZYY%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Dvsk2TpeTZYY&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2Fvsk2TpeTZYY%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=vsk2TpeTZYY&feature=youtu.be",
  "title": "Scanning API Endpoints via the NeuraLegion CLI",
  "favicon": "https://www.youtube.com/s/desktop/1b170d1d/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/vsk2TpeTZYY/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=vsk2TpeTZYY&feature=youtu.be"
}
[/block]




Bright can parse an uploaded API schema to define the attack surface of the target and optimize the selected security tests. The following versions of the API schemas are supported: Swagger 2+, OpenAPI 3+, Postman 2+. To ensure proper scanning of your API, you must configure the schema according to the general specification and specific Bright requirements. Find more information about the configuration validation [here](/docs/troubleshooting).

If you want to scan API endpoints using the Bright app, read [here](/docs/scanning-api-endpoints). 

## Prerequisites

- You have installed the [Bright CLI](/docs/installation-options).
- You have uploaded the API schema you want to scan to your Bright storage and copied the generated ID (`FILE_ID`).
- You have a valid `AUTH_TOKEN` (API key) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- You have copied the `Project ID` under which you want to run a scan. A project ID is required. If you do not have any custom projects, use the Default project ID.

## Step-by-step guide

1. Start a new scan with the API schema uploaded to your Bright storage:

```shell
nexploit-cli scan:run --token $AUTH_TOKEN --name "Bright Scan" --project $PROJECT_ID --archive $FILE_ID --cluster https://app.brightsec.com --smart
```



> 📘 Note
> 
> Sample variables are marked with a `$`. You must substitute them for your real values.

This command initializes a new scan engine in the cloud, which starts scanning the target. The crawler discovery type is used as an example.

> 👍 Tips
> 
> - If you are using the Bright app on a private cloud, ensure you specify the custom cluster instead of `<https://app.brightsec.com`> (for example,  `<https://my-cluster.brightsec.com`>).
> - To optimize the scan coverage and time, we are using the `--smart` option. This enables you to use automatic smart decisions, such as parameter skipping, detection phases and so on.

2. View the scan results.  
   You can follow the scan status in the [Bright app](https://app.neuralegion.com/) or by using the [Bright CLI polling command](/docs/checking-scan-status).

# Scanning applications behind your firewall, from the Bright cloud, in the Repeater mode

To scan targets in your private environment, for example, an application which is currently under development and cannot be exposed externally,  you need to use a [Repeater](/docs/on-premises-repeater-local-agent). If the scan target is closed within your network or protected by a firewall, the Bright engine cannot access it directly from the cloud. The Repeater serves as a request-proxy between the Bright engine and a scan target in your private environment. 

To scan in the Repeater mode, you first need to register (create) the Repeater in the [Bright app](https://app.neuralegion.com), and then connect (activate) it to for the scan using the generated Repeater ID. You can see how it works in our [video about connecting the Repeater](https://www.youtube.com/watch?v=ipFkP0od_04&feature=emb_imp_woyt). 

> 🚧 Important
> 
> To function properly, the Repeater must have an outbound connection to `amq.app.brightsec.com` via the AMQ protocol (over TLS) using port 5672 (or a private cloud using the relevant port). Other technical requirements for Repeater connection can be found [here](/docs/on-premises-repeater-local-agent#technical-requirements).

## Prerequisites

- You have installed the [Bright CLI](/docs/installation-options).
- You have a valid `AUTH_TOKEN` (API key) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- You have copied the `Project ID` under which you want to run a scan. A project ID is required. If you do not have any custom projects, use the Default project ID.
- You have registered the Repeater in the [Bright app](https://app.neuralegion.com/) and copied the generated `REPEATER_ID`. See [Managing Repeaters](/docs/manage-repeaters) for more information.

## Step-by-step guide

1. Activate the Repeater:

```shell
nexploit-cli repeater --token $AUTH_TOKEN --id $REPEATER_ID --cluster https://app.brightsec.com
```



2. Start a new scan with a crawler:

```shell
nexploit-cli scan:run --token $AUTH_TOKEN --repeater $REPEATER_ID --name "Bright Scan" --project $PROJECT_ID --crawler "https://www.example.com" --cluster https://app.brightsec.com --smart
```



> 📘 Note
> 
> Sample variables are marked with a `$`. You must substitute them for your real values.

This command initializes a new scan engine in the cloud, which starts scanning the target in the Repeater mode. The crawler discovery type is used as an example.

The Repeater must stay active during the whole scanning session. Closing the console or shutting down your machine will disconnect the Repeater and lead to the scan disruption. 

> 👍 Tips
> 
> - If you are using the Bright app on a private cloud, ensure you specify the custom cluster instead of `<https://app.brightsec.com`> (for example,  `<https://my-cluster.brightsec.com`>).
> - To optimize the scan coverage and time, we are using the `--smart` option. This enables you to use automatic smart decisions, such as parameter skipping, detection phases and so on.

3. View the scan results.  
   You can follow the scan status in the [Bright app](https://app.neuralegion.com/) or by using the [Bright CLI polling command](/docs/checking-scan-status).