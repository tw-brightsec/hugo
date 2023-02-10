---
title: "Okta Integration"
slug: "okta-integration"
hidden: true
createdAt: "2021-11-05T05:42:18.884Z"
updatedAt: "2022-10-11T17:49:56.905Z"
---
> 🚧 Disclaimer
> 
> The integration with Okta via the SAML protocol is currently under development and is not available to customers yet. Contact us at [support@neuralegion.com](mailto:support@neuralegion.com) to learn more.

[block:html]
{
  "html": "<table id=\"integrations\" >\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\"> To simplify user access to NeuraLegion, you can configure Single Sign-On (SSO) integration with your Okta application. You can also take advantage of Okta provisioning feature to automatically synchronize users and groups between your Okta application and Nexploit organization.<p></p> The provisioning integration is built around an industry-standard protocol known as SCIM (System for Cross-domain Identity Management).  This protocol is design for user management across multiple applications. It allows you to easily provision (add), deprovision (delete) and update (map) user data across multiple applications at once.<p>\n   \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/342dda2-Integration_logo_template10.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



You can set up SCIM provisioning in Okta to automatically add the Okta application users and groups to your organization in the NeuraLegion App. The added users will be able to access the NeuaLegion App using Okta SSO. NeuraLegion supports the OIDC and SAML protocols to enable Okta SSO, but only the SAML protocol allows users and groups provisioning. 

> 📘 Note
> 
> Currently, Okta/NeuraLegion OIDC integration only supports SP-initiated SSO.

NeuraLegion supports the following attribute mappings for SCIM provisioning:

- `userName`
- `givenName`
- `familyName`
- `email`
- `displayName`

# Enabling Okta SSO via OIDC protocol

## Features

Okta integration with NeuraLegion allows users to link their Okta accounts with their NeuraLegion accounts and sign in to the NeuraLegion App using Okta as a single sign-on provider.

## Requirements

The NeuraLegion integration with Okta is available to Pro and Enterprise users only. To learn how to upgrade your plan, please read [Manage Your Plan](/docs/manage-your-plan).

## Step-by-step configuration guide

To enable Okta SSO for your NeuraLegion organization, follow these steps:

1. Log in to Okta.
2. Browse for the preconfigured [NexPloit app](https://www.okta.com/integrations/nexploit/#overview) in the Okta catalog and add it to your applications. 
3. Assign users to the NexPloit app.  
   The assigned users will then get SSO access to the NeuraLegion App.
4. In the **General** tab of the app, set the redirection URL to `<https://app.neuralegion.com/okta/callback`>. If you are using NeuraLegion on a private cloud, specify your custom cluster in the following format: `<https://{clusterName}.neuralegion.com/okta/callback`>. 
5. In the **Sign On** tab, get the credentials of the created app to authorize it in the NeuraLegion App:

- Copy the client ID and client secret values.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/68a8bf4-oidc-credentials.png",
        "oidc-credentials.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- Click OpenID Provider Metadata and copy its URL. The metadata URL format is `<https://{org_slug}.okta.com/.well-known/openid-configuration`>

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1b5712a-metadata-oidc.png",
        "metadata-oidc.png",
        1893
      ],
      "sizing": "80"
    }
  ]
}
[/block]



6. Log in to the NeuraLegion App.
7. In the left pane, select the **Organization** option, and go to the **ORGANIZATION SETTINGS** section.
8. From the **Single sign on (SSO) Authentication** drop-down list, select **Okta**, and then click **Connect**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b2895b2-okta-provider.png",
        "okta-provider.png",
        1900
      ],
      "sizing": "80"
    }
  ]
}
[/block]



9. On the **OKTA AUTHENTICATION** page, select the default role for new members, enter the credentials copied from the app in Okta, and click **Continue**.  
   After Okta SSO is set up, an email is sent to all the users of your NeuraLegion organization suggesting to confirm their accounts and link their Okta profiles to the NeuraLegion profiles. Once the accounts are linked, the users can log in to the NeuraLegion App using the Okta SSO option.
