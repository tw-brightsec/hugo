---
title: "Repeater (Scan Proxy)"
slug: "on-premises-repeater-local-agent"
hidden: false
metadata: 
  description: "NeuraLegion’s Repeater is a local agent that provides a secure connection between NeuraLegion's cloud engine and a target on a local network."
createdAt: "2021-08-25T07:25:02.724Z"
updatedAt: "2022-12-08T13:14:15.031Z"
---
## Overview

The Bright Repeater is a scan proxy which provides a secure connection between the Bright cloud engine and a target on a local network. The Repeater mode enables you to securely scan targets on a local network, without having to allowlist the Bright IP address in your firewall for incoming traffic.

The Repeater mode is designed for:

- Organizations that cannot open a port in the firewall for inbound traffic. A Repeater enables you to scan either from the Bright SaaS or a private cloud.
- Users who must run a local scan on their machine without deploying the target application.

> 🚧 Important
> 
> - To function properly, a Repeater must have an outbound connection to **amq.app.brightsec.com** via the AMQ protocol (over TLS) using port 5672.
> - If your environment uses a proxy server, please make sure that the SOCKS protocol support is enabled.
> - If traffic from a Repeater to the scan targets is unstable or slow (under 100 milliseconds), this may result in Disrupted Scans and missed vulnerabilities. To avoid such situations, we recommend that you install the Repeater on a production grade machine with a fast and stable connectivity to the targets. You should also avoid connecting the Repeater through a VPN, mobile-hotspot or similar slow/unstable connections.
> - The Repeater mode is not compatible with TLS tests

A Repeater is not required if you are able to allowlist a specific IP and port in your firewall.

## How the repeater deployment works

The Bright Repeater is an [open source](https://www.npmjs.com/package/@neuralegion/nexploit-cli) scan proxy which securely connects to the Bright cloud engines and mediates all traffic from the cloud to any local target.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5e1f17e-Repeater_8.png",
        "Repeater (8).png",
        909
      ],
      "sizing": "80"
    }
  ]
}
[/block]



After starting a scan in the Repeater mode, communication works as follows:

1. The Repeater initiates a GET request to the cloud engine via the AMQ server.
2. The Repeater receives the request instructions describing how to interact with the local target.
3. The Repeater locally adds the relevant headers to the request, such as authentication headers and sends the request to the local target.
4. The local target returns the response to the Repeater.
5. The Repeater sends the response to the engine.
6. The Repeater returns to #1 until the scan completes.

## Technical requirements

Connecting a Repeater requires:

- A local machine with:
  - System: Ubuntu OS / Windows 8+ / MacOS / Docker 20+
  - Processor: x86 or x64 1 core (minimum), 2 core (recommended)
  - RAM: 512 MB (minimum), 1 GB (recommended)
  - Hard disk: up to 512 MB of available space may be required
  - The Docker compose or NodeJS (v10+, but not higher than v15) installed
- Access to the relevant internal targets on a local network
- Access to amq.app.brightsec.com on port 5672 or a private cloud on the relevant port
- If a proxy server is used, make sure it is configured to allow the SOCKS protocol. The Bright Repeater does not support HTTP/HTTPS proxy protocols.

## Installation

To run a scan in the Repeater mode so that all scan requests are pulled (as outbound traffic) from the Bright cloud through a Repeater to the local target, you first need to install the [Bright CLI](/docs/about-bright-cli) on your machine. Using a special [Bright CLI command](https://docs.brightsec.com/docs/command-list), you will be able to connect a Repeater to your local network. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/91d1370-repeater-flow_2.png",
        "repeater-flow (2).png",
        1454
      ],
      "sizing": "80"
    }
  ]
}
[/block]



See the [Bright CLI installation guide](https://docs.neuralegion.com/docs/installation-options) for the instructions.

## Usage

For the usage examples, see [Getting Started](https://docs.brightsec.com/docs/getting-started-with-bright-cli).