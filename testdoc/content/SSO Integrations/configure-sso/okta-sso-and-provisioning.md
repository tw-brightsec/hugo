---
title: "Okta SSO and Provisioning"
slug: "okta-sso-and-provisioning"
hidden: false
metadata: 
  description: "Okta integration with NeuraLegion allows users to link their Okta accounts with their NeuraLegion accounts and sign in to the NeuraLegion App via Okta SSO, using the SP-initiated flow."
  image: 
    0: "https://files.readme.io/f2a83d9-NeuraLegionOkta2.png"
    1: "NeuraLegion+Okta2.png"
    2: 1200
    3: 630
    4: "#171e3d"
createdAt: "2021-09-16T06:41:25.499Z"
updatedAt: "2023-01-04T12:45:08.589Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\"> To simplify user access to Bright, you can configure Single Sign-On (SSO) integration with your Okta application. Either the OIDC or SAML protocol can be used to enable Okta SSO.<p></p> You can also take advantage of Okta provisioning feature to automatically synchronize users and groups between your Okta application and Bright organization.<p></p> The provisioning integration is built around an industry-standard protocol known as SCIM (System for Cross-domain Identity Management).  This protocol is design for user management across multiple applications. It allows you to easily provision (add), deprovision (delete) and update (map) user data across multiple applications at once.<p>\n   \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/1532f80-okta-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



You can set up SCIM provisioning in Okta to automatically add the Okta application users and groups to your organization in the Bright App. The added users will be able to access the Bright App using Okta SSO.

Bright supports the following attribute mappings for SCIM provisioning:

- `userName`
- `email`
- `emailType`
- `displayName`

## Enabling Okta SSO via OIDC protocol

## Features

Okta integration with Bright allows users to link their Okta accounts with their Bright accounts and sign in to the Bright app via Okta SSO, using the SP-initiated flow.

## Requirements

The Bright integration with Okta is available to Pro and Enterprise users only. To learn how to upgrade your plan, please read [Manage Your Plan](/docs/manage-your-plan).

## Step-by-step configuration guide

To enable Okta SSO for your Bright organization, follow these steps:

1. Log in to Okta.
2. Browse for the preconfigured [Brightsec integration app](https://www.okta.com/integrations/neuralegion/#overview) in the Okta catalog and add it to your applications. 
3. When onboarding, in the **General Settings** tab, set your subdomain and click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/506296e-okta-subdomain.png",
        "okta-subdomain.png",
        1567
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. In the **Sign-On Options** tab, select **OpenID Connect**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c4f14d6-select-oidc.png",
        "select-oidc.png",
        1593
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the **Credentials Details** section, set the **Application username format** to **Email**, and then click **Done**.  
   The Brightsec integration app is set up. 
6. In the **Assignments** tab, assign users to the app.  
   The assigned users will then get SSO access to the Bright app.
7. In the **Sign On** tab, get the credentials of the created app to authorize it in the Bright app:

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



8. Log in to the Bright app.
9. In the left pane, select the **Organization** option, and go to the **ORGANIZATION SETTINGS** section.
10. From the **Single sign on (SSO) Authentication** dropdown list, select **Okta**, and then click **Connect**.

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



11. On the **OKTA AUTHENTICATION** page, do the following:

- Select the **Default Role** the new members will be assigned to.
- Select the **OIDC** protocol. 
- Enter the **Client ID**, **Client Secret** and **Metadata URL** copied from the Brightsec integration app in Okta.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/94eafa6-okta-auth.png",
        "okta-auth.png",
        1888
      ],
      "sizing": "80"
    }
  ]
}
[/block]



12. Click **Save settings**.  
    After Okta SSO is set up, an email is sent to all the users of your Bright organization suggesting to confirm their accounts and link their Okta profiles to the Bright profiles. Once the accounts are linked, the users can log in to the Bright app using the Okta SSO option.
13. _(Optional)_ You can enforce SSO registration by selecting the **Require your organization members to use SSO to access Bright** checkbox. When this option is selected, only the registered users (current members of a Bright organization) with existing SSO accounts can access the Bright app.

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
> Strict enforcement of SSO for all organization members will require resetting the connection in case of an SSO break. If that happens, please contact the [Bright technical support](mailto:support@brightset.com) for assistance.

14. On the login page of the Bright app, click **Single Sign On (SSO)**.

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



15. Enter your Bright organization name and click **Continue**.
16. Select **Sign in with Okta**.  
    You are redirected to the Okta login page.
17. Enter your Okta credentials and click **Sign In**.

## Known issues/troubleshooting

Please contact our support team at [support@brightsec.com](mailto:support@brightsec.com) if you encounter any issues with Bright/Okta integration.

## Enabling Okta SSO via SAML protocol

## Features

Okta integration with Bright allows users to link their Okta accounts with their bright accounts and sign in to the Bright app via Okta SSO, using the SP-initiated flow.

## Requirements

The Bright integration with Okta is available to Pro and Enterprise users only. To learn how to upgrade your plan, please read [Manage Your Plan](/docs/manage-your-plan).

## Step-by-step configuration guide

To enable Okta SSO for your Bright organization, follow these steps:

