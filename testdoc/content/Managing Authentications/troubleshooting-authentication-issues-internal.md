---
title: "Troubleshooting Authentication Issues"
slug: "troubleshooting-authentication-issues-internal"
hidden: false
createdAt: "2022-08-15T12:15:56.410Z"
updatedAt: "2022-12-08T06:59:49.688Z"
---
# Recording created with Google Chrome recorder is not replayed with the Evaluation failed error

When replaying the recording, an error appears: _Evaluation failed. TypeError: Failed to execute ‘observe’ on ‘IntersectionObserver’: parameter 1 is not type ‘Element’…_

![](https://files.readme.io/428c8d4-1.png "1.png")

### Cause

Google Chrome cannot find the element by one of the selectors.

### Workaround

1. Expand the step where the error appears.
2. Click “**\-**” against the affected selector to delete it.

![](https://files.readme.io/49d47bf-2.png "2.png")

3\. Replay the recording.

4\. If the replay is encountering the same errors, repeat steps 1-2 till the replay is successful.

# Recording created with Google Chrome recorder is not replayed because UID was changed

Some web applications specify a UID in the element name. Since web applications are frequently releasing new features, UID might change, which will cause the authentication object not working. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1b1998a-4.png",
        "4.png",
        658
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Solution

Remove the UID from the recording to create a generic authentication object that would work even if a new web application is released.

1. Expand the step containing UID.
2. Delete the UID.  

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bf5edba-5.png",
        "5.png",
        991
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 📘 Note
> 
> For creating recording, see [Configuring Recorded Browser-Based Form Authentication](https://docs.brightsec.com/docs/configure-recorded-browser-based-form-authentication).

# Surface discovery

[block:html]
{
  "html": "<table id=\"simple-table\">\n   <style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  </style>\n  <body>\n    <tr>\n        <th><strong>Indicators of this issue</strong></th>\n    </tr>\n</table>\n  </body><div></div>\n\n<style></style>"
}
[/block]



- Response statuses include:
  - `NexPloit::Session::AuthFlow::Error`
  - `401`
  - `405`
- Percentage of problematic statuses out of the total responses >10%

[block:html]
{
  "html": "<table id=\"simple-table\">\n   <style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  </style>\n  <body>\n    <tr>\n        <th><strong>Configuration problems</strong></th>\n    </tr>\n</table>\n  </body>"
}
[/block]



- The authentication object is configured incorrectly.
- The wrong authentication object is selected for the scan.
- The scan requires more than one type of authentication object.
- Some specific entry points may need different authentication parameters (like HMAC headers).

[block:html]
{
  "html": "<table id=\"simple-table\">\n   <style>\n #simple-table {\n    border-collapse: separate;\n    width: 100%;\n    display: block;\n    display: table;\n  }\n#simple-table th {\n    padding: 1.5%;\n    text-align: left;\n    vertical-align: text-top;\n    background-color: #B2D6DA;\n  </style>\n  <body>\n    <tr>\n        <th><strong>Remediation suggestions</strong></th>\n    </tr>\n</table>\n  </body>"
}
[/block]



- Create an authentication object that follows the design and flow of authorization within your web application. Bright has different types of authentication objects that can be used in scans. For detailed information, see our documentation - [Authentication Types](doc:creating-an-authentication-object-in-nexploit).
- Check the configuration of the exiting authentication object. For example, if you are using a Custom API Authentication object, check the validity of the regex and validate if your authorization data is correct. You can find more about regex in our documentation - [String Interpolation Syntax](doc:string-interpolation-syntax).
- Check if there is a need for an HMAC script for additional authorization (if more headers are needed). In the Repeater script, you should specify how exactly the server calculates the HMAC code to allow Bright to provide a valid HMAC token. Bright can reach targets ONLY after a successful HMAC authorization with the relative server. For more information, see our documentation - [Using Repeater Scripts](doc:repeater-scripts).

> 📘 Note
> 
> If you need help with this issue, contact our support at [support@brightsec.com](mailto:support@brightsec.com) or via Intercom at the bottom right of the Bright app.

# An authorization flow can not be done successfully

While adjusting the TOTP in the authorization flow, sometimes the process can not be done successfully. An error will be shown at the step with OTP. 

### Solution

Try to change the type to Google Authenticator or vice versa.

# How to set up the HOTP server counter

While using HOTP, a configured authentication server that will not increase the number of HOTP counters after each successful one-time iteration is needed.

### Solution

To do this, the start counter on the server must be 0. Thus, the counter will increase by 1 after creating the first code and binding it to the server. Next generated codes will use the counter value = 1 on both the server and the Auth object.