---
title: "Project API Key Scopes"
slug: "project-api-key-scopes"
hidden: false
createdAt: "2021-11-19T07:13:58.932Z"
updatedAt: "2022-11-08T14:49:29.145Z"
---
When creating an API key in the project settings, you can predefine access permissions for that key by selecting the relative scopes. The following table describes the permissions that each scope provides.  

| Scope                    | Description                                                                                                                    |
| :----------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| `bot`                    | Enables communication between a Repeater and the Bright engine                                                                 |
| `files:read`             | Allows reading files from the storage and verifying targets                                                                    |
| `files:write`            | Allows managing files in the storage, for example, uploading or deleting them                                                  |
| `integration.repos:read` | Allows viewing associated repositories, for example, GitHub repositories, Slack channels, or Jira boards                       |
| `issues:read`            | Allows viewing detected issues                                                                                                 |
| `issues:manage`          | Allows managing detected issues, for example assigning a user to an issue, marking an issue as resolved, or retesting an issue |
| `scans:delete`           | Allows deleting scans                                                                                                          |
| `scans:manage`           | Allows managing scans, for example editing scan settings or retesting a scan                                                   |
| `scans:read`             | Allows viewing existing scans                                                                                                  |
| `scans:run`              | Allows running scans                                                                                                           |
| `scans:stop`             | Allows stopping scans                                                                                                          |
| `scripts:read`           | Allows viewing repeater’s scripts                                                                                              |
| `scripts:write`          | Allows creating, editing, and deleting scripts                                                                                 |
| `repeaters:read`         | Allows viewing organization’s repeaters                                                                                        |
| `repeaters:write`        | Allows creating, editing, and deleting a repeater, as well as testing repeater connection to a network                         |