1. Log in to Okta.
2. Browse for the preconfigured [Brightsec integration app](https://www.okta.com/integrations/neuralegion/#overview) in the Okta catalog and add it to your applications. 
3. When onboarding, in the **General Settings** tab, set your subdomain and click **Next**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/30df28a-okta-subdomain.png",
        "okta-subdomain.png",
        1567
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. In the **Sign-On Options** tab, select **SAML 2.0**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5388a85-select-saml.png",
        "select-saml.png",
        1595
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the **Credentials Details** section, set the **Application username format** to **Email**, and then click **Done**.  
   The Brightsec integration app is set up. 
6. In the **Assignments** tab, assign users to the app.  
   The assigned users will then get SSO access to the Bright app.
7. In the **Sign On** tab, get the metadata of the created application to authorize it in the Bright app. For that, click **Indetity Provider Metadata** and copy its URL.

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



8. Log in to the Bright app.
9. In the left pane, select **Organization**, and go to the **ORGANIZATION SETTINGS** section.
10. From the **Single sign on (SSO) Authentication** dropdown list, select **Okta**, and then click **Connect**.

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



11. On the **OKTA AUTHENTICATION** page, do the following:

- Select the **Default Role** the new members will be assigned to.
- Select the **SAML** protocol. 
- Enter the **Metadata URL** copied from the Brightsec integration app in Okta.

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



12. Click **Save settings**.  
    After Okta SSO is set up, an email is sent to all the users of your Bright organization suggesting to confirm their accounts and link their Okta profiles to the Bright profiles. Once the accounts are linked, the users can log in to the Bright app using the Okta SSO option.
13. _(Optional)_ You can enforce SSO registration by selecting the **Require your organization members to use SSO to access Bright** checkbox. When this option is selected, only the registered users (current members of a Bright organization) with existing SSO accounts can access the Bright app. 

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

14. On the login page of the Bright app, click **Single Sign On (SSO)**.

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



15. Enter your Bright organization name and click **Continue**.
16. Select **Sign in with Okta**.  
    You are redirected to the Okta login page.
17. Enter your Okta credentials and click **Sign In**.

## Known issues/troubleshooting

Please contact our support team at [support@brightsec.com](mailto:support@brightsec.com) if you encounter any issues with Bright/Okta integration.

## Enabling SCIM provisioning between Okta and Bright

## Features

The following provisioning features are currently supported by Bright:

- **Push New Users**. Users created in Okta and assigned to the Brightsec integration application in Okta are automatically added as members to the linked organization in the Bright app.
- **Push Profile Updates**. Updates made to the user's profile through OKTA will be pushed to the Bright app.
- **Push User Deactivation**. Deactivating the user or disabling the user's access to the Brightsec integration application through OKTA will deactivate the user in the Bright app.  
  _Note:_ For the Brightsec integration application in Okta, deactivating a user means removing access to login, but maintaining the user's Bright information as an `inactive` user.
- **Reactivate Users**. User accounts can be reactivated for the Brightsec integration application in Okta.
- **Push Groups**. Groups and their members in Okta can be pushed to the linked Bright organization. 

## Requirements

- The Bright integration with Okta is available to Pro and Enterprise users only. To learn how to upgrade your plan, please read [Manage Your Plan](/docs/manage-your-plan).
- To configure the provisioning flow, first you need to enable Okta SSO for your Bright organization via the OIDC or SAML protocol. Please see the guides above for the detailed instructions.
- For the provisioning setup, you will require to create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) with the `scim` scope and copy its value.

## Step-by-step configuration guide

### Provisioning setup in the Bright app

1. In the **ORGANIZATION SETTINGS**, select the option **Sync the group & users from your SSO provider to Bright**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/25a86e7-SSO-syn.png",
        "SSO-syn.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Create an [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or a [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) with the `scim` scope and copy its value.

### Provisioning setup in Okta

1. In your Brightsec integration app, open the **Provisioning** tab and click **Configure API integration**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c9dae7b-provision.png",
        "provision.png",
        1709
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Select the **Enable API integration** checkbox, and then enter the **API token** copied from the Bright app.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/064a046-enable-api.png",
        "enable-api.png",
        1802
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Click **Save**.
5. In the **Provisioning to App** section, enable the provisioning options you will need by selecting the relevant checkboxes, and then click **Save**.  
   The provisioning setup is completed.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2f49622-provision-setup.png",
        "provision-setup.png",
        1820
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### User provisioning

Once you complete the provisioning setup, every new user assigned to the Brightsec integration app will be automatically added to the relevant Bright organization. 

### Group provisioning

Group provisioning from Okta to the Bright app is only enabled by pushing every group manually.

To push a group to your Bright organization, follow these steps: 

1. Assign the group you want to push to the Brightsec integration app.
2. In the **Push Groups** tab, click **Push Groups**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/948b2ae-group-active.png",
        "group-active.png",
        1896
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Select the group you want to push to your Bright organization and click **Save**.

If you need to deprovision a group from your Bright organization, delete the group from the Brightsec integration application in Okta, and then unlink this group in the **Push Groups** tab.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/52712fb-group-deactiv.png",
        "group-deactiv.png",
        1892
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Known issues/troubleshooting

Bright does not support special symbols for `userName`. If the `userName` of an Okta user contains special symbols, they will be sanitized when signing in to a Bright organization via SSO.  For example, “#John Do\`e¥” will be signed in to Bright as "John Doe”.

Please contact our support team at [support@brightsec.com](mailto:support@brightsec.com) if you encounter any issues with Bright/Okta integration.