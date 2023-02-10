---
title: "Scanning at the Enterprise Level"
slug: "scanning-at-the-enterprise-level"
hidden: false
createdAt: "2022-02-21T21:22:07.333Z"
updatedAt: "2022-12-08T12:36:57.938Z"
---
This guide is designed to match the needs of the following users: 

- An organization that needs to scan targets within their local network, but cannot open a port in the firewall for inbound traffic.
- An organization that needs to scan multiple targets of different teams in their private environments, without exposing the targets externally.

If you have not found your situation in the list above, please check out other use cases in the [Getting Started](https://docs.brightsec.com/docs/quickstart) section. You can also reach out to us at [support@brightsec.com](mailto:support@brightsec.com) or join our [discord channel](https://cmnbp04.na1.hubspotlinks.com/Btc/W1+113/cMnBp04/VVpmWg3C6Ft7W6qmJKp6mcW4FW8_npSB4DtSmXN2jjSxk3q905V1-WJV7CgLN-W6G6Zb21vL4dSW52pMws4_v10bVqz4CH6wnL-5W6K7Yst8FPtdxW2fCWJP2F3LJQW3TsF_C1TCytsW3bLtV12gc722W2dWwlL5nSP_ZW8vdHvH9dM7P-M3LNg6YV4CPN879WmM15R7lW4Vqcz_76RsjKN7VpcL08xMfXW1FWS3v7DGLkYW6n_dhw93YFJ8W1Wr6FD2rpH1cW4l4Fxz5k1vQ_W6dXyKx5H89QnW4NtqpT5VxN0GVdX6fn2-vdPRW1q-YlT3wfCVNN31WkC9CczFTN6qvfY13XkSZW2J2xn63xZ5W0388n1) to ask your questions directly.

For more information about the Bright CLI purpose and features, see [About Bright CLI](https://docs.brightsec.com/docs/about-bright-cli).

The Repeater mode of the Bright CLI is the best solution for organizations that cannot open a port in the firewall for inbound traffic or expose targets externally. If the scan target is closed within a private company network, the Bright engine cannot access it directly from the cloud, and in this case the Repeater will serve as a request-proxy between the Bright cloud engine and the scan target inside your private network. You can either connect a central Repeater to the entire network to run all scans through it, or connect multiple Repeaters to use them separately, for each specific project. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bb633cd-repeater-flow_2.png",
        "repeater-flow (2).png",
        1454
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 🚧 Important
> 
> - To function properly, the Repeater must have an outbound connection to `amq.app.brightsec.com` via the AMQ protocol (over TLS) using port 5672 (or a private cloud using the relevant port). Other technical requirements for Repeater connection can be found [here](/docs/on-premises-repeater-local-agent#technical-requirements).
> - Please contact the Bright [Sales](mailto:sales@brightsec.com) or [Sales Engineering team](mailto:@support@brightsec.com) for Proof of Concept (PoC) related environment details, configurations of repeaters, IP addresses, and ports for repeater connectivity.

Below you can find the following examples of running scans in the Repeater mode:

- [Scanning using the Repeater deployed on a cloud instance (VM)](/docs/scanning-at-the-enterprise-level#scan-using-a-repeater-deployed-on-a-cloud-instance-vm)
- [Scanning in the Repeater mode, via a custom proxy](/docs/scanning-at-the-enterprise-level#scan-using-a-repeater-via-a-custom-proxy)
- [Scanning from a private cloud in the Repeater mode](/docs/scanning-at-the-enterprise-level#scan-from-a-private-cloud-using-a-repeater)

# Scanning using the repeater deployed on a cloud instance (VM)

To scan a target in your local network (behind a firewall) in the Repeater mode, you can deploy the Repeater locally on your machine or use your cloud provider instead (for example, AWS, Azure, and so on). 

When deployed locally, the Repeater disconnects once you close the console, shut down the machine, or in case of a network failure. If the Repeater disconnects during a scanning process, the scan gets disrupted automatically. By running the Repeater on a cloud instance (VM), you decrease the risk of accidental disruption of a scan. This also allows you to use the Repeater as an “always-on” option. 

To deploy the Repeater on a cloud instance, you first need to create the instance. The process of instance creation differs for all cloud providers. Please see the documentation of your cloud provider for the instructions. For example, if you are using AWS, the instructions can be found [here](https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html).

Once the instance is launched, you need to install the Bright CLI on it, using the NPM or Docker option. The installation option depends on the instance OS. You can find the CLI installation guide [here](/docs/installation-options). 

To scan in the Repeater mode, you first need to register the Repeater in the [Bright app](https://app.neuralegion.comhttps://app.neuralegion.com), and then connect (activate) it using the generated Repeater ID. You can see how it works in our [video about connecting the Repeater](https://www.youtube.com/watch?v=ipFkP0od_04&feature=emb_imp_woyt). 

> 🚧 Important
> 
> To function properly, the Repeater must have an outbound connection to `amq.app.brightsec.com` via the AMQ protocol (over TLS) using port 5672 (or a private cloud using the relevant port). Other technical requirements for Repeater connection can be found [here](/docs/on-premises-repeater-local-agent#technical-requirements).
> 
> Please contact Bright Sales/Sales Engineering team for Proof of Concept(PoC) related environment details/configurations of repeaters, IP addresses and ports for repeater connectivity, and so on.

## Prerequisites

- You have launched a cloud instance (VM) and [installed the Bright CLI](/docs/installation-options) on it. 
- You have registered (created) the Repeater and copied the generated `REPEATER_ID`. See [Managing Repeaters](/docs/manage-repeaters) for more information.
- You have a valid `AUTH_TOKEN` (API key) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- You have copied the `Project ID` under which you want to run a scan. A project ID is required. If you do not have any custom projects, use the Default project ID.

## Step-by-step guide

1. Activate the Repeater on the cloud instance:

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

This command initializes a new scan engine in the Bright cloud, which starts scanning the target via the deployed Repeater. The crawler discovery type is used as an example.

> 👍 Tips
> 
> - If you are using the Bright app on a private cloud, ensure you specify the custom cluster instead of `<https://app.brightsec.com`> (for example,  `<https://my-cluster.brightsec.com`>).
> - To optimize the scan coverage and time, we are using the `--smart` option. This enables you to use automatic smart decisions, such as parameter skipping, detection phases, and so on.

3. View the scan results.  
   You can follow the scan status in the [Bright app](https://app.neuralegion.com/) or by using the [Bright CLI polling command](/docs/checking-scan-status).

# Scanning in the repeater mode, via a custom proxy

You can scan a target in your local network so that all requests from the Bright cloud are securely pulled via your custom proxy, in the Repeater mode. This also allows you to monitor all the traffic used for scan-related communication between the Bright engine, Repeater, and local target. You can configure the protocol to only proxy either the internal (from the Repeater to the local target) or external (from the Repeater to the Bright engine) traffic.

To scan in the Repeater mode, you first need to register (create) the Repeater in the [Bright app](https://app.neuralegion.comhttps://app.neuralegion.com), and then connect (activate) it using the generated Repeater ID. You can see how it works in our [video about connecting the Repeater](https://www.youtube.com/watch?v=ipFkP0od_04&feature=emb_imp_woyt).

> 🚧 Important
> 
> To function properly, the Repeater must have an outbound connection to `amq.app.brightsec.com` via the AMQ protocol (over TLS) using port 5672 (or a private cloud using the relevant port). Other technical requirements for Repeater connection can be found [here](/docs/on-premises-repeater-local-agent#technical-requirements).
> 
> Please contact Bright Sales/Sales Engineering team for Proof of Concept(PoC) related environment details/configurations of repeaters, IP addresses and ports for repeater connectivity, and so on.

## Prerequisites

- You have installed the [Bright CLI](/docs/installation-options). 
- You have registered (created) the Repeater and copied the generated `REPEATER_ID`. See [Managing Repeaters](/docs/manage-repeaters) for more information about handling Repeaters.
- You have a valid `AUTH_TOKEN` (API key) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- You have copied the `Project ID` under which you want to run a scan. A project ID is required. If you do not have any custom projects, use the Default project ID.

## Step-by-step guide

1. Activate the Repeater and connect it to your proxy:

```shell
nexploit-cli repeater --token $AUTH_TOKEN --id $REPEATER_ID --proxy $SOCKS_URL --cluster https://app.brightsec.com
```



Here is an example of the proxy format: `--proxy socks5://1.1.1.1`

- If you want to only proxy the **internal traffic**, then use the following command:

```shell
nexploit-cli repeater --token $AUTH_TOKEN --id $REPEATER_ID --proxy-internal $SOCKS_URL --cluster https://app.brightsec.com
```



- If you want to only proxy the **external traffic**, then use the following command:

```shell
nexploit-cli repeater --token $AUTH_TOKEN --id $REPEATER_ID --proxy-external $SOCKS_URL --cluster https://app.brightsec.com
```



> 📘 Notes
> 
> - Bright supports SOCKS4, SOCKS5, SOCKS4a, and SOCKS5h. If you specify `SOCKS://<URL>`,  SOCKS5h is applied by default.
> - `--proxy` is mutually exclusive with `--proxy-external` and `--proxy-internal`.
> - If you are using the Bright app on a private cloud, ensure you specify the custom cluster instead of `<https://app.brightsec.com`> (for example,  `<https://my-cluster.brightsec.com`>).

2. Start a new scan with a crawler:

```shell
nexploit-cli scan:run --token $AUTH_TOKEN --repeater $REPEATER_ID --name "Bright Scan" --project $PROJECT_ID --crawler "https://www.example.com"  --cluster https://app.brightsec.com --smart
```



This command initializes a new scan engine in the Bright cloud, which starts scanning the target in the Repeater mode. The crawler discovery type is used as an example. 

> 📘 Notes
> 
> - Sample variables are marked with a `$`. You must substitute them for your real values.
> - The Repeater must stay active during the whole scanning session. Closing the console or shutting down your machine will disconnect the Repeater and lead to the scan disruption. 
> - To optimize the scan coverage and time, we are using the `--smart` option. This enables you to use automatic smart decisions, such as parameter skipping, detection phases and so on.

3. View the scan results.  
   You can follow the scan status in the [Bright app](https://app.neuralegion.com/) or by using the [Bright CLI polling command](/docs/checking-scan-status).

# Scanning from a private cloud in the Repeater mode

If you are using the Bright app on a private cloud, you can run a scan using the CLI in a regular way, specifying your private cluster instead of the common Bright app subdomain (so it looks like `<https://your-private-cluster.brightsec.com`>). 

To scan in the Repeater mode, you first need to register (create) the Repeater in the [Bright app](https://app.neuralegion.comhttps://app.neuralegion.com), and then connect (activate) it using the generated Repeater ID. You can see how it works in our [video about connecting the Repeater](https://www.youtube.com/watch?v=ipFkP0od_04&feature=emb_imp_woyt).

> 🚧 Important
> 
> To function properly, the Repeater must have an outbound connection to the private cloud using the relevant port. Other technical requirements for Repeater connection can be found [here](/docs/on-premises-repeater-local-agent#technical-requirements).
> 
> Please contact Bright Sales/Sales Engineering team for Proof of Concept(PoC) related environment details/configurations of repeaters, IP addresses and ports for repeater connectivity, and so on.

## Prerequisites

- You have installed the [Bright CLI](/docs/installation-options). 
- You have registered (created) the Repeater and copied the generated `REPEATER_ID`. See [Managing Repeaters](/docs/manage-repeaters) for more information.
- You have a valid `AUTH_TOKEN` (API key) with the following scopes: `scans`, `files:write`, `org:read`, and `projects:read`. You can create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens). You can also watch our video about [creating API keys](https://www.youtube.com/watch?v=W_WdIGPXoUQ&t=3s).
- You have copied the `Project ID` under which you want to run a scan. A project ID is required. If you do not have any custom projects, use the Default project ID.

## Step-by-step guide

1. Activate the Repeater:

```shell
nexploit-cli repeater --token $AUTH_TOKEN --id $REPEATER_ID --cluster https://your-private-cluster.brightsec.com
```



2. Start a new scan with a crawler:

```shell
nexploit-cli scan:run --token $AUTH_TOKEN --repeater $REPEATER_ID --name "Bright Scan" --project $PROJECT_ID --crawler "https://www.example.com" --cluster https://your-private-cluster.brightsec.com --smart
```



This command initializes a new scan engine in the private cloud, which starts scanning the target in the Repeater mode. The crawler discovery type is used as an example.

> 📘 Notes
> 
> - Sample variables are marked with a `$`. You must substitute them for your real values.
> - The Repeater must stay active during the whole scanning session. Closing the console or shutting down your machine will disconnect the Repeater and lead to the scan disruption. 
> - To optimize the scan coverage and time, we are using the `--smart` option. This enables you to use automatic smart decisions, such as parameter skipping, detection phases and so on.

3. View the scan results.  
   You can follow the scan status in the [Bright app](https://app.neuralegion.com/) or by using the [Bright CLI polling command](/docs/checking-scan-status).