---
title: "Role Management Scopes"
slug: "role-management-scopes"
hidden: false
metadata: 
  description: "When creating a custom role to be assigned to a new or an existing user, you can predefine access permissions for this role by selecting the relative scopes. The following table describes the permissions each scope provides."
createdAt: "2021-09-13T06:56:46.801Z"
updatedAt: "2022-11-08T14:41:55.975Z"
---
When creating a custom role to be assigned to a new or an existing user, you can predefine access permissions for this role by selecting the relative scopes. The following table describes the permissions each scope provides.

| Scope                      | Description                                                                                                                                                 |
| :------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `activities`               | Allows viewing notifications and managing the notification feed                                                                                             |
| `api-keys`                 | Allows creating personal API keys                                                                                                                           |
| `auth-objects`             | Provides unrestricted access to authentication objects management                                                                                           |
| `auth-objects:read`        | Allows to view the basic configuration of authentication objects                                                                                            |
| `auth-objects:test`        | Allows testing an authentication object during its configuration                                                                                            |
| `auth-objects:write`       | Allows managing authentication objects that have been created by a user                                                                                     |
| `auth-providers`           | Allows configuring SSO providers (okta, Google, ADFS)                                                                                                       |
| `billing`                  | Allows viewing billing summary                                                                                                                              |
| `comments`                 | Allows viewing and managing comments in scans and issues that a user has access to                                                                          |
| `comments:read`            | Allows viewing comments in scans and issues that a user has access to                                                                                       |
| `comments:write`           | Allows managing (editing, deleting) comments in scans and issues that a user has access to                                                                  |
| `entry-points:read`        | Allows viewing all entry points discovered during a scan                                                                                                    |
| `files:read`               | Allows reading files from the storage and verifying targets                                                                                                 |
| `files:write`              | Allows managing files in the storage, for example, uploading or deleting them                                                                               |
| `groups:admin`             | Provides unrestricted access to all organization groups, including the possibility to assign a role to a group and view all group members                   |
| `groups:manage`            | Allow managing groups, for example creating a new group or editing an existing group                                                                        |
| `groups:read`              | Allows viewing information about groups that a user has been added to                                                                                       |
| `groups:admin`             | Allows viewing information about groups                                                                                                                     |
| `groups:delete`            | Allows deleting groups                                                                                                                                      |
| `integrations:read`        | Allows viewing a list of available and enabled integrations                                                                                                 |
| `integrations:write`       | Allows enabling connection and associating other repositories to be used for a scan (ticketing systems)                                                     |
| `integration.repos:read`   | Allows viewing associated repositories, for example, GitHub repositories, Slack channels, or Jira boards                                                    |
| `integration.repos:manage` | Allows filtering the severity level of issues to be opened in integrated services                                                                           |
| `issues:manage`            | Allows managing detected issues, for example assigning a user to an issue, marking an issue as resolved, or retesting an issue                              |
| `issues:read`              | Allows viewing detected issues                                                                                                                              |
| `logs`                     | Allows viewing the activities log                                                                                                                           |
| `org`                      | Provides unrestricted access to organization management (including permission to delete the organization)                                                   |
| `org:read`                 | Allows viewing basic information about an organization. This scope is required for running a scan                                                           |
| `org:write`                | Allows editing basic information about an organization and managing its basic settings, for example, enforcing MFA                                          |
| `org.api-keys`             | Allows creating organization API keys (tokens)                                                                                                              |
| `org.memberships:manage`   | Allows managing organization members, for example adding a member to an organization, deleting a member from an organization, or viewing a member’s profile |
| `org.memberships:read`     | Allows viewing members of an organization.                                                                                                                  |
| `payments`                 | Allows managing user’s payments                                                                                                                             |
| `payment-methods`          | Allows managing payment methods                                                                                                                             |
| `plans`                    | Allows viewing information about offered plans                                                                                                              |
| `products`                 | Allows viewing information about offered products                                                                                                           |
| `projects:admin`           | Allows viewing information about projects                                                                                                                   |
| `projects:delete`          | Allows deleting projects                                                                                                                                    |
| `projects:manage`          | Allows managing projects, for example creating a new project or editing an existing one                                                                     |
| `projects:read`            | Allows displaying available projects. This scope is required for running a scan                                                                             |
| `project.api-keys`         | Allows creating project-level API keys                                                                                                                      |
| `repeaters:read`           | Allows viewing organization’s repeaters                                                                                                                     |
| `repeaters:write`          | Allows creating, editing, and deleting a repeater, as well as testing repeater connection to a network                                                      |
| `reports:read`             | Allows viewing scan reports                                                                                                                                 |
| `reports:write`            | Allows managing configuration of PDF reports                                                                                                                |
| `roles:read`               | Allows viewing a list of roles                                                                                                                              |
| `roles:write`              | Allows creating and editing custom roles. The default roles (for example, “Admin”, “Owner”, etc.) are read-only.                                            |
| `scans`                    | Provides unrestricted access to scan management                                                                                                             |
| `scans:delete`             | Allows deleting scans                                                                                                                                       |
| `scans:manage`             | Allows managing scans, for example editing scan settings or retesting a scan                                                                                |
| `scans:read`               | Allows viewing existing scans                                                                                                                               |
| `scans:run`                | Allows running scans                                                                                                                                        |
| `scans:stop`               | Allows stopping scans                                                                                                                                       |
| `scans-templates`          | Provides unrestricted access to scan templates management                                                                                                   |
| `scans-templates:read`     | Allows viewing existing scan templates                                                                                                                      |
| `scans-templates:write`    | Allows creating, editing, and deleting custom scan templates                                                                                                |
| `scripts:read`             | Allows viewing repeater’s scripts                                                                                                                           |
| `scripts:write`            | Allows creating, editing, and deleting scripts                                                                                                              |
| `subscriptions`            | Allows managing plan subscriptions for an organization                                                                                                      |
| `user`                     | Selected by default for all roles                                                                                                                           |
| `user:read`                | Allows viewing user’s personal details                                                                                                                      |
| `user:write`               | Allows users to edit their personal details, for example, change names, emails, and passwords                                                               |