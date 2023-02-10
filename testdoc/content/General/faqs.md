---
title: "FAQs"
slug: "faqs"
hidden: false
metadata: 
  description: "During a scan, NeuraLegion collects both application data and user data, which are used as part of the scan"
createdAt: "2021-08-20T10:56:42.650Z"
updatedAt: "2023-01-04T11:18:26.475Z"
---
## Data security

### What kind of information does Bright access **during** a scan?

During a scan, Bright collects both application data and user data, which are used as part of the scan:

- Application Data – Refers to anything related to the application structure and functionality, such as parameter names and object structures. Collectively, this information is used to determine the application's attack surface.
- User Data – Refers to specific user information, such as parameter values or authentication data. This information is used to improve the scan quality and results, as well as to identify parameter types and automatically log in, as needed.

### What kind of information does Bright store **after** a scan?

Bright cloud engine does not store the customer’s user data after the scan. User data obtained during a scan is stored solely in memory and is deleted as the scan ends. Application data is stored anonymously after a scan in order to improve Bright’s machine learning engines.

In addition, Bright stores scan results after a scan. This data is not directly available to Bright unless the customer shares it with Bright.

### How does Bright ensure data security and privacy?

At Bright the security and privacy of our customers are our top priority. Our cloud engine does not retain or store any customer information. Private data is temporarily in memory and deleted after the scan ends. We follow the industry's best practices in managing data, including but not limited to encryption, access regulations, and data separation (private separate instance for each scan per client).

### Your clients generate data as they use your solutions, what part of that information are you exposed to?

Bright is a SaaS based product, the traffic requires a communication channel between the Bright engine and scanned target. However, that channel is controlled by the customer, Bright does not have access to the channel traffic (private data) generated during the scan such as: found issues, private user data, and others.

Required sensitive data generated or used during a scan is temporarily stored in run-time memory, and is deleted at the scan conclusion.

### Will Bright share the finding reports with anyone else?

No. Only the customer has access to their reports. Customers can choose to download reports or to use them within our system. Customers have complete control over access permissions to these reports.

Be aware that once scans are removed from the system, they are permanently deleted. This means that after scans are removed from the system, Bright has no access to them and cannot restore the deleted information.

### Why aren’t there any false positives?

Bright solutions do not simply scan, but rather interact with the target application. This means that every reported vulnerability is validated in real time. If a vulnerability cannot be validated, it is not reported, thereby saving you from unnecessary noise and hours of manual labor.

### Will Bright have access to the vulnerabilities (issues) that it detects in my applications?

A Bright representative cannot access your scan results without your permission. If support is needed, then an organization’s owner can invite a Bright engineer to access your vulnerabilities in order to provide support.

## Before scanning

### What are the pre-conditions / technical steps / requirements to scan an application with Bright?

To scan your application, Bright requires access to the target, which means  that you need to:

