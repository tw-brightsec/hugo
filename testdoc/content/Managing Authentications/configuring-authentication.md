---
title: "Creating Authentication"
slug: "configuring-authentication"
hidden: true
createdAt: "2022-07-11T12:54:11.578Z"
updatedAt: "2022-11-22T07:35:22.752Z"
---
> 📘 
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via a Repeater.

# Configuring authentication

1. From the menu in the left pane of the [Bright app](https://app.neuralegion.com), select **Authentications**.
2. In the **Authentications** pane, click **+ Create Authentication**. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/5e3bc42-1e1f425-dbcf47a-create-auth.png",
        "1e1f425-dbcf47a-create-auth.png",
        1918
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. In the **Create authentication** dialog, fill in the fields as described below.
4. After filling in all the necessary fields, in the right-bottom corner of the **Create Authentication** dialog, click **Create**.

> 📘 
> 
> - The **Create authentication** window contains three tabs: **Details**, **Setup**, and **Logout Indicators**. Use the menu in the right pane of the dialog to switch between the tabs.
> - All mandatory fields are marked with an asterisk (\*).
> - Bright allows testing a scan before saving it. For details, see the [Testing Authentication](#testing-authentication) section below.

## The Details tab

### Details

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/52379f2-5931c32-auth-details.png",
        "5931c32-auth-details.png",
        1557
      ],
      "sizing": "80"
    }
  ]
}
[/block]



Specify the details of the authentication object you want to create.

| Field                   | Guidelines                                                                                                                                                          |
| :---------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Authentication name** | Enter the authentication object name.                                                                                                                               |
| **Description**         | Enter the authentication object description. For example, you can specify the application type or other information that helps you distinguish your created object. |

### Protected resource details

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/343a813-35f2022-protected-resource.png",
        "35f2022-protected-resource.png",
        1553
      ],
      "sizing": "80"
    }
  ]
}
[/block]



Provide the details of the authentication-protected resource.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Guidelines",
    "0-0": "**Protocol**",
    "0-1": "From the dropdown list, select the **HTTPS** or **WebSockets** (currently under development) protocol to be used for authentication.",
    "1-0": "**Method**",
    "1-1": "Select the HTTP method of an active tester end-point (authenticated resource).",
    "2-0": "**Validation URL**",
    "2-1": "Enter the URL of the authenticated (protected) resource to test if the authentication scenario is configured correctly. The validation URL should be different from the authentication URL.",
    "3-0": "**Merge Strategy**",
    "3-1": "Select whether the specified header must be replaced or appended with the provided value before sending each request.",
    "4-0": "**Name**",
    "4-1": "Select an additional header to be replaced or appended before sending each request, for example, Authorization.",
    "5-0": "**Value**",
    "5-1": "Enter the header value.",
    "6-0": "**Body**",
    "6-1": "Enter the HTTP request body to be sent in the request sent, for example: `{“user”: “foo”, “pass”: “bar”}`",
    "7-0": "**Maximum number of redirects to follow**",
    "7-1": "Enter the maximum number of redirections that Bright should follow during the authentication process.  \n  \n_Pro Tips_: Select the checkbox **Change redirected method to get** for the redirects with code `302`, where the server expects the following methods to always be `GET` during redirects and not the original method that triggered the redirect.",
    "8-0": "**WebSocket frame payload extractor regex**",
    "8-1": "The functionality is currently under development, please skip this field.",
    "9-0": "**XPath to the request identifier field**",
    "9-1": "The functionality is currently under development, please skip this field.",
    "10-0": "**Repeater**",
    "10-1": "If you use a local Repeater to reach the scan target, select it from the dropdown list to connect it to the scan."
  },
  "cols": 2,
  "rows": 11,
  "align": [
    "left",
    "left"
  ]
}
[/block]

## The Setup tab

This tab allows setting authentication details.

From the **Authentication type** dropdown list, select the necessary authentication type, and then proceed to the authentication details. For information on how to fill in the fields for the selected authentication type, follow the relevant link below.

### Valid authentication types

- [Browser-based form authentication](/docs/configure-multi-step-browser-based-form-authentication)
- [Recorded browser-based form authentication](/docs/configure-recorded-browser-based-form-authentication)
- [Header authentication](/docs/configure-header-authentication-in-nexploit)
- [OpenID connect (OAuth)](/docs/configure-oidc-connect-oauth) 
- [Custom API authentication call](/docs/configure-custom-multi-step-authentication) 
- [NTLM authentication](/docs/configure-ntlm-authentication)

### Deprecated authentication types

- [API call](/docs/configure-api-call-authentication)
- [Form authentication](/docs/configure-form-authentication)

For more information on each authentication type, see [Authentication Types](docs/creating-an-authentication-object-in-nexploit).

## The Logout Indicators tab

This section contains the options to be used during the application scanning to determine if the authentication flow is no longer valid and the authenticated resources cannot be reached. The options define how the application responds in case the authentication flow fails.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/f102a7c-Logout_indicators_tab.png",
        null,
        ""
      ],
      "sizing": "650px"
    }
  ]
}
[/block]



| **Field**               | Guidelines                                                                                                                                                                                                                                                            |
| :---------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Response status**     | Select the checkbox and then enter the HTTP response status that will tell you about the authentication failure.                                                                                                                                                      |
| **Header pattern**      | Select the checkbox and then enter the header name and Regex pattern that will help you identify the authentication failure. For example, you can use a simple Regex pattern, such as `index`.                                                                        |
| **Bode pattern**        | Select the checkbox and then enter the body pattern that will help you identify the authentication failure. For example, this Regex pattern detects a body looking for a UUID in a `sessionId` parameter: `sessionId: \"\\b(uuid:){0,1}\\s_([a-f0-9\\-]_){1}\\s\*\".` |
| **Page pattern**        | Select the checkbox and then specify CSS selector(s) or inner text selector(s) that match page element(s) to be used as logout indicator(s).                                                                                                                          |
| **Request URL pattern** | Select the checkbox and then enter the URL pattern that will help you identify the authentication failure.                                                                                                                                                            |

# Testing authentication

Preliminary authentication testing helps you verify if the authentication object has been configured correctly. This allows you to reveal the configuration issues timely, before running a scan.

To test your authentication object, at the bottom of the **Create authentication** dialog, click **Test authentication**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/42d44d2-e30ce0b-test-auth.png",
        "e30ce0b-test-auth.png",
        1560
      ],
      "sizing": "80"
    }
  ]
}
[/block]



The application displays the test results in a separate **Test results** tab. 

- A valid authentication object returns three success messages indicated in the relevant  **Test results** sections: 
  - **Test Authentication Triggers** provides the test request and response data.
  - **Authentication call (fillForm #)** provides a screenshot of the form filled by the engine per stage.
  - **Authentication call (submitForm #)** provides a screenshot of the authenticated page as evidence of the successful login.
  - **Authentication call (Check Post-Login URL)** provides a screenshot of the post-login URL as evidence of the successful login.
  - **Access Protected Resource** provides the test request and response data.

In this case, you can save the configured object and add it to your scans.

- If the test results include a failure message, go back to the object configurations and verify their correctness. Use the test request/response data to find a certain failure and fix it.

> 📘 
> 
> The Bright engine only supports the `set-cookie` headers that are less than 4097 bytes. If the received header exceeds this limit, the engine will ignore the header and will not include it in the request/response data.  Breaking the limit may also cause authentication object failure.