---
title: "Adding Ticketing Integration to a Project"
slug: "adding-ticketing-integration-to-a-project"
hidden: false
createdAt: "2022-11-01T11:28:38.610Z"
updatedAt: "2023-01-04T09:33:47.499Z"
---
You can integrate one or several ticketing systems with a specific Bright project. Therefore, you are able to select any of the repositories available for the specified Bright project when you start a new scan. 

## Prerequisites

Integration flow is divided into organization and project levels. At the organization level, basic integration settings are performed - in some cases, just turning it on or off. Complete integration setup is done at the project level. This is made in order to simplify and speed up the configuration process in companies with a large number of projects. 

## Step-by-step guide

### Configuring the Bright project integration on the Organization level

1. First of all, you need to enable a particular ticketing integration. In the left pane, select the **Organization** page and scroll down to **Ticket Management Integration** settings.  
   ![](https://files.readme.io/4eea092-__2022-11-01__16.41.34.png)
2. Click the <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26">, and then click **Settings**.  
   ![](https://files.readme.io/e42f383-__2022-11-01__16.42.49.png)
3. Click **Activate** to continue.

![](https://files.readme.io/8689f52-__2022-11-01__16.45.11.png)



4. Next, make sure you have granted all required permissions to the integration app. 

   Congratulations! Now everything is ready to be adjusted at the project level. 

### Configuring the Bright project integration on the Project level

1. Open the **Projects** page and choose the one project which you want to manage. 

![](https://files.readme.io/2aaa83c-__2022-11-01__17.28.45.png)

2. Click **Settings** and scroll down to **Ticketing settings**.

   ![](https://files.readme.io/db2013a-__2022-11-01__17.29.40.png)

   > 📘 Info
   > 
   > Also, you can simply click the icon near the Project name and then click Settings without opening the Project page.
3. Click **+Add Ticketing** and then choose the integration you have added in the organization-level step.
4. Choose a repository, which you want to associate with this ticketing service.
5. Click **Save**.  
   Now, this service is displayed in the **Ticketing Settings** list and successfully integrated.

### Filtering the severity level of issues to be opened in the integrated services

You can select a certain severity level of issues to be sent to a repository/channel associated with your Bright project. For example, if you set the high severity level for the GitHub integration, then only the detected issues of high severity will be displayed in your GitHub repository. 

> 📘 Note
> 
> The option to filter issue severity is only available to the users whose roles include the `integrations.repos:manage` access scope. For more information, see [Manage Access Scopes](/docs/manage-access-scopes).

1. In the left pane, select **Projects**.
2. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to the project which is integrated with the required ticketing service, and then select **Settings**.
3. In the **TICKETING SETTINGS** section, use the **Issue severity** dropdown menu to filter the issues that will be sent to the associated repository.

### How to turn off the integration with the ticketing service

1. To disassociate an integrated ticketing service, open the **Project** settings page and scroll down to the Ticketing settings. 
2. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> and choose **Disassociate**.
3. Click **Yes** to continue.