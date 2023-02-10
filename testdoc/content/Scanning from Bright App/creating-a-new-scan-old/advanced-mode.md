---
title: "Advanced Mode"
slug: "advanced-mode"
excerpt: "Run a scan with advanced settings."
hidden: true
metadata: 
  description: "In the **NEW SCAN** dialog box, select the **Advanced** tab to create a scan with expanded settings."
createdAt: "2021-09-01T10:52:45.508Z"
updatedAt: "2022-09-12T18:29:15.443Z"
---
In the **Create scan** dialog box, select the **Advanced** tab to create a scan with expanded settings.

### Specifying scan details

In the <u> **Scan Details** tab</U>, do the following:

1. In the **Scan name** field, enter any free-text name for the scan.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6b3ed4c-details-advanced.png",
        "details-advanced.png",
        1561
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. From the **Project** dropdown list, select the Bright project you want to use for the scan.

> 📘 Note
> 
> You can start a scan ONLY if a project is selected. If you do not have any projects in the Bright app, select the **Default** one.

3. _(Optional)._ If you have integrated the selected project with a ticketing system, you can connect the associated repository for the scan in the **Integrations** field. The detected issues will be automatically opened as tickets/issues/messages in the integrated repository. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0a77a32-integrations.png",
        "integrations.png",
        1559
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. _(Optional)._ Bright provides a list of preconfigured scan templates to help the users assess their vulnerabilities quicker and more efficiently. The list is available in the <u>**Templates** tab</u>. There is also an option to create your own template. For further details, see [Managing Scan Templates](/docs/managing-scan-templates).
5. _(Optional)._ You can schedule a scan by selecting the **Enable scheduling** option and then defining the scan as follows:

- **Single scan** – Select date and time to schedule the scan to run once automatically.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d5c4706-single-scan.png",
        "single-scan.png",
        1552
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Recurring scan** – Define the frequency and schedule of the scan to run repeatedly automatically.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/de62007-recurring-scan.png",
        "recurring-scan.png",
        1555
      ],
      "sizing": "80"
    }
  ]
}
[/block]



### Defining scan targets

In the <u>**Scan Targets** tab</u>, do the following:

1. In the **Discovery Types** field, select one of the following ways your application attack surface should be mapped (depending on your subscription) – Crawler, Recording (HAR) or Open API: <br>

