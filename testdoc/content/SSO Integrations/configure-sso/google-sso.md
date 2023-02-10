---
title: "Google SSO"
slug: "google-sso"
hidden: false
metadata: 
  description: "The SSO option becomes available once Google SSO is configured for the organization"
createdAt: "2021-09-16T06:20:47.041Z"
updatedAt: "2022-12-08T13:27:51.459Z"
---
[block:html]
{
  "html": "<table id=\"integrations\">\n  <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/952f890-google-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      To simplify user access to Bright solutions, you can configure Single Sign-On (SSO) for Google.\n    </td>\n  </tr>\n  <tr>\n  <td>\n  <h3>Enable Google SSO for Your Nexploit Organization</h3>\n  </td>\n  </tr>\n  <tr>\n  <td>\n  To enable Google SSO for an organization, follow these steps:\n  </td>\n  </tr>\n</table>\n</body>"
}
[/block]



1. Log in to the [Bright app](https://app.brightsec.com).
2. In the left pane, select the **Organization** option, and go to the **ORGANIZATION SETTINGS** section.
3. From the **Requires SSO provider**, select **Google**, and then click **Connect**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6b42048-google-sso.png",
        "google-sso.png",
        1910
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. On the **GOOGLE AUTHENTICATION** page, do the following:

   - From the **Default Role** dropdown list, select the default role to which users are assigned upon their first login.

   - In the **Domain** field, specify the domain to be used by users when logging in.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a2dca22-auth-google.png",
        "auth-google.png",
        1920
      ],
      "sizing": "80"
    }
  ]
}
[/block]



6. Click **Continue**.  
   You are redirected to the Google login page. 

7. Sign in to your Google account.

8. _(Optional)_ You can enforce SSO registration by selecting the **Require your organization members to use SSO to access Bright** checkbox. When this option is selected, only the registered users (current members of a Bright organization) with existing SSO accounts can access the Bright app.

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

### Logging to Bright with Google SSO

The SSO option becomes available once Google SSO is configured for the organization.

To log in to Bright using Google SSO, follow these steps:

1. On the login page, click **Single Sign On (SSO)**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/52a3f26-sso-button.png",
        "sso-button.png",
        1914
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Enter your Bright organization name and click **Continue**.

3. Select **Sign in with Google**.  
   You are redirected to the Google login page.

4. Enter your Google credentials.