10. On the login page of the NeuraLegion App, click **Single Sign On (SSO)**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e0739cf-sso-neuralegion.png",
        "sso-neuralegion.png",
        1914
      ],
      "sizing": "80"
    }
  ]
}
[/block]



11. Enter your NeuraLegion organization name and click **Continue**.
12. Select **Sign in with Okta**.  
    You are redirected to the Okta login page.
13. Enter your Okta credentials and click **Sign In**.

## Known issues/troubleshooting

Please contact our support team at [support@neuralegion.com](mailto:support@neuralegion.com) if you encounter any issues with NeuraLegion/Okta integration.

# Enabling Okta SSO via SAML protocol

## Features

Okta integration with NeuraLegion allows users to link their Okta accounts with their NeuraLegion accounts and sign in to the NeuraLegion App using Okta as a single sign-on provider.

## Requirements

The NeuraLegion integration with Okta is available to Pro and Enterprise users only. To learn how to upgrade your plan, please read [Manage Your Plan](/docs/manage-your-plan).

## Step-by-step configuration guide

To enable Okta SSO for your NeuraLegion organization, follow these steps:

1. Log in to your Okta application.
2. Create a NeuraLegion integration application and assign users to this app. The assigned users will then get SSO access to the NeuraLegion App.
3. In the **General tab** of the integration NeuraLegion application , set the **Single sign on URL** to `<https://app.neuralegion.com/api/v1/auth/login/okta/callback`>. If you are using the NeuraLegion App on a private cloud, specify your custom cluster in the following format: `<https://{clusterName}.neuralegion.com/api/v1/auth/login/okta/callback`>.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6ad3736-sso-url-okta.png",
        "sso-url-okta.png",
        1897
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Set the **Audience URL (SP Entity ID)** to match the format of the SSO URL. For example, `<https://{clusterName}.neuralegion.com`>.
5. In the **Attribute Statements (Optional)** section, set the statements to the following:

- `firstName`
- `lastName`
- `email`

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2c40409-attributes-okta.png",
        "attributes-okta.png",
        1702
      ],
      "sizing": "80"
    }
  ]
}
[/block]



6. In the **Credentials Details** section, set **Application username format** to **Email**. 
7. In the **Sign On** tab, get the metadata of the created application to authorize it in the NeuraLegion App. For that, click **OpenID Provider Metadata** and copy its URL.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d5223d1-saml-metadata.png",
        "saml-metadata.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



8. Log in to the NeuraLegion App.
9. In the left pane, select **Organization**, and go to the **ORGANIZATION SETTINGS** section.
10. From the **Single sign on (SSO) Authentication** drop-down list, select **Okta**, and then click **Connect**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8f34c21-okta-provider.png",
        "okta-provider.png",
        1900
      ],
      "sizing": "80"
    }
  ]
}
[/block]



11. On the **OKTA AUTHENTICATION** page, set the default role for new members, select the **SAML** protocol, and enter the copied metadata URL.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/09c2896-saml-radiobutton.png",
        "saml-radiobutton.png",
        1909
      ],
      "sizing": "80"
    }
  ]
}
[/block]



12. Click **Continue**.  
    After Okta SSO is set up, an email is sent to all the users of your NeuraLegion organization suggesting to confirm their accounts and link their Okta profiles to the NeuraLegion profiles. Once the accounts are linked, the users can log in to the NeuraLegion App using the Okta SSO option.
13. On the login page of the NeuraLegion App, click **Single Sign On (SSO)**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b3ca433-sso-button.png",
        "sso-button.png",
        1914
      ],
      "sizing": "80"
    }
  ]
}
[/block]



14. Enter your NeuraLegion organization name and click **Continue**.
15. Select **Sign in with Okta**.  
    You are redirected to the Okta login page.
16. Enter your Okta credentials and click **Sign In**.

