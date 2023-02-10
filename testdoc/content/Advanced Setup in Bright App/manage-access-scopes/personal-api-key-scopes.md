---
title: "Personal API Key Scopes"
slug: "personal-api-key-scopes"
hidden: false
metadata: 
  description: "When creating a personal API key in the user settings, you can predefine access permissions for this key by selecting the relative scopes. The following table describes the permissions each scope provides."
createdAt: "2021-09-13T06:55:50.725Z"
updatedAt: "2022-11-08T14:44:05.350Z"
---
When creating a personal API key in the user settings, you can predefine access permissions for this key by selecting the relative scopes. The following table describes the permissions each scope provides.  

| Scope                    | Description                                                                                                                                                 |
| :----------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `auth-objects`           | Provides unrestricted access to authentication objects management                                                                                           |
| `auth-objects:read`      | Allows to view the basic configuration of authentication objects                                                                                            |
| `auth-objects:test`      | Allows testing an authentication object during its configuration                                                                                            |
| `auth-objects:write`     | Allows managing authentication objects that have been created by a user                                                                                     |
| `bot`                    | Enables communication between a Repeater and the Bright engine                                                                                              |
| `files:read`             | Allows reading files from the storage and verifying targets                                                                                                 |
| `files:write`            | Allows managing files in the storage, for example, uploading or deleting them                                                                               |
| `groups:delete`          | Allows deleting groups                                                                                                                                      |
| `groups:manage`          | Allow managing groups, for example creating a new group or editing an existing group                                                                        |
| `groups:read`            | Allows viewing information about groups that a user has been added to                                                                                       |
| `integration.repos:read` | Allows viewing associated repositories, for example, GitHub repositories, Slack channels, or Jira boards                                                    |
| `issues:manage`          | Allows managing detected issues, for example assigning a user to an issue, marking an issue as resolved, or retesting an issue                              |
| `issues:read`            | Allows viewing detected issues                                                                                                                              |
| `org:read`               | Allows viewing basic information about an organization                                                                                                      |
| `org:write`              | Allows editing basic information about an organization and managing its basic settings, for example, enforcing MFA                                          |
| `org.memberships:manage` | Allows managing organization members, for example adding a member to an organization, deleting a member from an organization, or viewing a member’s profile |
| `org.memberships:read`   | Allows viewing members of an organization                                                                                                                   |
| `projects:delete`        | Allows deleting projects                                                                                                                                    |
| `projects:manage`        | Allows managing projects, for example creating a new project or editing an existing one                                                                     |
| `projects:read`          | Allows displaying available projects. This scope is required for running a scan                                                                             |
| `repeaters:read`         | Allows viewing organization’s repeaters                                                                                                                     |
| `repeaters:write`        | Allows creating, editing, deleting a repeater, as well as testing repeater connection to a network                                                          |
| `roles:read`             | Allows viewing a list of roles                                                                                                                              |
| `roles:write`            | Allows creating and editing custom roles. The default roles (for example, “Admin”, “Owner”, etc.) are read-only                                             |
| `scans`                  | Provides unrestricted access to scan management                                                                                                             |
| `scans:delete`           | Allows deleting scans                                                                                                                                       |
| `scans:manage`           | Allows managing scans, for example editing scan settings or retesting a scan                                                                                |
| `scans:read`             | Allows viewing existing scans                                                                                                                               |
| `scans:run`              | Allows running scans                                                                                                                                        |
| `scans:stop`             | Allows stopping scans                                                                                                                                       |
| `scripts:read`           | Allows viewing repeater’s scripts                                                                                                                           |
| `scripts:write`          | Allows creating, editing, and deleting scripts                                                                                                              |
| `user`                   | Selected by default for all roles                                                                                                                           |
| `user:read`              | Allows viewing user’s personal details                                                                                                                      |
| `user:write`             | Allows users to edit their personal details, for example, change names, emails, and passwords                                                               |