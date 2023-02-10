---
title: "Websocket Scanning"
slug: "websocket-scanning"
hidden: true
createdAt: "2022-08-18T08:20:05.516Z"
updatedAt: "2022-08-30T05:19:35.258Z"
---
WebSocket is an async protocol, which can be used for real-time communication. Websocket updates are sent immediately when they are available, while in HTTP(S) you have to constantly request updates.

> 📘 Websocket scanning is only available with pre-recorded HAR file. See [Scanning with a HAR](https://docs.brightsec.com/docs/scanning-with-a-har) to learn more about this type of scanning.

To make sure the system will define the connection between a outgoing-incoming frame pairs, a unique identifier is used. The request identifier field ("correlationId") is generated during the scan for this purpose. 

To extract the correct payload object, such as JSON, out of WebSocket frames that may contain some auxiliary service data (such as prefix, suffix, etc.) pattern is used. The regex pattern must be specific to extract the actual payload object.









***