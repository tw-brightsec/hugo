---
title: "GitLab Boards"
slug: "gitlab-boards"
hidden: false
metadata: 
  description: "Your guide to GitLab Boards"
createdAt: "2021-09-16T15:02:18.598Z"
updatedAt: "2023-01-04T09:36:27.010Z"
---
[block:html]
{
  "html": "<table id=\"integrations\" >\n   <style>\n #integrations {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n #integrations td,\n  th {\n    border: 0px solid #ddd;\n    padding-left: 0px;\n    background-color: #FFFFFF;\n  }\n  </style>\n  <body>\n  <tr>\n    <td width=\"70%\">\n      \n    </td>\n    <td width=\"30%\" style=\"text-align:center\" rowspan=\"3\">\n      <img src=\"https://files.readme.io/9369e75-gitlab-int.png\" width=\"170\" height=\"200\"></img>\n    </td>\n  </tr>\n  <tr>\n    <td style=\"text-align:left;vertical-align:text-top;padding:0px\">\n      You can connect your GiLab repository to a Bright scan to get the reports on every detected vulnerability in automatically opened GitLab issues. Each report provides the following information:\n      <ul>\n        <li>Issue severity level</li>\n        <li>Details of discovery</li>\n        <li>Possible exposure</li>\n        <li>Remediation suggestions </li>\n      </ul>\n      For each new scan, you can select any of your GitLab repositories integrated with your Bright projects.\n    </td>\n  </tr>\n  <tr><td></td></tr>\n</table>\n</body>\n"
}
[/block]



## Setup

To enable the integration, you should first register the Bright application in GitLab.

1. Go to your GitLab account preferences. For that, in the upper-right corner, click the down-arrow and select **Preferences**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f45930e-preferences.png",
        "preferences.png",
        1915
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the left pane, select **Applications**.
3. On the **Applications** page, do the following:  
       a) In the **Name** field, enter a name for the integration application, for example, **Nexploit**.  
       b) In the **Redirect URI** field, enter `<https://app.brightsec.com/organization/services/gitlab/callback`>.  
       c) In the **Scopes** section, select the **api** checkbox.  
       d) Click **Save application**.  
         The created **Application ID** and **Secret** will then be required for enabling the integration in the [Bright app](https://app.neuralegion.com).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a371b91-created-application.png",
        "created-application.png",
        1877
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Step-by-step guide

### Connecting Bright to your GitLab repository

1. Go to the [Bright app](https://app.neuralegion.com).
2. In the left pane, select **Organization**. 
3. On the **Organization** page, scroll down to the **TICKET MANAGEMENT INTEGRATION** section.
4. Click <img src="https://files.readme.io/60c9313-dots-button.png" width="23" height="26"> next to **GitLab**, and then select **Settings**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/02dd4f6-gitlab-settings.png",
        "gitlab-settings.png",
        1886
      ],
      "sizing": "80"
    }
  ]
}
[/block]



5. In the **GITLAB INTEGRATION CONFIG** dialog box, do the following:  
   a) Copy the **Application ID** and the **Secret** created in GitLab and paste them in the relative fields.  
   b) _(Optional)_. If your GitLab application is hosted on a private cloud or you are using on-premise GitLab, enter the relative link in the **Base URL** field.  
   c) Click **Connect**. You will be redirected to an authorization page on GitLab. Click **Authorize** to allow Bright to access your GitLab account.

<img src="https://files.readme.io/e9e1f12-gitlab-config.png" width="360" height="300">

The Bright connection to GitLab is enabled.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/10a26c6-gitlab-enabled.png",
        "gitlab-enabled.png",
        1906
      ],
      "sizing": "80"
    }
  ]
}
[/block]



#### Configure GitLab Integration with Bright Projects

After you have connected Bright to GitLab, you need to integrate a specific Bright project with your GitLab repository(ies) to be used for a scan. The integration allows Bright to automatically provide the scan reports in the associated GitLab repositories. Moreover, you can select a certain severity level of issues to be sent to the repositories associated with your Bright project.

To integrate a certain Bright project with your GitLab repository(ies), follow [these steps](/docs/add-ticketing-integration-to-a-project).