- **Crawler –** this is the simplest option. Simply enter a URL (target host) to scan the whole or a part of the specified application. The crawler will map the entire application attack surface automatically.

  To scan only specific parts of your application or add multiple hosts, click  <img src="https://files.readme.io/bad6a00-plus-dark.png" width="22" height="23"> at the right side of the **Targets** section. In this case, only the specified sections of the application and everything downstream from them will be scanned. 

  Note that some hosts may be unreachable or unauthorized for a direct scan from the cloud. If a host cannot be reached by the engine, select a running Repeater for the scan in the **Network Settings** section. If a host is unauthorized for a direct scan from the cloud, either select a running Repeater for the scan or add a `.nex` file to the host root directory (read more information [here](/docs/manage-your-organization#define-the-hosts-authorized-for-scanning)).<br> 

  See [Scanning a website with a crawler](/docs/crawler) for detailed information.

![](https://files.readme.io/5c937d4-crawler-advanced.png "crawler-advanced.png")

- **Recording (HAR) –** Use a pre-recorded session of your application (HAR file), which has been created either manually or automatically (using QA tools, such as Selenium to scan your application). This discovery type enables you to define the scope of a scan and store login information in order to scan areas in your application that require authentication. 

  See [Creating a HAR File](/docs/creating-a-har-file) to learn how to create a HAR file.

  Note that some hosts may be unreachable or unauthorized for a direct scan from the cloud. If a host cannot be reached by the engine, select a running Repeater for the scan in the **Network Settings** section. If a host is unauthorized for a direct scan from the cloud, either select a running Repeater for the scan or add a `.nex` file to the host root directory (read more information [here](/docs/manage-your-organization#define-the-hosts-authorized-for-scanning)).

  See [Scanning a website with a HAR file](/docs/scanning-with-a-har) for detailed information.

> 👍 Tip
> 
> To enjoy both full automation and deeper attack surface analysis, you can combine **Crawling** and **Recording (HAR)** in a single scan!

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/010b82e-har-advanced.png",
        "har-advanced.png",
        1556
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Open API –** Use a `*.yml` file to scan APIs. See [Scanning API endpoints](/docs/scanning-api-endpoints) for detailed information.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/88833db-api-advanced.png",
        "api-advanced.png",
        1554
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. _(Optional)_ If you are going to scan a target on a local network, select a **Repeater** to use it for the scan. The list includes the global Repeaters and the Repeaters created for the selected Project. The Repeater is created in the **Repeaters** section and serves as a request-proxy between Bright and the target hosted on a local network.  See [On-Premises Repeater (Agent)](/docs/on-premises-repeater-local-agent) for more information.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/cbf9305-repeater-advanced.png",
        "repeater-advanced.png",
        1558
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. _(Optional)_ The **Coverage Exclusions** section contains two panes: **Excluded entry-points** and **Excluded parameters**. The **Excluded entry-points** pane contains an expression that excludes most common static files like images, audio, video, and other files that don't contain any vulnerabilities (including fonts). If you don't want these files to be excluded, you can clear the **URL regex pattern** field.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9cd4a38-coverage_exclusions.png",
        "coverage_exclusions.png",
        1654
      ],
      "sizing": "80"
    }
  ]
}
[/block]



In this pane, you may set additional parameters to be ignored during scanning.

- Below the **Method** field, click ** + Add exclusion**. Empty fields will appear. 
- From the **Method** dropdown menu, select the method you want to be excluded from scanning. 
- In the **URL regex pattern** field, enter the parameters for the selected method.

For example, if you don't want the **POST** method to go over entry points that contain _vendor_ in the URL, from the **Method** dropdown menu, select _POST_ and then in the **URL regex pattern** field, enter _vendor_. Any URL which contains _vendor_ will be excluded from scanning. 

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a1be2f2-post.png",
        "post.png",
        1258
      ],
      "sizing": "80"
    }
  ]
}
[/block]



   In the **Excluded parameters** pane, in the **Ignored parameter names** field, enter the URLs and  
   parameters to be ignored during scanning. For example, to skip all URLs that include  
   _instructions_, _setup_, _security_, and _csrf_ during a scan, enter these patterns  
   into the **Ignored parameter names** field. Start each parameter with a new line.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/687a458-2022-06-28_17-55-03.png",
        "2022-06-28_17-55-03.png",
        1274
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. _(Optional)_ In the **Attack Surface Optimization** section, you can use the following options to optimize the scanning flow:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/683a786-attack_sur_opt.png",
        "attack_sur_opt.png",
        1385
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Stop scan, if the target does not respond for** – Set a limit to response duration for the scan target globally. If the specified duration is exceeded, the scan will be stopped automatically. The default value is 5 min.
- **Smart scan** – Specify whether to use automatic smart decisions (such as parameter skipping, detection phases, and so on) in order to minimize scan time. When this option is turned off, all tests are run on all the parameters, which increases coverage at the expense of scan time.
- **Optimized crawler** – With this option enabled, the crawler skips the forms and URLs with the same set of parameters, which significantly reduces the crawling time. This setting also allows avoiding scan crashes when there is not enough memory for large sites.

> 📘 Note
> 
> Disabling the **Optimized crawler** setting increases the coverage at the expense of the crawling time.
> 
> - With the **Optimized crawler** setting enabled, Bright may find not all entry points for the specified site.
> - With the **Optimized crawler** setting disabled, the crawling time may be significantly longer.

