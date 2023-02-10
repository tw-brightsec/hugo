---
title: "CSS and XPath Draft"
slug: "css-and-xpath-draft"
hidden: true
createdAt: "2022-08-09T15:09:34.499Z"
updatedAt: "2022-08-25T10:08:56.459Z"
---
In the **CSS & XPath Exclusions** pane, in the **Exclude links inside these XPath & CSS selectors** field, enter CSS selectors and XPath to be excluded from the scan, separated by a new line.

![](https://files.readme.io/04930bd-08.png "08.png")

> 📘 Note
> 
> Please make sure the XPath/CSS selector is very specific, that is only one element matches the XPath/CSS selector. Otherwise, it will negatively affect scan results.
> 
> To check if the XPath/CSS selector is specific, you can use the search option in your browser DevTools. 
> 
> 1. Open the **Elements** tab and press** Ctrl + F**/**Cmd ⌘ + F** (the steps may differ for some browsers). 
> 2. In the search field, enter the XPath/CCS selector you specified for the scan.  
>    In the upper-right corner of the search field, you will find the number of elements defined by the XPath/CCS selector. No elements or more than 1 element indicate that the XPath/CCS selector is invalid or non-specific respectively.
> 
> To check the number of elements defined by the XPath, you can also use a special script.  
> In the DevTools, open the **Console** tab and execute the script below. Substitute **${desired_xpath}** with the XPath specified for the scan. No elements or more than 1 element indicate that the XPath is invalid or non-specific respectively.
> 
> (function(selector) {  
>   let results = \[];
> 
>   let xpath = document.evaluate(selector, document, null, XPathResult.ORDERED_NODE_SNAPSHOT_TYPE, null);  
>   for (let i = 0; i \< xpath.snapshotLength; i++) {  
>     results.push(xpath.snapshotItem(i));  
>   }
> 
>   return results;  
> })('${desired_xpath}')

test \<id="test">

<a id="test">Local SEO</a>

<p><a name="DNS-Custom-Records"></a></p>

<p><a href="https://docs.brightsec.com/docs/advanced-mode#defining-scan-targets#DNS-Custom-Records">Learn more about Custom DNS Records</a></p>

<p><a href="https://docs.brightsec.com/docs/advanced-mode#defining-scan-targets#DNS-Custom-Records">Learn more about Custom DNS Records</a></p>