---
title: "Managing Scan Templates"
slug: "managing-scan-templates"
hidden: false
metadata: 
  description: "A scan template enables you to save and reuse a set of scan settings so that you can start another scan more quickly. NeuraLegion provides the following default scan templates"
createdAt: "2021-09-03T07:48:18.634Z"
updatedAt: "2022-10-18T07:16:15.578Z"
---
A scan template enables the users to save and reuse a set of scan settings so that they can start another scan more quickly. Bright provides a list of preconfigured scan templates to help users assess their vulnerabilities quicker and more efficiently.

- **OWASP Top 10 for Web Apps (2021)** – The engine runs only the tests for the vulnerabilities included in to the "OWASP Top 10" list for 2021.
- **PCI DSS** - The engine runs only the tests for the vulnerabilities included in to the PCI Data Security Standard.
- **WordPress** - The engine runs only WordPress-relevant tests.
- **OWASP Top 10 (2017)** – The engine runs only the tests for the vulnerabilities included in to the "OWASP Top 10" list for 2017.
- **MITRE Top 25 (2019)** – The engine runs only the tests for the vulnerabilities included in to the "MITRE Top 25" list for 2019.
- **MITRE Top 25 (2020)** – The engine runs only the tests for the vulnerabilities included in to the "MITRE Top 25" list for 2020.
- **API Scan** – Predefined tests that are relevant for API targets.
- **Light Scan** – This is a preconfigured optimized scan, during which the engine automatically determines which tests to run, based on the data types that are detected. Some tests will be skipped in favor of speed.
- **Deep Scan** – All possible tests are performed during the scan. This is the most thorough scan, which takes the longest time to complete.
- **Passive Scan** – The engine selects only host-based passive tests to be run.

## Viewing all scan templates

To open the list of scan templates, follow the steps below.

1. From the left menu, select **Scans**. 
2. In the upper right corner, click **Scan Templates**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc6947f-scan-templates.png",
        "scan-templates.png",
        1904
      ],
      "sizing": "80"
    }
  ]
}
[/block]



The system displays the list of default and custom scan templates.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a0dcc72-templates-list.png",
        "templates-list.png",
        1897
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. To display the details of a specific template, select it from the list.  
   In the dialog box, you can view all the information about this scan template, including:
   - Scan details
   - Scan targets
   - Network and application settings
   - Security tests to be run 

## Creating a new template

To create a new template, follow these steps:

1. At the top of the **Scan Templates** page,  click **+ Create Scan Template**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/734e6f1-create-template.png",
        "create-template.png",
        1911
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **CREATE SCAN TEMPLATE** dialog box, define the settings for a new scan template. These are mostly the same [settings as for creating a new scan](/docs/creating-a-new-scan). 

> 👍 Tip
> 
> If you need to add **Additional headers** in the **Network Settings** tab, you can copy-paste several headers in the **Name** field. The headers will be separated and broken down by the fields automatically.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e8b064e-new-template-popup.png",
        "new-template-popup.png",
        1089
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. Once you complete the setup, click **Create Template** to save the defined scan template.

## Editing a template

To edit a template, follow these steps:

1. In the **Scan Templates** list, click <img src="https://files.readme.io/515ad55-dots-button.png" width="22" height="28"> next to the template you want to edit.
2. Select the **Edit** option.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/67f51fc-edit-template.png",
        "edit-template.png",
        1911
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 📘 Note
> 
> The default templates cannot be edited.

3. In the dialog box, make changes to the setup of the selected scan template. These are the same [settings as for creating a new scan](/docs/creating-a-new-scan).
4. Once you complete editing the template, click **Update Template**.

## Deleting a template

To delete a template, follow these steps:

1. In the **Scan Templates** list, click <img src="https://files.readme.io/515ad55-dots-button.png" width="22" height="28"> next to the template you want to delete.
2. Select the **Delete** option.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fa7c5a5-delete-template.png",
        "delete-template.png",
        1907
      ],
      "sizing": "80"
    }
  ]
}
[/block]



> 📘 Note
> 
> The default templates cannot be deleted.