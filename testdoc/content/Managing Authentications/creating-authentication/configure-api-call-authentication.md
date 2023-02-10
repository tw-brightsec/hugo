---
title: "Configuring API Call Authentication"
slug: "configure-api-call-authentication"
hidden: false
metadata: 
  description: "If you need to enable NeuraLegion to reach an authenticated resource by sending API requests with a customized body, you should use the API call authentication method."
createdAt: "2021-09-03T13:31:09.459Z"
updatedAt: "2022-10-18T07:15:29.606Z"
---
> ❗️ Deprecation notice
> 
> The **API call** authentication type is deprecated. Your existing authentication objects of this type are currently working, and later will be converted in to the **Custom API authentication** objects automatically.

The API call authentication method is designed to enable Bright to reach an authenticated resource by sending API requests with customized request queries, headers and bodies, requiring the use of dynamic information between steps (such as CSRF tokens).

> 📘 Note
> 
> This topic describes only how to fill in fields specific for API call authentication (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/configuring-authentication).

> 📘 Note
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via the Repeater.

From the **Authentication type** dropdown list, select **API call** and then proceed to the authentication setup. 

#### Authentication setup

In this section, set up a valid authentication request to be sent to the end-point API by completing the provided fields. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/689ad62-api-call-setup.png",
        "api-call-setup.png",
        1564
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<table id=\"simple-table\">\n  <style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Method</b></td>\n    <td width=\"75%\" >\n       Enter the HTTP method of the relevant API end-point.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>URL</b></td>\n    <td width=\"75%\" >\n    Enter the URL of the relevant API end-point.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Body</b></td>\n    <td width=\"75%\" >\n        Enter the HTTP request body to use with the request sent to the API end-point, for example:{“user”: “foo”, “pass”: “bar”}’.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Extract from</b></td>\n    <td width=\"75%\" >\n        Select where in the responses the correct authentication token should be extracted from.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><li><b>Header</b></li></ul></td>\n    <td width=\"75%\" >\n        Select if you need the authentication token to be extracted from the response header.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><b>Header name</b></ul></td>\n    <td width=\"75%\" >\n        Enter the name of the header to extract the authentication token from.\n    </td>\n  </tr>\n   <tr>\n    <td width=\"25%\"><ul><li><b>Body</b></li></ul></td>\n    <td width=\"75%\" >\n        Select if you need the authentication token to be extracted from the response body.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Authenticated token extraction regex</b></td>\n    <td width=\"75%\" >\n        Enter the Regex pattern that extracts the authentication token from the specified location.<br><br>\n      <font color=\"green\"><b>Pro Tip:</b></font> Make sure the specified Regex captures ONLY the token itself, and not any additional parts of the string such as prefix, suffix, delimiter, padding, etc.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Token encoder</b></td>\n    <td width=\"75%\" >\n        Select any encoder that you need to use on the token itself, for example Base64.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Embed in</b></td>\n    <td width=\"75%\" >\n        Select where in the subsequent authenticated requests the authentication token should be embedded in to.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><li><b>Header</b></li></ul></td>\n    <td width=\"75%\" >\n        Select if you need the authentication token to be embedded in to the request header.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><b>Target header name</b></ul></td>\n    <td width=\"75%\" >\n        Enter the name of the header to embed the authentication token in to.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><li><b>Body</b></li></ul></td>\n    <td width=\"75%\" >\n        Select if you need the authentication token to be embedded in to the request body.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><ul><b>Content type</b></ul></td>\n    <td width=\"75%\" >\n        Select the content type of the request body.<br><br>\n        <font color=\"blue\"><b>Note:</b></font> Currently only `application/json` is supported.\n    </td>\n  </tr>\n   <tr>\n    <td width=\"25%\"><ul><b>XPAth</b></ul></td>\n    <td width=\"75%\" >\n        Enter the exact path to the object to be used in the requests sent to the API end-point.\n    </td>\n  </tr>\n   <tr>\n    <td width=\"25%\"><b>Token template string</b></td>\n    <td width=\"75%\" >\n        Enter the expected token and final pattern to be embedded in to the end-point request header or body.<br><br>\n        <font color=\"green\"><b>Pro Tip:</b></font> The required syntax is to have the `{{token}}` string in the field, along with any needed prefixes/suffixes. The `{{token}}` part will be replaced with the extracted token from the authentication response.\n    </td>\n  </tr>\n   <td width=\"25%\"><b>Maximum number of redirects to follow</b></td>\n    <td width=\"75%\" >\n        Enter the maximum number of redirections that the NeiraLegion should follow during the authentication process.\n    </td>\n  </tr>\n   <tr>\n    <td width=\"25%\"><b>Additional headers</b></td>\n    <td width=\"75%\" >\n        <em>(Optional)</em> Select an additional header that you need to use for each request and enter its value. For example, additional cookies that might be needed for the authentication, such as host-related metadata.<br>To replace or append the selected header before sending each request, select the corresponding option from the <b>Merge strategy</b> dropdown list.<br><br>\n         <font color=\"green\"><b>Pro Tips:</b></font>\n        <ul>\n            <li>\n                If your application uses cookies that are set via the Set-Cookie header in the response, then you do not need to extract and reuse the cookies. Any Set-Cookie header will be automatically used during authentication.  \n            </li>\n             <li>\n                MFA required on initial IP login may be handled using a cookie value. For that, you need to identify which cookie holds the completed MFA/2FA and include a valid cookie as a part of your authentication object.  \n            </li>\n        </ul>\n    </td>\n  </tr>\n  </table>\n</body>"
}
[/block]



- You can add as many header as you need by clicking **+ Add header** at the bottom of the **Authentication Setup** section. 
- To delete a header, click <img src="https://files.readme.io/d6f5fdd-delete-icon.png" width="24" height="23"> next to the corresponding header field.

#### Valid authentication response

In this section, select the options you want to use during the application scanning to determine that the authenticated resource has been reached. The options define how the application responds in case a full authentication flow passes successfully.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/63ab146-auth-response.png",
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
  "html": "<table id=\"simple-table\">\n<style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n    </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response STATUS</b></td>\n    <td width=\"75%\" >\n       Enter the HTTP response status that will tell you about the authentication success.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response HEADER pattern</b></td>\n    <td width=\"75%\" >\n        Enter the header name and Regex pattern that will help you identify the authentication success.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response BODY pattern</b></td>\n    <td width=\"75%\" >\n       Enter the body pattern that will help you identify the authentication success.\n    </td>\n  </tr>\n  </table>\n </body>"
}
[/block]



#### Authentication triggers

In this section, select the options you want to use during the application scanning to determine if the authentication flow is no longer valid and the authenticated resources cannot be reached. The options define how the application responds in case the authentication flow fails.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2875320-auth-triggers.png",
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