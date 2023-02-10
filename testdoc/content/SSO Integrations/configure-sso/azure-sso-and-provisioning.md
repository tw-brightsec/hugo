---
title: "Azure SSO and Provisioning"
slug: "azure-sso-and-provisioning"
hidden: false
metadata: 
  description: "To enable NeuraLegion SSO with AD FS, you should first authenticate Azure in the NeuraLegion App."
createdAt: "2021-09-16T06:19:01.880Z"
updatedAt: "2023-01-04T13:05:57.041Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      <h1></h1>\n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/9b168ab-azure-int.png\" width=170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      <p>System for Cross-domain Identity Management (SCIM) is a protocol for user management across multiple applications. It allows you to easily provision (add), deprovision (delete) and update (map) user data across multiple applications at once. </p>\n      <p>You can set up SCIM provisioning in Azure AD to automatically add the AD application users and groups to your organization in the Bright app. The added users will be able to access the Bright app using Active Directory Federation Services (AD FS) SSO.</p>\n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



Bright supports the following provisioning attribute mappings:

- `userPrincipleName`
- `Switch([IsSoftDeleted], , "False", "True", "True", "False")`
- `givenName`
- `surname`
- `mail`
- `displayName`

## Prerequisites

- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) with the `scim` scope.  
  \*The user profile email is specified in Azure.

## Step-by-step guide

### Step 1. Create an application for SSO integration in Azure

To enable Bright SSO with AD FS, you should first authenticate Azure in the Bright app.

1. Create an application for Bright in Azure. For that, go to **Enterprise Applications** and click **+ New application**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7dcc9a9-select-enterprise.png",
        "select-enterprise.png",
        1893
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Click **+ Create your own application**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/29e0cf2-add-application.png",
        "add-application.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. In the **Create your own application** window, enter a name for a new application and click **Create**. 
4. Once the application is created, go back to the **Home** page and select  **Azure Active Directory**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/31f9bda-select-ad.png",
        "select-ad.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the left pane, select **App registrations**, open the **All applications** tab and select the created application from the list.

> 📘 Note
> 
> It may take some time until the predefined application is published in the Azure AD gallery.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e0b4e85-app-registration.png",
        "app-registration.png",
        1916
      ],
      "sizing": "80"
    }
  ]
}
[/block]



6. Add the redirect URL. For that, select the relevant setting and add a **Web** platform.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ec5df0c-redirect-url.png",
        "redirect-url.png",
        1901
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7628213-select-web.png",
        "select-web.png",
        1915
      ],
      "sizing": "80"
    }
  ]
}
[/block]



          In the **Redirect URIs** field, enter `<https://app.brightsec.com/adfs/callback`> and click **Configure**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/db021fc-enter-url_1.png",
        "enter-url (1).png",
        1910
      ],
      "sizing": "80"
    }
  ]
}
[/block]