1. Select the target you want to scan (make sure our SaaS environment has access to it).  
   For internal targets (within your private environment), please add our [static IP address](/docs/saas-deployment#before-you-begin) to allowlist on your WAF / firewall.
2. Select a discovery method (Crawler, HAR recording or OpenAPI schema).
3. Provide a URL to the target, .HAR file or OpenAPI schema respectively to initiate the scan.  
   For more information, see [Quickstart](/docs/quickstart).

### What is a target? What constitutes a target for Brights solutions?

A target is a website, web application, server or network device that you would like to scan for security vulnerabilities using one of the other Bright solutions.

## Scanning

### Do the scans need to be operated manually?

They can be run manually, however we recommend that for optimal efficiency they either be run as part of the SDLC component, using a REST API hook to call a scan, or automatically by configuring a scanning schedule.

### How much time does a scan usually take?

Scan time depends on several key factors:

- Size of the target application, or in other words: how big is the attack surface?
- Intensity of the scan, or in other words: how many requests per second are sent to the target?  
  From our experience, a medium-size application that is being scanned with a low-level intensity can take a few hours. Contact our support to learn how to optimize a scan strategy to best fit your needs, and yes, it is possible to do a scan in only a few minutes!

### How many scans is it possible to run?

The number of scans is not limited, however each concurrency is limited to 1 scan at a time with others going in to a queue and starting after the first completes.

### We have different branches of the application - how do we deal with that?

Since we are using dynamic testing, interacting with a live (running) application, it doesn't matter to our products how many / which branches an application is using. We are testing the application as a whole, including any sub-applications or microservices it might use. That being said, you have full control of the scope of the scan, and can decide not to scan certain parts of an application. If developers want to only test specific parts of their code they can test those parts using a .HAR file.

### What do you test related to GraphQL? What is Bright approach to this?

As an alternative to REST, GraphQL lets developers get data from multiple data sources with a single query. If implemented and tested properly, GraphQL is an extremely elegant methodology for data retrieval, where “if implemented and TESTED properly” is the key condition to be met. Otherwise, GraphQL may turn in to a source of critical security vulnerabilities.   

Bright allows you to test your GraphQL for any potential vulnerabilities as part of a .[HAR file](/docs/scanning-with-a-har) or a [Postman collection](/docs/scanning-api-endpoints). When scanning GraphQL endpoints inside a Postman collection, a user must specify all required environmental variables (types, fields, mutations, and so on). This will enable Bright to fully determine the scan surface and reach complete scan coverage of the target. The variables are usually specified during scan configuration. To learn more about the Postman configuration validation, read [here](/docs/troubleshooting#postman-schema-validation-checklist). 

One of the biggest benefits of Bright is that you can deploy full depth parsing, meaning that you can parse varying interactive definitions (in this case, a good example would be an XML object inside a GraphQL query). To put it simply, Bright parses the input parameters and tries to manipulate them as an attacker would do. Any type of parameters can be parsed by Bright. 

In the following example, such parameters will be `username`, `new_password`, `reset_token`:

```text
mutation ResetPassword {
  passwordReset(input: {username:"Helena_Simonis", new_password: "RTest!", reset_token:{gt:""}}) {
    username
  }
}
```



The API backend queries the database to check if the token was correct, directly passing the username and reset token values that haven’t been properly checked from the input. If the input is not properly validated, the attacker can reset the password and get access to secret data, or even change it. 

This is only one example of the attacks that can be executed on your GraphQL. To learn about the most common GraphQL security attacks and best practices, read our [blog post](https://brightsec.com/blog/graphql-security/?utm_content=182132619&utm_medium=social&utm_source=twitter&hss_channel=tw-904376285635465217). For more information about GraphQL, refer to the [GraphQL documentation](https://graphql.org/learn/).

## Scanning APIs

## How to make sure the API file is formatted correctly?

API specifications (swagger or postman collection) have specific formatting guidelines that they must follow. You can check your swagger files for compatibility using editor.swagger.io and for postman collections you should use the postman software which can be downloaded from [www.postman.com](https://www.postman.com/).

## Scanning with a .HAR

### What is the purpose of a .HAR file?

A .HAR file (HTTP Archive) is a recording of the traffic between a client and a server of an application, which includes requests and responses. But it is possible to start a scan with other methods as well such as a Crawler, and OpenAPI/Swagger schema or directly from Unit Testing. 

Using a .HAR file provides us with several key benefits:

- Provides our solutions with a full understanding of a modern application's structure and parameters
- Gives our solution real context understanding of the target (what data is expected by the application)
- Allows you to have full control of the scope of the scan  
  To learn how to create a .HAR file, watch [our video](https://www.youtube.com/watch?v=HMpBQ7JkxHI&t=1s).

### I ran two scans against the same target, but the number of discovered entry-points were very different. How can you explain the difference?

When scanning the same application with the same attack surface, there should be the same scan results. However, there may be differences between two separate scans that affect the attack surface. 

The most common issue is authentication ("dead session"). If you used an [authentication object](https://docs.neuralegion.com/docs/creating-an-authentication-object-in-nexploit) for a scan, the difference in the number of entry-points might be caused by expired credentials. In that case, the attack surface was not defined completely for the second scan, since the engine couldn’t access the authenticated parts of the target. Another reason why some entry-points could not be found during another scan is the network connectivity issues. Please verify that the connection to the network wasn’t lost.  

Other possibilities include:

- Changes to the application itself (code). The entry-points detected during the first scan no longer exist on the target.
- Changes to the application environment (configuration, network, etc.). Bright allows configuring the limit to entry-point response duration, which is 1000 ms by default. If the response takes longer than the predefined time (for example, due to some target configuration changes), Bright will skip that entry-point. You can change the limit in the **Scan Targets** tab of the **New Scan** window, but this will affect the scan speed.

### I ran two scans against the same target, but the number of detected security issues were very different. How can you explain the difference?

When scanning the same application with the same attack surface, there should be the same scan results. However, there may be differences between two separate scans that affect the attack surface. 

- First, you should compare the number of entry-points discovered during the scans.  
  If the number is different, it means that the issues located in the omitted entry-points were not counted. See the previous question to learn why the number of entry-points might be different. 
- If the number of entry-points is the same, you should consider the reason that some issues had already been fixed before the second scan was run. 

### If I have a large application, can I automate the .HAR recording process?

Yes, you can use QA automation or Proxy tools to record .HAR files automatically. In addition, you can add a Crawler to your scan that will fill in the missing parts of the target application that were not covered in the session recording. However, the interactions from the Crawler are not saved in the .HAR file.

A single .HAR file is limited to 500MB, so it is recommended to split scans of big applications in to several separate sessions. To learn how to create a .HAR file, watch [our video](https://www.youtube.com/watch?v=HMpBQ7JkxHI&t=1s).

### What is the maximum allowed storage for uploaded .HAR files in your platform?

Default user storage is 200Mb, this can be increased if needed by contacting our support.

## Private cloud deployment

### Will using a private cloud mean that I don’t need to use the Repeater?

If the only reason for using the Repeater is to control network flow, and if a site2site VPN tunnel can be created that enables full access from the private cloud to the organization’s network, then the Repeater is not needed. Otherwise, the Repeater is still needed in order to enable secure access to a local target from the cloud.

### Do I still need to use allowlist in my firewall if I have a private cloud?

Yes, you must use allowlist in your firewall with a private cloud, unless a site-to-site VPN is configured and used.

### Can I use a private data center instead of a private cloud?

You cannot use a private data center instead of a private cloud. This option is not supported at this time.

## Scanning targets in a private environment

### Our servers are internal without any external access. How can I connect to Bright solutions?

Our solutions are SaaS based, all traffic to and from it requires an open communication channel between the scan engine and the scanned target.

For internal systems, you can use the [Repeater (local proxy agent)](/docs/on-premises-repeater-local-agent) that can be installed to relay the scan traffic to and from the target. 

### Our application has a firewall - can Bright solutions work with this?

Yes, you need to open a port for our [static IP address](/docs/saas-deployment#before-you-begin) and configure the firewall to allow-list it.

### Can I integrate Bright solutions with my CI/CD pipeline? Do they have an automatic mode?

Yes, Bright can be integrated with many popular SDLC tools and frameworks. In addition, Bright provides a REST API to set automatic slots for scans without a need for manual intervention.

Find more information on the available integrations [here](/docs/integrate-nexploit-with-your-ci-pipeline).

### What is the maintenance / patching frequency for the Repeater?

The Bright engine does not require any maintenance or patching from the client side. It is in the cloud and therefore is always updated automatically. 

The Repeater does require periodic updates. These can be performed either manually (using a simple CLI update command) or automatically (if the Repeater is installed during a build as part of the CI process).

### Can I use a single machine with the Repeater in order to access multiple internal targets?

Yes, on the condition that the local machine on which the Repeater is installed has access to the internal applications. In this case, multiple scans can be performed using the same Repeater.

In addition, by installing the Repeater on a personal computer, it is possible to scan locally running applications. This is useful for developers who want to perform quick tests without deploying code.

### Can I use one Bright Repeater to handle several concurrent scans or do I have to have a dedicated repeater per scan?

One Repeater can handle multiple scans concurrently. And a single Repeater can be used to connect to multiple Bright engines with distributed concurrent scans among the engines.

### Do I need to change firewall / port settings for the Repeater?

No. Using the Repeater does not require any changes to your network’s inbound traffic settings, because  all the generated traffic is based on outbound requests from inside the network.

### I have a firewall between various internal applications. How do I handle this?

You have the following options, to:

- Install a separate Repeater behind the relevant firewalls in order to avoid the need for allow-listing.
- Use open ports between the internal applications.
- Configure new ports for the Repeater.

### Will a firewall affect the scan results or add false positives?

The Repeater does not contain any complicated logic. All decision making and removal of false-positives using active validation is performed by the engine in the cloud. This means that all the computational and advanced algorithms are available to scans that use the Repeater, in the same way as for scans that are deployed as a SaaS or in the private cloud.

## Authentications

### Can your solution automatically login to the application again? How do you deal with authentication?

Bright supports different [types of authentication](/docs/creating-an-authentication-object-in-nexploit). By creating an authentication object in the Bright App and connecting it to a scan, you enable Bright to access the authenticated resources within your applications and APIs. 

### How to deal with CAPTCHA and/or one-time passwords (OTP) while scanning

During scanning, Bright sends hundreds of requests per minute to the target. If a request is rejected, Bright re-authenticates and continues the scan. The problem appears when the authentication form includes Captcha and/or OTP, which are dynamic by their nature and require “manual actions” (for example, submitting SMS and PIN codes, clicking emailed links or checkboxes for verification, and so on). 

Our engine must be able to re-authenticate automatically to maintain continuity of the scanning process, while Captchas and OTPs break this process. 

There are several solutions on how to set up Bright to properly authenticate and scan targets with Captchas and OTPs: 

- If it’s possible, **set OTP to static value**, so Bright can use the same OTP every time in the authentication flow.
- When configuring an authentication object, you can **use an internal login form** that is uninhibited with Captchas/OTPs, for example, like a QA team may use. 
- If there is some API call which Bright can use to get the token dynamically, then create a **Custom API authentication object** and retrieve that token dynamically.
- If your development team can create functionality to skip OTP provided that some kind of **parameter is added to the URL as a URL query**, Bright can use that too and **incorporate it in the authentication object**.

## Access privileges

### Are there different user rights / access privileges in your systems? How are they configured?

As an admin, you have full discretion to determine users, admins and other access roles, each has specific privileges. Bright allows you to create custom roles with different access scopes and assign them to new or existing users. Read more about managing user’s roles [here](/docs/manage-custom-roles).

## SSO

### How does a user login for the first time in an org with active SSO?

The user should follow the link in the email invitation they have received, then click on “create user using email”, fill out their details on the next screen and then log in with their SSO service.

## Other

### What QA testing suite do you integrate with / import from (besides Selenium)?

We can support any test suite that can export a .HAR file (HTTP archive), including Charles, Selenium, Appium, PhantomJS, and even unit testing.

### What kind of reports can I get from Bright?

Bright provides multiple reports, including but not limited to executive summaries and technical reports containing detailed explanations of findings, threats, and remedies.  As a SaaS product, all reports can be downloaded at any time by the client and are useful for developers, QAs, and CISOs to understand and fix the findings.