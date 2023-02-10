---
title: "Configuring OIDC Connect (OAuth)"
slug: "configure-oidc-connect-oauth"
hidden: false
metadata: 
  description: "If you need to grant NeuraLegion access to the authenticated resources that support OIDC, you should configure an authentication object using the OpenID Connect."
createdAt: "2021-09-03T14:49:42.770Z"
updatedAt: "2023-01-04T11:24:54.094Z"
---
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FgrZlK9WYJkY%3Fstart%3D2%26feature%3Doembed%26start%3D2&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DgrZlK9WYJkY&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FgrZlK9WYJkY%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=grZlK9WYJkY&t=2s",
  "title": "Creating an OpenID Connect Authentication Object",
  "favicon": "https://www.youtube.com/s/desktop/21ad9f7d/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/grZlK9WYJkY/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=grZlK9WYJkY&t=2s"
}
[/block]




The OIDC (OAuth) authentication method is designed to configure the standard OAuth 2.0 flow, which requires the use of client or user secrets. 

> 📘 Note
> 
> Currently only the **Customer Credentials** and **Resource Owner Password** grant types of the OIDC are supported.

> 📘 Note
> 
> This topic describes only how to fill in fields specific for OIDC connect (OAuth) (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/configuring-authentication)).

> 📘 Note
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via the Repeater.

From the **Authentication type** dropdown list, select **OpenID Connect (OAuth)**, and then proceed to the authentication details. 

#### Authentication details

In this section, set up a valid authentication request to be sent to the end-point API by completing the provided fields. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/b25e263-oidc-setup_2.png",
        "oidc-setup (2).png",
        1558
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:parameters]
{
  "data": {
    "h-0": "**Field**",
    "h-1": "**Guidelines**",
    "0-0": "**Discovery document URL**",
    "0-1": "Provide a discovery document URL (<https://your_host/.well-known/openid-configuration>) to populate endpoint URLs automatically or leave this field empty to enter endpoint URLs manually.",
    "1-0": "**Grant type**",
    "1-1": "From the drop-down list, select the grant type you need:  \n- Client Credentials Grant  \n- Resource Owner Password Grant  \n  \nIf you select the **Resource Owner Password Grant**, the **Username** and **Password** fields are added to the setup flow.",
    "2-0": "**Token Endpoint**",
    "2-1": " Obtain an access and/or ID token by presenting an authorization grant or refresh token.",
    "3-0": "**Client ID**",
    "3-1": " Enter your application client ID, unique client identifier preregistered in OpenID Provider.",
    "4-0": "**Client Secret**",
    "4-1": " Enter your application client secret, used to authenticate to the Token Endpoint.",
    "5-0": "**Username**",
    "5-1": " Enter the resource owner username.",
    "6-0": "**Password**",
    "6-1": " Enter the resource owner's password.",
    "7-0": "**Scope**",
    "7-1": "_(Optional)_ Enter a space-separated list of scopes.",
    "8-0": "**Audience**",
    "8-1": "_(Optional)_ Enter the intended recipient of the token.",
    "9-0": "**Embed in**",
    "9-1": "Select where to embed the token in the request.  \n  \n- If the **Default** option is selected, the token is embedded according to the OIDC specification. For example, a token can be embedded in the authorization header with the Bearer prefix.  \n- If you select the **Body** option, specify the token encoder, content type, exact location in the body, and the token template string.  \n- If you select the **Header** option, specify the token encoder, the name of the target header, and the token template string."
  },
  "cols": 2,
  "rows": 10,
  "align": [
    "left",
    "left"
  ]
}
[/block]

#### Valid authentication response

In this section, select the options you want to use during the application scanning to determine that the authenticated resource has been reached. The options define how the application responds in case a full authentication flow passes successfully.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c4ed3a3-valid-response.png",
        "valid-response.png",
        1560
      ],
      "sizing": "80"
    }
  ]
}
[/block]



| **Field**                                | **Guidelines**                                                                                                                                                                                                                           |
| :--------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Detect using Response STATUS**         | Enter the HTTP response status that will tell you about the authentication success.                                                                                                                                                      |
| **Detect using Response HEADER pattern** | Enter the header name and Regex pattern that will help you identify the authentication success. For example, you can use a simple Regex pattern, such as `index`.                                                                        |
| **Detect using Response BODY pattern**   | Enter the body pattern that will help you identify the authentication success. For example, this Regex pattern detects a body looking for a UUID in a `sessionId` parameter: `sessionId: \"\\b(uuid:){0,1}\\s_([a-f0-9\\-]_){1}\\s\*\"`. |

> 📘 Note
> 
> Bright allows testing a scan before saving it. For details, see the [Testing Authentication](https://docs.brightsec.com/docs/configuring-authentication#testing-authentication).