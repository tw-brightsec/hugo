---
title: "Configuring Form Authentication"
slug: "configure-form-authentication"
hidden: false
metadata: 
  description: "The form authentication type is set by default when you create an authentication object in the NeuraLegion App."
createdAt: "2021-09-03T11:24:49.542Z"
updatedAt: "2022-10-18T07:19:47.370Z"
---
> ❗️ Deprecation notice
> 
> The **Form authentication** type is deprecated. Your existing authentication objects of this type are currently working, and later will be converted in to the **Custom API authentication** objects automatically.

You can use the form authentication if the login-protected resources within the application you want to scan use<br> the `application/x-www-form-urlencoded` content type of the HTTP requests. 

The form authentication type is set by default when you create an authentication object in the Bright app.  

> 📘 Note
> 
> This topic describes only how to fill in fields specific for form authentication (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/configuring-authentication).

> 📘 Note
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via the Repeater.

From the **Authentication type** dropdown list, select **Form authentication**, and then proceed to the authentication setup. 

#### Authentication setup

In this section, set up a valid authentication request to be sent to the end-point API by completing the provided fields. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d65222b-form-auth-setup.png",
        "form-auth-setup.png",
        1402
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<table id=\"simple-table\">\n<style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>URL</b></td>\n    <td width=\"75%\" >\n        Enter the relevant URL for the HTTP request. The POST method is set by default for the form authentication.<br><br>\n        <font color=\"green\"><b>Pro Tips:</b></font>\n        <ul>\n            <li>\n                This is <b>not</b> the URL where the login form resides, but the URL where the form request is sent to. The form host URL can be the same as the request URL, but can be different as well. You can get the <b>Request URL</b> in the <b>Headers</b> section of the relevant login request.\n            </li>\n            <li>\n                Form login type will encode any URL-encoded values as required by the protocol, this means that values (user, pass) should be entered without encoding to avoid double encoding issues.\n            </li>\n        </ul>\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Parameter name</b></td>\n    <td width=\"75%\" >\n        Enter the form parameters from the request body. For example, username and password.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Parameter value</b></td>\n    <td width=\"75%\" >\n        Enter the values of the form parameters (credentials) from the request bodies.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Maximum number of redirects to follow</b></td>\n    <td width=\"75%\" >\n        Enter the maximum number of redirects that the Bright should follow during the authentication process.<br></br>\n <font color=\"green\"><b>Pro Tips:</b></font> Select the checkbox <b>Change redirected method to get</b> for the redirects with code 302, where the server expects the following methods to always be GET during redirects and not the original method that triggered the redirect.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Additional headers</b></td>\n    <td width=\"75%\" >\n        <em>(Optional)</em> Select an additional header you need to use for each request and enter its value.  For example, additional cookies that might be needed for the authentication such as host-related metadata.<br> To replace or append the selected header before sending each request, select the corresponding option from the <b>Merge strategy</b> dropdown list.<br><br>\n        <font color=\"green\"><b>Pro Tips:</b></font>\n        <ul>\n            <li>\n                Make sure that the values you use for the additional headers are static and must not be changed between scans.\n            </li>\n            <li>\n                If your application uses cookies that are set via the Set-Cookie header in the response, then you do not need to extract and reuse the cookies. Any Set-Cookie header will be automatically used during authentication.  \n            </li>\n             <li>\n                There are cases when MFA is required  ONLY on initial IP login. This means that our scan IP can be validated once and will not require any further MFA validations. For that case, you need to identify which cookie supports the completed MFA/2FA and include a valid cookie as a part of your authentication object, typically using the <b>Additional Headers</b> field.  \n            </li>\n        </ul>\n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



- You can add as many parameters as you need by clicking **+ Add item** at the bottom of the **Parameter Name & Value** section. 
- To delete a parameter, click <img src="https://files.readme.io/d6f5fdd-delete-icon.png" width="24" height="23"> next to the corresponding parameter field.

#### Valid authentication response

In this section, select the options you want to use during the application scanning to determine that the authenticated resource has been reached. The options define how the application responds in case a full authentication flow passes successfully.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/37ea796-auth-response.png",
        "auth-response.png",
        1556
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<table id=\"simple-table\">\n<style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n  <tr>\n    <td width=\"25%\"><<b>Detect using Response STATUS</b></td>\n    <td width=\"75%\" >\n       Enter the HTTP response status that will tell you about the authentication success.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response HEADER pattern</b></td>\n    <td width=\"75%\" >\n        Enter the header name and Regex pattern that will help you identify the authentication success.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response BODY pattern</b></td>\n    <td width=\"75%\" >\n       Enter the body pattern that will help you identify the authentication success.\n    </td>\n  </tr>\n</table>\n </body>"
}
[/block]



#### Authentication triggers

In this section, select the options you want to use during the application scanning to determine if the authentication flow is no longer valid and the authenticated resources cannot be reached. The options define how the application responds in case the authentication flow fails.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/30c225e-auth-triggers.png",
        "auth-triggers.png",
        1410
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<table id=\"simple-table\">\n<style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response patterns</b></td>\n    <td width=\"75%\" >\n       Select if your application explicitly indicates the authentication session expiration in the body or headers, or using status codes.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><li><b>Detect using Response STATUS</b></li></ul></td>\n    <td width=\"75%\" >\n       Enter the HTTP response status that will tell you about the authentication failure.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><li><b>Detect using Response HEADER pattern</b></li></ul></td>\n    <td width=\"75%\" >\n        Enter the header name and Regex pattern that will help you identify the authentication failure.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><li><b>Detect using Response BODY pattern</b></li></ul></td>\n    <td width=\"75%\" >\n       Enter the body pattern that will help you identify the authentication failure.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Request patterns</b></td>\n    <td width=\"75%\" >\n           Select if your application does not provide any explicit indication in the body or headers when the session expires, but the client-side code redirects you to the login page, for example, based on absence of cookies or cookies expiration. In this case the only way to detect the re-login requirement is by detecting the redirect to the login URL.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><li><b>Detect using Request URL pattern</b></li></ul></td>\n    <td width=\"75%\" >\n       Enter the URL pattern that will help you identify the authentication failure.\n    </td>\n  </tr>\n</table>\n </body>"
}
[/block]



> 📘 Note
> 
> Bright allows testing a scan before saving it. For details, see the [Testing Authentication](https://docs.brightsec.com/docs/configuring-authentication#testing-authentication).