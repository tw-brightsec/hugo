---
title: "Configuring NTLM Authentication"
slug: "configure-ntlm-authentication"
hidden: false
metadata: 
  description: "If the target network uses the NTLM protocol to verify user’s access rights, you need to set up an NTLM authentication object."
createdAt: "2021-09-03T14:14:50.867Z"
updatedAt: "2022-11-02T13:41:28.901Z"
---
If the target network uses the NTLM protocol to verify the user’s access rights, you need to set up an NTLM authentication object. The protocol requires a user to be authenticated by providing a username and a corresponding password. After the user’s log-in credentials are recognized, the network can then check access rights and allow the user to enter. 

Therefore, you can grant  Bright access to an NTLM authenticated network you are going to use for a scan by providing your credentials, workstation name, and the network domain. 

> 📘 Note
> 
> This topic describes only how to fill in fields specific for NTLM authentication (the **Setup** tab). For general steps, see [Creating Authentication](https://docs.brightsec.com/docs/configuring-authentication).

> 📘 Note
> 
> Before following the instructions below, ensure that your application and authenticated resources are accessible to the Bright engine, either directly from the Internet or via the Repeater.

From the **Authentication type** dropdown list, select **NTLM authentication**, and then proceed to the authentication details. 

#### Authentication details

In this section, set up a valid authentication request to be sent to the end-point API by completing the provided fields. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/650c8c3-ntlm-setup.png",
        "ntlm-setup.png",
        1556
      ],
      "sizing": "80"
    }
  ]
}
[/block]



| Field           | Guidelines                                                                                                              |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------- |
| **Username**    | Enter the NTLM username.                                                                                                |
| **Password**    | Enter the NTLM password.                                                                                                |
| **Domain**      | Enter the domain of the NTLM network you need to get access to.                                                         |
| **Workstation** | Enter your workstation name, _for example_, a computer name. The maximum length of a workstation name is 64 characters. |



> 📘 Note
> 
> Bright allows testing a scan before saving it. For details, see the [Testing Authentication](https://docs.brightsec.com/docs/configuring-authentication#testing-authentication).