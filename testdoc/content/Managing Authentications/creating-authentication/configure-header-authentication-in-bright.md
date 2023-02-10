---
title: "Configuring Header Authentication"
slug: "configure-header-authentication-in-bright"
hidden: false
metadata: 
  description: "You can use the header authentication method if the login-protected resources within the application you want to scan require one or more static header authentication tokens."
createdAt: "2021-09-03T11:01:02.589Z"
updatedAt: "2022-12-05T10:24:24.448Z"
---
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FUxVaWMy6-CE%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DUxVaWMy6-CE&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FUxVaWMy6-CE%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=UxVaWMy6-CE",
  "title": "Creating a header authentication object",
  "favicon": "https://www.youtube.com/s/desktop/b422c796/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/UxVaWMy6-CE/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=UxVaWMy6-CE"
}
[/block]




You can use the header authentication method if the login-protected resources within the application you want to scan require one or more static header authentication tokens, which are generated outside of Bright.

> 📘 Note
> 
> In case a specified authentication token expires, the authentication object will no longer provide Bright with the ability to reach authenticated resources of that particular target.

> 📘 Note
> 
> This topic describes only how to fill in fields specific for header form authentication (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/configuring-authentication).

From the **Authentication type** dropdown list, select **Header authentication**, and then add the authentication **Headers**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8de6551-headers.png",
        "headers.png",
        1561
      ],
      "sizing": "80"
    }
  ]
}
[/block]



| Field              | Guidelines                                                                                                                         |
| :----------------- | :--------------------------------------------------------------------------------------------------------------------------------- |
| **Merge Strategy** | Select whether the specified header must be replaced or appended before sending each request, for example, authentication cookies. |
| **Name**           | Select an additional header to be replaced or appended before sending each request, `Authorization`.                               |
| **Value**          | Enter the header value.                                                                                                            |

- You can add as many headers as you need by clicking **+ Add header** at the bottom of the **Headers** section. 
- To delete a header, click <img src="https://files.readme.io/d6f5fdd-delete-icon.png" width="24" height="23"> next to the corresponding header field.

> 👍 Tip
> 
> There are cases when MFA is required  ONLY on initial IP login. This means that our scan IP can be validated once and will not require any further MFA validations. For that case, you need to identify which cookie supports the completed MFA/2FA and include a valid cookie as a part of your authentication object.

> 📘 Note
> 
> Bright allows testing a scan before saving it. For details, see the [Testing Authentication](https://docs.brightsec.com/docs/configuring-authentication#testing-authentication).