## Known issues/troubleshooting

Please contact our support team at [support@neuralegion.com](mailto:support@neuralegion.com) if you encounter any issues with NeuraLegion/Okta integration.

# Enabling SCIM provisioning between Okta and Bright

## Features

The following provisioning features are currently supported by NeuraLegion:

- **Push New Users**. Users created in Okta and assigned to the NeuraLegion integration application in Okta are automatically added as members to the linked organization in the NeuraLegion App.
- **Push Profile Updates**. Updates made to the user's profile through OKTA will be pushed to the NeuraLegion App.
- **Push User Deactivation**. Deactivating the user or disabling the user's access to the NeuraLegion integration application through OKTA will deactivate the user in the NeuraLegion App.  
  _Note:_ For the NeuraLegion integration application in Okta, deactivating a user means removing access to login, but maintaining the user's NeuraLegion information as an `inactive` user.
- **Reactivate Users**. User accounts can be reactivated for the NeuraLegion integration application in Okta.
- **Push Groups**. Groups and their members in Okta can be pushed to the linked NeuraLegion organization. 

## Requirements

- The NeuraLegion integration with Okta is available to Pro and Enterprise users only. To learn how to upgrade your plan, please read [Manage Your Plan](/docs/manage-your-plan).
- For the setup, you will require to create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) with the `scim` scope and copy its value.

## Step-by-step configuration guide

### Provisioning setup in the Bright app

1. In the **ORGANIZATION SETTINGS**, select the option **Sync the group & users from your SSO provider to NexPloit**.  
   Please note that this option is only available for Okta SSO configured via the SAML protocol.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/efe0e93-sync-checkmark.png",
        "sync-checkmark.png",
        1904
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) with the `scim` scope and copy its value.

### Provisioning setup in Okta

1. In your NeuraLegion integration application, open the **Provisioning** tab and scroll down to the **{app_name} Attribute Mappings** section.
2. Set the attribute mappings to the following:

- `userName`
- `givenName`
- `familyName`
- `email`
- `displayName`

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f238d64-image-20211028-082134.png",
        "image-20211028-082134.png",
        1542
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. From the **Settings** menu, select **Integration**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6dcb0e3-integration-tab.png",
        "integration-tab.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. In the **SCIM connector base URL** field, enter `<https://app.neuralegion.com/api/v1/scim`>. If you are using the NeuraLegion App on a private cloud, specify your custom cluster in the following format: `<https://{clusterName}.neuralegion.com/api/v1/scim`>.
5. Set the **Unique identifier field for users** to `UserName`.
6. Enable pushing new users, profile updates and groups by selecting the relevant checkboxes. 
7. In the **Authorization** field, paste the API key created in the NeuraLegion App, and then click **Save**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/550c719-scim-url.png",
        "scim-url.png",
        1892
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### User provisioning

Once you complete the provisioning setup, every new user assigned to the NeuraLegion integration application will be automatically added to the relevant NeuraLegion organization. 

### Group provisioning

Group provisioning from Okta to the NeuraLegion App is only enabled by pushing every group manually.

To push a group to your NeuraLegion organization, follow these steps: 

1. Assign the group you want to push to the NeuraLegion integration application.
2. In the **Push Groups** tab, click **Push Groups**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4904ccd-push-groups.png",
        "push-groups.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Select the group you want to push to your NeuraLegion organization and click **Save**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/72dcb1e-save-push.png",
        "save-push.png",
        1899
      ],
      "sizing": "80"
    }
  ]
}
[/block]



If you need to deprovision a group from your NeuraLegion organization, delete the group from the NeuraLegion integration application in Okta, and then unlink this group in the Push Groups tab.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/54b8335-unlink-pushed-group.png",
        "unlink-pushed-group.png",
        1892
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Known issues/troubleshooting

Please contact our support team at [support@neuralegion.com](mailto:support@neuralegion.com) if you encounter any issues with NeuraLegion/Okta integration.