- **Skip static parameters** – Specify whether to skip static parameters to minimize scan time.
- **Skip entry points, if the response is longer than** – Set the limit to response duration for entry points to minimize scan time. If the specified duration is exceeded, the entry point will be skipped. The default value is 1000 ms.
- **Target Parameter Locators** – Specify the URL scope to be scanned, as follows:
  - **URL Path** – The main part of the URL, after the hostname and before the query parameters is used to identify the specific resource in the host that the client wants to access. In some cases (such as API endpoints), it may contain dynamic parameters (for example, object id). Enabling parsing and testing of URL path will significantly increase the attack surface, as well as the overall scan time.
  - **Headers** – Request Headers are used to provide additional information from the client to the server in each HTTP request, such as cookies, information formats, security settings and so on. Enabling parsing and testing of all possible headers will significantly increase the attack surface, as well as the overall scan time. But you can optimize this by specifying the custom headers manually. To enable selection of custom headers, you need to select both the **Headers** and **Smart scan** checkboxes.  This will open an additional field where you can enter a comma-separated list of custom headers that should be parsed and tested for injections within the scan scope. 
  - **URL Query** – The query parameters string (after the question mark (?) and, if relevant, before the hash sign (#)) is used to provide additional information from the client to the request, such as data to search for in the target resource.
  - **URL Fragment** – The last part of a URL, after the hash sign (#), is used as an internal page reference or by DOM elements such as JavaScript, only used on the client side.
  - **Body** – A Request Body can contain anything. In many cases, it contains data bytes transmitted from the client to the server, such as files.
  - **Artificial URL Query** - A URL Query added artificially to check if it can be manipulated for attacks. 
  - **Artificial URL Fragment** -  A URL Fragment added artificially to check if it can be manipulated for attacks. 

In the <u>**Network**</u> section, you can configure the following options:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/92cc448-concurrent_requests.png",
        "concurrent_requests.png",
        1557
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Custom host placeholders** – Defines host placeholders with specific addresses. For example, replacing `localhost` with a specific IP address.
- **Concurrent requests** – Specify the maximum concurrent requests allowed to be sent by the scan in order to control the load on your server.

### Selecting tests for a scan

In the <u>**Scan Tests** tab</u>, do the following:

1. In the **Modules** section, select one of the following scan types (depending on your subscription):

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/11d430c-modules-advanced.png",
        "modules-advanced.png",
        1553
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **DAST** – Scans your application for OWASP Top 10+ issues (vulnerabilities) and many different CVEs. This is the default option.
- **Fuzzer** – Scans your application for OWASP Top 10+ issues (vulnerabilities), as well as business logic vulnerabilities, 0-Days and many unknown issues.

> ❗️ Warning
> 
> This type of scan may harm your system and so must only be used on a testing environment.

2. In the **Tests** section, select the tests to be performed during the scan by checking their checkboxes.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d4b721a-tests.png",
        "tests.png",
        1557
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 📘 Note
> 
> For details on vulnerabilities that can be detected by Bright, see [Vulnerability Guide](https://docs.brightsec.com/docs/vulnerability-guide).

### Configuring application settings

In the <u>**App settings**</u> tab, do the following:

1. Select the authentication option you want to apply for the scanned target:

- **None** - Select if the scan target does not include any authenticated resources.
- **Authentication object** - you can find a full description about how to use an authentication object in the [Managing Your Authentications section](/docs/creating-an-authentication-object-in-nexploit).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/daaa1b5-app-settings.png",
        "app-settings.png",
        1554
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **Additional Headers** section, define any custom headers to be appended to or replaced in each request. If you need to add some authentication headers, see [Header Authentication](/docs/configure-header-authentication-in-nexploit).

> 👍 Tip
> 
> If you need to add several **Additional headers**, you can copy-paste them in a single **Name** field. The headers will be distributed among the fields automatically.

### Starting a scan

Once you complete the setup, you can run the scan immediately or save it as a template. The template will be saved to the templates list in the **Templates** tab.  You can select any template when creating a new scan.

- Click **Save as Template** to save the scan template.
- Click **Start Scan** to run the preconfigured scan immediately.

> 📘 Note
> 
> If the maximum number of scans that can be run simultaneously is exceeded, the scan is placed in the queue. The concurrent scans limitation can be set either for the entire organization or for this particular project in the project settings. The new scan will start as soon as you manually stop another running scan or when the current scan is completed.

You can also use the **Restore Default** button to reset the custom settings.