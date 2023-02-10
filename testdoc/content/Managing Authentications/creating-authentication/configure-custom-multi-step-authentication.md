---
title: "Configuring Custom API Authentication Flow"
slug: "configure-custom-multi-step-authentication"
hidden: false
metadata: 
  description: "If you need to create a custom authentication flow consisting of multiple stages, you should use the custom multi-step authentication method."
createdAt: "2021-09-03T14:31:21.398Z"
updatedAt: "2023-01-04T09:43:47.783Z"
---
The custom API authentication method is designed to easily create a single or multi-stage authentication flow.  During the authentication object configuration, you can also create templates to extract dynamic information from the previous steps, easily performed by using the [String Interpolation Syntax](https://docs.neuralegion.com/docs/string-interpolation-syntax).

> 📘 Note
> 
> This topic describes only how to fill in fields specific for custom API authentication (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/creating-authentication#the-advanced-tab).

> 📘 Note
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via the Repeater.

From the **Authentication type** dropdown list, select **Custom API authentication flow**, and then proceed to the authentication details. 

#### Authentication Details

In this section, build the authentication flow. You can create a single-stage flow or add as many stages as the Bright engine should pass through to access the authenticated resource. To change the order of the stages, simply drag-and-drop them using the <img src="https://files.readme.io/71ef6b1-drag-icon.png" width="21" height="23"> icon to the left of the stage name. 

Start the setup with creating the first stage. In the **Name** field, enter the stage name that can be used further for creation of interpolation expressions. 

#### Request

In this section, set up a valid authentication request to be sent to the end-point API. For that, complete the **Authentication Setup** fields.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9ad7ca2-custom-multi-step.png",
        "custom-multi-step.png",
        1560
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Guidelines",
    "0-0": "**Protocol**",
    "0-1": "From the drop-down list, select the **HTTPS** or **WebSockets** protocol to be used for authentication.",
    "1-0": "**Method**",
    "1-1": "Enter the HTTP method of the relevant API end-point.",
    "2-0": "**URL**",
    "2-1": "Enter the URL of the relevant API end-point. The URL can contain an interpolation string that you can create using the [String Interpolation Syntax](https://docs.brightsec.com/docs/string-interpolation-syntax).",
    "3-0": "**Headers**",
    "3-1": "Enter an additional header that you may need to use for each request and specify its value. You can interpolate the header name and value using the [String Interpolation Syntax](https://docs.brightsec.com/docs/string-interpolation-syntax). _For example_, a value of an `Authorization` header can be retrieved from an application response header as `{{stage1.response.headers|get:\\\"Authorization\\\"}}`.  \nTo replace or append the specified header before sending each request, select the corresponding option from the **Merge Strategy** drop-down list.",
    "4-0": "**Body**",
    "4-1": "Enter the HTTP request body to use it with the request sent to the API end-point, _for example_:` {“user”: “foo”, “pass”: “bar”}`. You can interpolate the body using the [String Interpolation Syntax](https://docs.brightsec.com/docs/string-interpolation-syntax). For example, a value of a token can be retrieved from an application response body as `username=admin&password=password&Login=Login&user_token={{ stage1.response.body | match: /value=.(.{32})./ }}`.",
    "5-0": "**Maximum number of redirects to follow**",
    "5-1": "Enter the maximum number of redirections that Bright should follow during the authentication process.  \n  \n**_Pro Tips_**: Select the checkbox **Change redirected method to get** for the redirects with code 302, where the server expects the following methods to always be GET during redirects and not the original method that triggered the redirect."
  },
  "cols": 2,
  "rows": 6,
  "align": [
    "left",
    "left"
  ]
}
[/block]

- You can add as many headers as you need by clicking **+ Add header** at the bottom of the **Headers** section. 
- To delete a header, click <img src="https://files.readme.io/d6f5fdd-delete-icon.png" width="24" height="23"> next to the corresponding header field.

#### Valid authentication response

In this section, select the options you want to use during the application scanning to determine that the authenticated resource has been reached. The options define how the application responds in case a full authentication flow passes successfully.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/aa30fd5-valid-response.png",
        "valid-response.png",
        1560
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<table id=\"simple-table\">\n<style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response STATUS</b></td>\n    <td width=\"75%\" >\n       Enter the HTTP response status that will tell you about the authentication success.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response HEADER pattern</b></td>\n    <td width=\"75%\" >\n        Enter the header name and Regex pattern that will help you identify the authentication success.<font color=\"darkblue\">For example</font>, you can use a simple Regex pattern, such as <code>index</code>.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Detect using Response BODY pattern</b></td>\n    <td width=\"75%\" >\n       Enter the body pattern that will help you identify the authentication success.<font color=\"darkblue\"> For example</font>, this Regex pattern detects a body looking for a UUID in a <code>sessionId</code> parameter: <code>sessionId: \\\"\\b(uuid:){0,1}\\s*([a-f0-9\\\\-]*){1}\\s*\\\"</code>.\n    </td>\n  </tr>\n</table>\n </body>"
}
[/block]



To add another stage required for authentication, click **+ Add another Stage**.

#### Authorized requests setup

In this section, specify the values to be added to each request sent to the authenticated resource.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/673c8d8-request-setup.png",
        "request-setup.png",
        1558
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<table id=\"simple-table\">\n  <style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Headers </b></td>\n    <td width=\"75%\" >\n       Specify the name and expected value template of an additional header to be appended to each request. To create the value template, use the <a href=\"/docs/string-interpolation-syntax\">String Interpolation Syntax</a>. \n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Content-Type </b></td>\n    <td width=\"75%\" >\n        Specify the content type of the request body.<br>\n        <font color=\"blue\"><b>Note:</b></font> Currently only <code>application/json</code> is supported.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>XPath to parameter</b></td>\n    <td width=\"75%\" >\n       Specify the exact location of the parameter in the object sent with the requests to the target.<font color=\"darkblue\">For example</font>, a path to a session token may look like <code>metadata.authorization.sessionToken</code>.\n    </td>\n  </tr>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Value</b></td>\n    <td width=\"75%\" >\n       Specify the template of the expected value (interpolation string) to be embedded into the target parameter. To create the value template, use the <a href=\"/docs/string-interpolation-syntax\">String Interpolation Syntax</a>. <font color=\"darkblue\">For example</font>, a token template string may look like <code>{{token}}</code>. \n    </td>\n  </tr>\n</table>\n</body>\n"
}
[/block]



- For some parameters, you can add more fields by clicking <img src="https://files.readme.io/134406e-plus-icon.png" width="23" height="26"> at the upper-right of the relevant setup section. 
- To delete a parameter, click <img src="https://files.readme.io/1fbc936-trash-icon.png" width="23" height="23"> to the left of the relevant field.

> 📘 Note
> 
> Bright allows testing a scan before saving it. For details, see the [Testing Authentication](https://docs.brightsec.com/docs/configuring-authentication#testing-authentication).