7. Go back to the created application and get the following credentials to use them further in the [Bright app](https://app.brightsec.com):

- On the application page, copy the **Client ID**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/ddb2b03-client-ID.png",
        "client-ID.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- In the **Certificates & secrets** tab, create a new secret key and copy its **Value**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7c26555-secret-key.png",
        "secret-key.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- In the **Endpoints** tab, copy the **OpenID Connect metadata document** URL. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1388aa4-endpoints.png",
        "endpoints.png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



8. Go back to **App registrations**, select the created application, and then assign users to this application in the **Users** section.  
   The assigned users will be able to log in to the Bright App using AD FS SSO. 

### Step 2. Enable SSO authentication in the Bright app

Now go to the [Bright app](https://app.brightsec.com) and do the following:

1. In the left pane, select the **Organization** option.
2. From the **Required SSO provider** dropdown list, select **AD FS**, and then click **Connect**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/33329da-sso-connect.png",
        "sso-connect.png",
        1919
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Fill in the **AD FS Authentication** fields with the credentials copied in Azure AD, and then click **Continue**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/7abad46-continue-setup.png",
        "continue-setup.png",
        1911
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. On the Microsoft **Permissions Requested** page, click **Accept**.  
   Now the AD FS SSO is enabled for all the users of the authenticated application with no limitations. 
5. _(Optional)_ You can enforce AD FS SSO registration by selecting the **Require your organization members to use SSO to access Bright** checkbox. When this option is selected, only the registered users (current members of a Bright organization) with existing SSO accounts can access the Bright app.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c1a0686-require-SSO.png",
        "require-SSO.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 🚧 Important
> 
> Strict enforcement of SSO for all organization members will require resetting the connection in case of an SSO break. If that happens, please contact the [Bright technical support](mailto:support@brightsec.com) for assistance.

### Step 3. Enable provisioning

To configure automatic provisioning of Azure AD users and groups to your Bright organization, follow these steps:

1. In the **ORGANIZATION SETTING** section, select the **Sync the groups & users from SSO provider to Bright** checkbox.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/36a6f1c-Group_1261150958.png",
        "Group 1261150958.png",
        1917
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In Azure AD, go to the provisioning section of your application and click **Get Started**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/66fcddb-provisioning.png",
        "provisioning.png",
        1912
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Select one of the following provisioning modes:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a880af0-provisioning-mode.png",
        "provisioning-mode.png",
        719
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Manual** option allows you to add a new user or group to your Bright organization manually with immediate synchronization.
- **Automatic** mode enables adding every new user or group to your Bright organization automatically. The automatic provisioning interval is 40 minutes.

4. In the **Admin Credentials** section, do the following:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cc79fe4-admin-credentials.png",
        "admin-credentials.png",
        1519
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- In the **Tenant URL** field, enter `<https://app.brightsec.com/api/v1/scim`>.

> 🚧 Important
> 
> If you delete a user that was provisioned to a connected Bright organization on the Azure side (either from the synced group or completely), the user will become inactive in the Bright organization and will not be activated back automatically after re-adding them to Azure (or the synced group). To enable automatic activation of users after re-adding them on the Azure side, add the `?aadOptscim062020` flag to the **Tenant URL**, to make it look like `<https://app.brightsec.com/api/v1/scim?aadOptscim062020`>.  
> According to the [Microsoft docs](https://docs.microsoft.com/en-us/azure/active-directory/app-provisioning/application-provisioning-config-problem-scim-compatibility#flags-to-alter-the-scim-behavior), this behavior is currently only available when using the flag, but will become the default behavior over the next few months. Note this feature flag currently does not work with on-demand provisioning.

- In the **Secret Token** field, enter the API key created in the [Bright app](https://app.brightsec.com).

5. Click **Test Connection** to verify the credentials that are authorized for provisioning.
6. _(Optional)_ In the **Settings** section, make sure to set the scope to **Sync only assigned users and groups**. This will ensure that the provisioning will be limited to assigned users/groups only, and that no other Azure AD users will have access to the [Bright app](https://app.brightsec.com) unintendedly.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/af46b8c-assigned-users.png",
        "assigned-users.png",
        668
      ],
      "sizing": "80"
    }
  ]
}
[/block]



7. Above the **Provisioning mode**, click **Save** to save the configuration.
8. In the **Manage provisioning** section, select **Edit attribute mappings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/19d6a3b-Group_205_3.png",
        "Group 205 (3).png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



9. In the **Mappings** section, select **Provision Azure Directory Users**.  
   _Note_: You can keep the group provisioning mappings to default, no changes are required.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/aae30be-_29-10-2021_11.23.52.png",
        "Скриншот 29-10-2021 11.23.52.png",
        1146
      ],
      "sizing": "80"
    }
  ]
}
[/block]



10. Set the attribute mappings to the following:
    - `userPrincipleName\`
    - `Switch([IsSoftDeleted], , "False", "True", "True", "False")`
    - `givenName`
    - `surname`
    - `mail`
    - `displayName`

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/09692d8-image-20211028-082015.png",
        "image-20211028-082015.png",
        3806
      ],
      "sizing": "80"
    }
  ]
}
[/block]



11. To start provisioning, click **Start provisioning**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/96d8a72-start-provisioning.png",
        "start-provisioning.png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Step 4. Assign Azure AD users and groups to your Bright organization

1. In the left pane, select **Users and groups**.
2. Click **+ Add user/group**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f0eea8d-add-users.png",
        "add-users.png",
        1895
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. In the **Users and groups** field, click **None Selected**. Select specific users or a group of users to sync them to your Bright organization, and then click **Assign**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/41286f8-add-assignment.png",
        "add-assignment.png",
        896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- The assigned users will be automatically added to the **MEMBERS** section of your Bright organization. 
- The assigned groups will be automatically added to the **GROUPS** section of your Bright organization. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9f65feb-nexploit-organization.png",
        "nexploit-organization.png",
        1899
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 📘 Note
> 
> If you deprovision a user from the Bright integration application in Azure AD, the relative member turns inactive in your Bright organization and is no longer able to log in to the Bright app using AD FS SSO.

### Step 5. Log in to the Bright app using AD FS SSO

1. On the login page, click **Single Sign On (SSO)**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f1ff795-sso-button.png",
        "sso-button.png",
        1914
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Enter the name of the Bright organization for which the AD FS SSO was enabled, and then click **Continue**.

3. Select **Sign in with AD FS**.  
   You are redirected to the Microsoft login page.

4. Enter your Azure AD user's credentials.