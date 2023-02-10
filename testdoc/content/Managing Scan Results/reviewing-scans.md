---
title: "Reviewing All Scans"
slug: "reviewing-scans"
hidden: false
metadata: 
  description: "You can view the scanning log of your organization, including completed, pending and scheduled scans."
createdAt: "2021-09-02T06:20:31.642Z"
updatedAt: "2022-11-14T10:31:37.192Z"
---
You can view the scanning log of your organization, including completed, pending and scheduled scans. To display the scans list, in the left pane, select the **Scans** option. Each scan appears as a single row.

![](https://files.readme.io/532f49d-__2022-10-31__09.41.16.png)

> 👍 Tip
> 
> You can open a scan in a new tab by a middle-mouse click or a Ctrl + left-mouse click.

You can set the information scope to display in the **MY SCANS** table settings. Bright allows you to change the order of the columns, select additional columns to be visible, and adjust their width.

By default, the scans table includes the following columns:

- **Name** - the custom name of the scan.
- **Issues** - number of detected vulnerabilities grouped by the severity level (red - high, yellow - medium, blue - low).
- **Requests** - total number of requests sent to the endpoints during the scan.
- **Elapsed** - total duration of the scan.
- **Start time** - date and time when the scan started.
- **End Time** - date and time when the scan ended.
- **Labels** - the custom text information, added at the scan creation step.

## Filtering scans

To simplify searching for a particular scan, Bright allows you to filter scans by multiple parameters, such as: 

- **History ID** - ID of a scan history to distinguish all the re-run and scheduled scans
- **Discovery type** - archive, crawler, OAS (Open API Specification)
- **End time** - when a scan finished
- **Start time** - when a scan started
- **Initiator** - a user who created a scan
- **Issues by severity** - high, medium, low
- **Project** - a Bright project name
- **Status** - disrupted, done, failed, pending, queued, running
- **Repeater** - a Repeater name
- **Labels** - labels,  appeared during new scan creation



To apply a filter, follow these steps:

1. In the header of the **SCANS** table, click <img src="https://files.readme.io/2b1b3f8-filter-icon.png" width="70" height="25">.
2. In the **Filter by** dialog box, select the necessary filter option and set up the relevant filter parameters.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/672b3de-filter-options.png",
        "filter-options.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



3. _(Optional)_. If you need to apply several filters at once, click **+ Add filter** to apply one more filter.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0f3ca56-add-filter.png",
        "add-filter.png",
        1895
      ],
      "sizing": "80"
    }
  ]
}
[/block]



4. Click **Apply**.

To reset the filter parameter(s), follow these steps:

1. In the header of the **SCANS** table, click the applied filter parameter(s).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0c1f34f-filter-parameter.png",
        "filter-parameter.png",
        1889
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **Filter by** dialog box, click **Clear all** and then **Apply**.

You can also search for a certain scan by its name or ID across the table using the **Search** bar.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e91edc8-search-by-scan-name.png",
        "search-by-scan-name.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



## Sorting scans

Scans can be sorted by the column parameters, either in the ascending or descending order. For example, you may need to move the most recent scans up in the table, or put the scans that detected the high severity issues first.

To sort scans by a parameter, follow these steps:

1. In the header of the **SCANS** table, click <img src="https://files.readme.io/8924d12-sort_icon.png" width="53" height="25">.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3484cf9-sort-scans.png",
        "sort-scans.png",
        1894
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **Sort by** dialog box, select a parameter for sorting and the sorting order, and then click **Apply**.  

To reset the sorting parameter(s), follow these steps:

1. In the header of the **SCANS** table, click the applied sorting parameter(s).

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc20902-sort-parameter.png",
        "sort-parameter.png",
        1891
      ],
      "sizing": "80"
    }
  ]
}
[/block]



2. In the **Sort by** dialog box, click **Clear** and then **Apply**.    

## Adjusting scans table

To configure the scans table view, follow these steps:

1. Below the **+ Create scan** button, click <img src="https://files.readme.io/116c0a0-settings-icon.png" width="22" height="23"> to open the table settings.
2. In the dialog box, do the following:

- _(Optional)_. Using the **Items per page** option, select the number of rows to be displayed on a single **Scans** page.
- Using the toggle buttons, select the columns you want to view in the table.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/a1709ea-table-settings.png",
        "table-settings.png",
        1903
      ],
      "sizing": "80"
    }
  ]
}
[/block]



- Drag the selected columns to put them in the desired order.
- _(Optional)_. Adjust the width of the selected columns in the corresponding **Width** boxes.
- _(Optional)_. To reset the table settings to default, click **Reset defaults** at the bottom of the dialog box.

## Managing scans from the scans table

To display the options menu for a scan run, click <img src="https://files.readme.io/a74f9a9-dots-button.png" width="22" height="26"> in the corresponding row.

Different options appear depending on the **Status** of the run. The following options are available: 

- **Stop –** Stops a scan that is running. 
- **Delete –** Deletes all data about the selected scan run, cancels the next scheduled run of a recurring scan, stops its recurrence. You can delete multiple scan runs by selecting their checkboxes and then selecting the **Delete** option. 
- **Export –** Exports the scan results and details as a CSV or PDF.
- **Edit –** When a scan has the **Scheduled** status, the **Edit** option enables you to modify the start time and settings of the next scan to be run. The settings options are the same as on the **Scans** page. Modifying the scan settings using this option retains the same scan history.  
  By default, a scan run is assigned the same name as the original scan. The **Edit** option always enables you to rename a specific run (regardless of its status) to give it a more indicative name. For example, this can be done to indicate an important finding or event, such as the installation of a new product version.
- **Run Immediately –** Runs a scheduled scan immediately using its most recently defined settings.
- **Retest –** Creates a separate scan entity that is a duplicate of the selected scan. Initially, the settings are identical, but you can modify them without affecting the original scan settings. A separate scan history is maintained for this retested scan.