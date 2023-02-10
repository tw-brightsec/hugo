---
title: "Entry-Points"
slug: "entry-points"
hidden: true
createdAt: "2022-08-18T08:18:58.959Z"
updatedAt: "2022-10-11T17:57:54.815Z"
---
An **Entry-point** is a single logical interaction with the target application (such as visiting a page, submitting a form, etc). Bright defines the target attack surface as a collection of entry-points and the information in each entry-point enables the Bright engine to have a baseline of a valid interaction. With this information Bright can performs all the necessary tests and validations of the scan findings for the best results without false positives.

An entry-point is valid when it contains all the information needed for a successful interaction such as default values for parameters, authentication information, etc.

There are several ways to find entry-points with Bright:

1. **Via Crawler**. For more information, see [Scanning with a Crawler page ](https://docs.brightsec.com/docs/crawler).
2. **Via HAR file**. For more information, see [Scanning with a HAR](https://docs.brightsec.com/docs/scanning-with-a-har).
3. **Via API-schema**. For more information, see [Configuring API Schema](https://docs.brightsec.com/docs/configuring-an-api-schema-for-scanning).

In order to get the best scan results, you need to ensure the entry-points have all the needed data for interactions. To improve the scan results, the first thing you should do is review the number of entry-points in the scan. Generally, if no entry-points or only a few of them are found, this should be a red flag, because it may indicate that there is missing or incorrect information that prevents Bright from mapping the target attack surface correctly. 

Learn more about how to improve scan results in [Troubleshooting page](https://docs.brightsec.com/docs/troubleshooting-for-problematic-scans#problematic-scan-results).

# Entry-points Summary

If you want to analyze the information about your entry-point, you can open an overview of each entry-point by selecting it from the entry-points table.

![](https://files.readme.io/274878e-.png)

The Entry-points table includes the following columns: 

- **Method** - used HTTP method
- **URL** - entry-point URL 
- **Response time** - interaction average response time for the target
- **Tested scenarios** - number of executed requests as part of tested scenarios

Click the specified entry-point to open a page with detailed information about it. Click <img src="https://files.readme.io/eeef5cc-Screenshot_1.png" width="34" height="34"> to open the page in a new tab. To copy the entry-point's URL, click <img src="https://files.readme.io/8f4a6dc-Screenshot_3.png">.

This page consists of the following tabs:

- **Tested Scenarios** -  information about how many test scenarios were executed if a vulnerability was found
- **Parameters** - entry-point parameters
- **Statuses** - response statuses received during the scan
- **Request** - full request information
- **Response** - full response information

***



## Tested scenarios

The total number of requests was done on entry-points to find a vulnerability.

![](https://files.readme.io/de95ff0-.png)

The table includes the following columns: 

- **Tests** - tests by name
- **Scenarios** - number of executed scenarios
- **Found issue** - the name of the found issue after test execution
- **Severity** -  how much damage can be done

## Parameters

The tab contains detailed information about entry-point parameters if they exist. Click the arrows to expand or collapse the menu.

![](https://files.readme.io/b67a9ad-.png)

## Statuses

The tab contains detailed information about the final entry-point status.

![](https://files.readme.io/4b97401-.png)

The table includes the following columns:

- **Status** - status code
- **Occurrences** - a number of received responses

## Requests

![](https://files.readme.io/8cb054c-.png)

The tab contains detailed information about the entry-point request.

From the **Copy request as** drop-down menu, select the desired option to copy the request.

![](https://files.readme.io/ddf54ff-.png)

## Response

The tab contains detailed information about the entry-point response.

![](https://files.readme.io/92c81de-.png)

From the **Copy request as** drop-down menu, select the desired option to copy the request.

![](https://files.readme.io/5360312-.png)