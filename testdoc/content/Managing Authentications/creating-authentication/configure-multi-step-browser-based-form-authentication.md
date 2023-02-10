---
title: "Configuring Browser-Based Form Authentication"
slug: "configure-multi-step-browser-based-form-authentication"
hidden: false
createdAt: "2022-01-06T11:23:41.837Z"
updatedAt: "2022-10-18T07:12:14.252Z"
---
> 📘 Note
> 
> We recommend that you use [Recorded Browser-Based Form Authentication](https://docs.brightsec.com/docs/configure-recorded-browser-based-form-authentication) method for creating these type of authentication.


[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2Fb5QP6u4w3UM%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Db5QP6u4w3UM&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2Fb5QP6u4w3UM%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=b5QP6u4w3UM&feature=emb_logo",
  "title": "Creating a Browser-Based Authentication Object",
  "favicon": "https://www.youtube.com/s/desktop/df3209e6/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/b5QP6u4w3UM/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=b5QP6u4w3UM&feature=emb_logo"
}
[/block]




You can grant Bright access to the login-protected pages of your application by specifying the form fields with the corresponding valid credentials to be entered in to those fields. Using this data, Bright automatically completes the form in the same way you would do it to gain access to the protected pages. You are also able to configure a browser-based authentication object for multi-step login forms.

> 📘 
> 
> This topic describes only how to fill in fields specific for browser-based form authentication (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/configuring-authentication).

> 📘 Note
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via the Repeater.

1. From the **Authentication type** dropdown list, select **Browser-based form authentication**.
2. To configure a valid authentication request to be sent to the end-point API, fill in the fields as described below.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/69afab6-280d834-auth-setup.png",
        "280d834-auth-setup.png",
        1556
      ],
      "sizing": "80"
    }
  ]
}
[/block]



[block:html]
{
  "html": "<table id=\"simple-table\">\n<style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  }\n\n  #simple-table td {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n  }\n\n  #simple-table tr:nth-child(odd) {\n    background-color: #FFFFFF;\n  }\n\n  #simple-table tr:nth-child(even) {\n    background-color: #F4F6F7;\n  }\n  </style>\n  <body>\n  <tr>\n    <th width=\"25%\"><b>Field</b></th>\n    <th width=\"75%\"><b>Guidelines</b></th>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Form page URL</b></td>\n    <td width=\"75%\" >\n        Enter the URL of the page where the form is located.\n    </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Stage #</b></td>\n    <td width=\"75%\" >\n        Each stage represents a separate login page. Add as many stages as the login flow consists of by clicking <b>+ Add stage</b> below the <b>Form submission</b> section. To change the order of the stages, simply drag-and-drop them using the <img src=\"https://files.readme.io/71ef6b1-drag-icon.png\" width=\"21\" height=\"23\"> icon to the left of the stage name.  <br></br>\n      \t<b>Stage type</b> Use the default <b>Form interaction</b> type unless the login page loads longer than 30 seconds (the generic timeout of the system). For a long-loading page, select the <b>Standby</b> type and specify the time for Bright to wait before to take the next step. Once the specified time is over, Bright sends a screenshot of the current state of the page. You can find it in the test authentication results.<br></br>\n    \t\tElements represent the fields, buttons and other types of input given on the login page. Simply fill in the elements names and types as you see them on the login page and provide the valid values for them.\n     <ul>\n       <li>You can add as many elements as you need by clicking <b>+ Add item</b> in the lower-left corner of the section.</li>\n       <li>To delete an element, click <img src=\"https://files.readme.io/d6f5fdd-delete-icon.png\" width=\"23\" height=\"23\"> next to the corresponding element.</li>\n      </ul>\n    <b>Form submission</b> allows you to select the action that must be performed to submit the form.\n     <ul>\n      <li> If you have a single-stage login form, or you need to press <b>Enter</b> to switch to the next login page, select the <b>Press Enter</b> option.</li>\n      <li>If you need to click a button to switch to the next login page, select the <b>Click button</b> option and enter the relevant button name. </li>\n     </ul>\n      </td>\n  </tr>\n  <tr>\n    <td width=\"25%\"><b>Expected URL after successful login</b></td>\n    <td width=\"75%\" >\n        URL of the page that should open after successful login.\n    </td>\n  </tr>\n</table>\n</body>"
}
[/block]



> 📘 Note
> 
> Bright allows testing a scan before saving it. For details, see the [Testing Authentication](https://docs.brightsec.com/docs/configuring-authentication#testing-authentication).