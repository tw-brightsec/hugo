---
title: "Creating a Scan"
slug: "creating-a-new-scan"
hidden: false
createdAt: "2022-08-18T08:22:22.379Z"
updatedAt: "2022-12-05T11:59:23.965Z"
---
> 📘 Note
> 
> Currently our scans are capped at 2000 entry-points. If you want to get more, please contact our sales at [sales@brightsec.com](mailto:support@neuralegion.com).

To run a security scan against a target, follow these steps:

1. In the left pane, select the **Scans** option to see the list of available scans.
2. In the **Scans** pane, click **Create scan** to create a new scan.

![](https://files.readme.io/7841cbb-.png)

# Specifying scan details

In the  **Details** tab, do the following:

1. In the **Scan name** field, enter any free-text name for the scan.

![](https://files.readme.io/441b3d2-__2022-10-31__09.30.43.png)

2. From the **Project** dropdown list, select the Bright project you want to use for the scan.

> 📘 Note
> 
> You can start a scan ONLY with a project selected. If you do not have any projects in Bright, select the **Default** one.

2. Bright allows users to mark any scans to simplify work with them. Labels can be added in this field, separated by commas. All the added labels will be displayed on the **Scans page** and on the **Configuration tab** in the Scan info page. If there is an existing label from previous scans, start to type it, and then choose from the autocompleted form below. 
   Semicolons and commas are used to separate labels, so It is not allowed to use them in label names. For one scan it is possible to add up to 15 labels, each of them can be up to 255 symbols in length. The ability to add or/and remove labels is limited to `scans`, `scan:run`, and `scan:manage` scopes. 
   > 📘 Note:
   > 
   > It is allowed to change the scan labels after the scan creation on a **Scan editing** page
3. _(Optional)._ Bright provides a list of preconfigured scan templates to help users assess their vulnerabilities quicker and more efficiently. The list is available in the **Scan Template**.  Click **Import configuration** to apply changes. For further details, see [Managing Scan Templates](/docs/managing-scan-templates).

# Defining scan targets

In the **Scan targets** tab, do the following:

1. Choose the scan targets type. Scan targets may be the following types:

**Publicly accessible from Bright's cloud** - Scanning directly from the cloud is allowed for authorized targets only. [Learn more about Target Authorization](https://docs.brightsec.com/docs/target-authorization).

**On a private network or not authorized** - Scanning via CLI in Repeater Mode, provides secure access to local networks or unauthorized targets. 

**Choose repeater** (this option is available only if the "On a private network or not authorized" type is selected) - From the dropdown menu if there are existing ones. To know how to create a new repeater, [Learn more about Repeater Mode](https://docs.brightsec.com/docs/manage-repeaters)

**Use custom DNS records** - Are used to access local, non-public targets. Use it when you want to replace localhost with a specific IP address. [Learn more about Custom DNS records](https://docs.brightsec.com/docs/creating-a-new-scan#custom-dns-records).

_(Optional)_ **Authentication** - Select authentication type. [Learn more about Authenticated scans](https://docs.brightsec.com/docs/creating-an-authentication-object-in-bright).

## Discover entry-points

2. Select a suitable way to discover entry-points while scanning. [Learn more about Entry-points](https://docs.brightsec.com/docs/entry-points).

### For websites and web apps

**Via crawling** - Smart Crawler is a procedure aimed to minimize crawler time. It can skip entry-points with duplicate parameters, and so on. [Learn more about Crawling](https://docs.brightsec.com/docs/creating-a-new-scan#smart-crawling). 

**URL** - Simply enter a URL (target host) to scan the whole or a part of the specified application. The crawler will map the entire application attack surface automatically.

To scan only specific parts of your application or add multiple hosts, click on the right side of the Targets section. In this case, only the specified sections of the application and everything downstream from them will be scanned.

> 📘 Note
> 
> Some hosts may be unreachable or unauthorized for a direct scan from the cloud:
> 
> - If a host cannot be reached by the engine, select a running Repeater for the scan in the Network Settings section. 
> - If a host is unauthorized for a direct scan from the cloud, either select a running Repeater for the scan or add a `.nex` file to the host root directory. ([Learn more about Managing organizations](https://docs.brightsec.com/docs/manage-your-organization#define-the-hosts-authorized-for-scanning)).

![](https://files.readme.io/4acaf77-.png)

**Via a .HAR file** - Use a pre-recorded session of your interaction with the application (HAR file), which has been created either manually or automatically (using QA tools, such as Selenium to scan your application). This discovery type enables you to define the scope of a scan and ensures complete coverage of the attack surface.

  See [Creating a HAR File](https://docs.brightsec.com/docs/creating-a-har-file) to learn how to create a HAR file.

> 📘 Note
> 
> Some hosts may be unreachable or unauthorized for a direct scan from the cloud:
> 
> - If a host cannot be reached by the engine, select a running Repeater for the scan in the section below.
> - If a host is unauthorized for a direct scan from the cloud, either select a running Repeater for the scan or add a \`.nex file to the host root directory. [Learn more about Managing organizations](https://docs.brightsec.com/docs/manage-your-organization#define-the-hosts-authorized-for-scanning).

   See [Scanning a website with a HAR file](https://docs.brightsec.com/docs/scanning-with-a-har) for detailed information.

**Delete the file after it has been sent to the engine for a scan** - Mark this checkbox if you don't want the file to be saved.

> 👍 Tip
> 
> To enjoy both full automation and deeper attack surface analysis, you can combine **Crawling** and **Recording (HAR)** in a single scan.

### For APIs

Via API schema file (for API endpoints)- Use an \*.yml file to scan APIs. See [Scanning API endpoints](https://docs.brightsec.com/docs/scanning-api-endpoints) for detailed information. The file can be chosen from a disc or pre-uploaded to the Bright app. Also, you can simply add a link to the file. 

Delete the file after it has been sent to the engine for a scan - mark this checkbox if you don't want the file to be saved.

![](https://files.readme.io/0867aac-.png)

## Entry-point discovery options

**Skip entry-points, if a response is longer than** - Bright allows configuring the limit to entry-point response duration, which is 1000 ms by default. If the response takes longer than the predefined time (for example, due to some target configuration changes), Bright will skip that entry-point. You can change the limit, but this will affect the scan speed. [Learn more about Entry-points](https://docs.brightsec.com/docs/entry-points).

_(Optional)_.The **Skip entry-points by patterns** section contains an expression that excludes the most common static files like images, audio, video, and other files that don't contain any vulnerabilities (including fonts). If you don't want these files to be excluded, you can clear the **URL regex pattern** field.

In this pane, you may set additional parameters to be ignored during scanning.

- Below the **Method** field, click ** + Add exclusion**. Empty fields will appear. 
- From the **Method** dropdown menu, select the method you want to be excluded from scanning. 
- In the **URL regex pattern** field, enter the parameters for the selected method.

![](https://files.readme.io/9579c6e-.png)

For example, if you don't want the **POST** method to go over entry points that contain _vendor_ in the URL, from the **Method** dropdown menu, select _POST_ and then in the **URL regex pattern** field, enter _vendor_. Any URL which contains _vendor_ will be excluded from scanning.

**CSS & XPath exclusions** - CSS selectors & XPath for links to exclude.

## Target specific settings

In the **Additional Headers** section, define any custom headers to be appended to or replaced in each request. If you need to add some authentication headers, see [Header Authentication](https://docs.brightsec.com/docs/configure-header-authentication-in-bright).

> 👍 Tip
> 
> If you need to add several **Additional headers**, you can copy-paste them in a single **Name** field. The headers will be distributed among the fields automatically.

**Websocket handling settings** - Unlike HTTP(S) WebSockets is an async protocol. Scanning it requires the ability to correlate between specific outgoing-incoming frame pairs. [Learn more about Websocket Scanning](https://docs.brightsec.com/docs/websocket-scanning)

![](https://files.readme.io/b354a1a-.png)

# Selecting test for a scan

In the **Scan Tests** tab, do the following:

- In the **Tests** section, select the tests to be performed during the scan by checking their checkboxes.

![](https://files.readme.io/5788a70-.png)

> 📘 Note
> 
> For details on vulnerabilities that can be detected by Bright, see [Vulnerability Guide](https://docs.brightsec.com/docs/vulnerability-guide).

**Business-logic vulnerability tests** - Advanced, context-specific tests that look for non-trivial vulnerabilities such as using legitimate app flows in a way that results in a negative consequence to the organization, such as stolen user data.

**Third-party tests** - Using third-party tools to find known vulnerabilities (CVEs) in the target.

# Configuring optimizations settings

## Scan performance and speed

**Stop scan, if the target does not respond**  – Set a limit to response duration for the scan target globally. If the specified duration is exceeded, the scan will be stopped automatically. The default value is 5 min.

**Concurrent requests** - Specify the maximum concurrent requests allowed to be sent by the scan in order to control the load on your server. The default value is 10 requests.

![](https://files.readme.io/0c39111-.png)

## Test optimizations

**Use smart scanning for speed optimizations** - Specify whether to use automatic smart decisions (such as parameter skipping, detection phases, and so on) in order to minimize scan time. When this option is turned off, all tests are run on all the parameters, which increases coverage at the expense of scan time. [Learn more about Smart scanning.](https://docs.brightsec.com/docs/creating-a-new-scan#smart-scanning)

**Skip static parameters** - Specify whether to skip static parameters to minimize scan time. [Learn more about Static parameters](https://docs.brightsec.com/docs/creating-a-new-scan#static-parameters).

**Skip parameters by patterns** - You can define which parameters you want to skip in order to improve scan time. [Learn more about Skipping parameters](https://docs.brightsec.com/docs/creating-a-new-scan#skipping-parameters).

**Target parameter locations** - Settings are used to manually point the scanner which parts of the request (address) to attack. 

In most cases, this is enough to provide a high-quality scan. Select all available options if you want the deepest scan and don't care about the long scan time. In this case, the scanner will check all parts of the request (address), which will significantly increase the scanning time. In some cases, this can improve scan results. [Learn more about Target parameter locations](https://docs.brightsec.com/docs/creating-a-new-scan#target-parameter-locations).

![](https://files.readme.io/dac7504-.png)

# Summary and scheduling

**Run a scan now** - Choose this option to start the scan immediately.

**Schedule a single scan for later** - Select a date and time to schedule the scan to run once automatically.

**Create a recurrent scan** – Define the frequency and schedule of the scan to run repeatedly and automatically.

![](https://files.readme.io/6c3fe15-.png)

# Starting a scan

Once you complete the setup, you can run the scan immediately or save it as a template. The template will be saved to the templates list in the **Templates** tab.  You can select any template when creating a new scan.

- Click **Save as Template** to save the scan template.
- Click **Start Scan** to run the preconfigured scan immediately.

> 📘 Note
> 
> If the maximum number of scans that can be run simultaneously is exceeded, the scan is placed in the queue. The concurrent scans limitation can be set either for the entire organization or for this particular project in the project settings. The new scan will start as soon as you manually stop another running scan or when the current scan is completed.

You can also use the **Restore Default** button to reset the custom settings.

# Technologies

## Custom DNS records

Custom DNS Records are used to access local, non-public targets. Use it when you want to replace localhost with a specific IP address. 

Also, it can be helpful to bypass CDN and proxy layers when requesting content from the site by sending those web requests directly to a specific IP address without using the site's public DNS records.

Mark the checkbox to make the fields available. Click **Add placeholder** button to add more placeholders. You can add as many items as you need.

## Smart crawling

Smart Crawler is a procedure aimed to minimize crawler time. It can skip entry-points with duplicate parameters, and so on. 

> 🚧 Please keep in mind that it is possible that not all entry-points will be found if Smart Crawling is turned on.

Smart Crawling can be turned off to ensure that all entry-points will be found during a scan. When turned off, crawler time might be significantly longer, which increases the coverage at the expense of crawler time.

If your scan time is still not satisfied, see [Troubleshooting page](https://docs.brightsec.com/docs/troubleshooting-for-problematic-scans#scan-too-long) to learn about how to increase scan time.

> 📘 Note
> 
> Disabling the **Optimized crawler** setting increases the coverage at the expense of the crawling time.
> 
> - With the **Optimized crawler** setting enabled, Bright may find not all entry points for the specified site.
> - With the **Optimized crawler** setting disabled, the crawling time may be significantly longer.

## Smart scanning

Smart scan holds inside a few optimizations to minimize scan time while maintaining the test coverage. 

- For specific tests, the Bright app scan only relevant type parameters, for example for a test that needs to manipulate "URL", don't test it as an "Integer". 
- Only the relevant headers that have a high chance of having vulnerabilities (User-Agent, Referer) will be tested, if "Headers scan location" is chosen, other headers will be skipped.
- For [Operating System Command Injection](https://docs.brightsec.com/docs/os-command-injection) test we will choose only the payloads that are relevant to the detected operating system, without it all the payloads will be tested.
- For the [SSRF test](https://docs.brightsec.com/docs/server-side-request-forgery-ssrf), only the payloads that are relevant to the detected operating system will be chosen, without it, all the payloads will be tested.

## Static parameters

Static parameters are the parts of the request that does not effect on the target system's behavior when changed. Skipping static parameters greatly increases the scan speed, without compromising the scan coverage. Static parameters can include: style parameters like 'javascript.version=', analytics-related data, and other kinds of metadata. 

The Bright app can define which part of a request is static and then skip it while scanning. To make this happen there is an advanced algorithm that is able to check all the requests parameters before the scan starts.

## Skipping parameters

You can define which parameters you want to skip in order to improve scan time. 

There are two types of skipping parameters:

- **Based on entry-point** - If you don't want to add a specific entry-point to the scan attack. 
- **Based on scan parameters** - This only refers to the speed of the test, not to the attack surface.  
  You can skip parameters that will cause performance issues. For example, you can define a specific name. 

To improve scan results sometimes it is useful to define invalid parameters and exclude them from the scan. This will improve the scan time and result.

## Target parameter locations

The Bright app can pick different parts of the address to find vulnerabilities. Target parameter locations settings are used to manually point the scanner which parts of the request (address) to attack.

By default settings are set for optimal results: **URL Query**, **URL Fragment**, and **Body** are turned on.

In most cases, this is enough to provide a high-quality scan. Select all available options if you want the deepest scan and don't care about the long scan time. In this case, the scanner will check all parts of the request (address), which will significantly increase the scanning time. In some cases, this can improve scan results.

You can also specify the URL scope to be scanned, as follows:

- **URL Path** – The main part of the URL, after the hostname and before the query parameters is used to identify the specific resource in the host that the client wants to access. In some cases (such as API endpoints), it may contain dynamic parameters (for example, object id). Enabling parsing and testing of URL path will significantly increase the attack surface, as well as the overall scan time.
- **Headers** – Request Headers are used to provide additional information from the client to the server in each HTTP request, such as cookies, information formats, security settings, and so on. Enabling parsing and testing of all possible headers will significantly increase the attack surface, as well as the overall scan time. But you can optimize this by specifying the custom headers manually. To enable the selection of custom headers, you need to select both the Headers and Smart scan checkboxes. This will open an additional field where you can enter a comma-separated list of custom headers that should be parsed and tested for injections within the scan scope.
- **URL Query** – The query parameters string (after the question mark (?) and, if relevant, before the hash sign (#)) is used to provide additional information from the client to the request, such as data to search for in the target resource.
- **URL Fragment **– The last part of a URL, after the hash sign (#), is used as an internal page reference or by DOM elements such as JavaScript, only used on the client side.
- **Body** – A Request Body can contain anything. In many cases, it contains data bytes transmitted from the client to the server, such as files.
- **Artificial URL Query** - A URL Query added artificially to check if it can be manipulated for attacks.
- **Artificial URL Fragment** - A URL Fragment added artificially to check if it can be manipulated for attacks.