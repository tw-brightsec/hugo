---
title: "Exporting a Scan Report"
slug: "exporting-a-scan"
hidden: false
metadata: 
  description: "You can download a scan report in the PDG, JSON or CSV format for further analysis. NeuraLegion also provides the option to generate a SARIF (Static Analysis Results Interchange Format) report file and send it to GitHub Code Scanning Alerts"
createdAt: "2021-09-02T10:36:49.663Z"
updatedAt: "2022-10-18T07:16:52.607Z"
---
You can download a scan report in the PDF, JSON or CSV format for further analysis. Bright also provides the option to generate a SARIF (Static Analysis Results Interchange Format) report file and upload it to your GitHub repository so that you can open the detected vulnerabilities as Code Scanning Alerts. Using this option, you can easily triage the existing security issues, prioritize fixes and open tickets for them in your GitHub repository. Each detected vulnerability from the report will be displayed as a separate alert automatically. 

> 👍 Tip
> 
> To configure an integration with your GitHub CI pipeline and open detected vulnerabilities as Code Scanning Alerts automatically, read [here](/docs/github-actions).

Bright provides you with the opportunity to select the scope of the information to be included in the PDF report. For example, you can get a full report or only select certain parts of the full report to be exported.

The following PDF report options are available:

- **Full Report** – Combines the **Executive Summary** and the **Scan Details** reports.
- **Executive Summary** – Is intended for executives. It contains a brief analysis of each issue and its possible consequences, as well as a compliance report.
- **Scan Details** – Provides detailed information about the scan, including all the technical information about the issues that have been detected, possible consequences, remedy suggestions, and much more.
- **Custom report** – Enables you to select the parts of the full report to be exported during this action.

To export a scan report, do the following:

1. In the left pane, select the **Scans** option to display the scans list. 
2. Click <img src="https://files.readme.io/a74f9a9-dots-button.png" width="22" height="26"> next to the scan to be exported.
3. From the dropdown list, select **Export as CSV**, **Export as JSON** or **Export as PDF**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/166fe1a-export-as.png",
        "export-as.png",
        1903
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- **Export as CSV –** Exports a simple CSV file containing a short description of the issues that have been detected. 
- **Export as SARIF -** Sends a SARIF report file to your GitHub repository and creates code scanning alerts for each detected vulnerability from the report. 
- **Export as JSON -** Exports a simple JSON file containing a short description of the issues that have been detected.
- **Export as PDF –** Select one of the report options to be exported.  
  For the **Custom** report, in the dialog box, select the information to be included in to the report and click **Export**.

<img src="https://files.readme.io/c07009b-pdf-options.png" width="330" height="480">

## Customizing PDF reports

You can make your PDF reports more distinctive by customizing their appearance. You can change the cover, add your company logo, select other colors and fonts, and optimize page parameters. 

> 📘 Note
> 
> The PDF customization functionality is only available to the paid plans users. If you want to enable this functionality, please contact our sales team at [plans@brightsec.com](mailto:plans@brightsec.com).

To customize a PDF report, follow these steps: 

1. In the left pane, select **Organization**, and then scroll down to the **PDF REPORT CUSTOMIZATION** section.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1e999b1-pdf-customization.png",
        "pdf-customization.png",
        1893
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. Expand the options you want to configure.
3. Complete the fields with your custom values or upload an image file.  
   For example, to upload your company logo, expand **Page options: logo**, click the **Image file** field and select the logo from your local storage.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3383747-logo-in-pdf.png",
        "logo-in-pdf.png",
        1578
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. To save the changes, in the upper right corner of the **PDF REPORT CUSTOMIZATION** section, click **Save**.