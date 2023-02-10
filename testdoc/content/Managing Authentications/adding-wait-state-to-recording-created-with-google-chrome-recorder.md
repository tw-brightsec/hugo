---
title: "Known Issues (Internal)"
slug: "adding-wait-state-to-recording-created-with-google-chrome-recorder"
hidden: true
createdAt: "2022-08-25T12:36:17.442Z"
updatedAt: "2022-10-20T16:42:23.302Z"
---
# RAO inconsistency issues

## Issues affecting OAuth2, OIDC, SPA (Single Page Application)

### The redirects are not taken into account while asserting.

Results in RAO failure.

> 📘 Example
> 
> GET <https://nexploit.okta.com/login/login.htm?fromURI=/oauth2/v1/authorize/redirect?okta_key=sueOmcIiKdFwyJgkDj0xZO4JWUF8ZAxFVJuyh4rJRPA> responds with 302 status and Location header, which value is used in asserted navigation events.

### Await is missing on asserting for navigation event.

Results in RAO failure.

The authentication tester provides the following output: "**The actual URL doesn't match up to the specified validation URL, please make sure the URL is correct or record again with the correct configuration.**"

**Workaround**

Add the timeout step. 

```html
{
      "type": "customStep",
      "name": "TimeoutStep",
      "parameters": {},
      "timeout": 5000,
      "assertedEvents": [
        {
          "type": "navigation",
          "url": "http://dvwa2.neuralegion.com/index.php",
          "title": ""
        }
      ]
    }
```



> 📘 Note
> 
> This workaround may not help.

### Dynamic title in assertedEvent navigation causes AO failure.

Results in RAO failure.

If part of the title in assertedEvents navigation is changed dynamically, Recorded BBAO doesn’t consider the navigation done correctly and fails. In Chrome, the same Recorded BBAO is replayed successfully.

The following error appears: "**Unable to find the specified target page, please make sure that the specified target page exists or record again with the correct configuration.**"

**Workaround**

On the client side, change title to static.

### Recorded BBAO fails to find a frame if the frame appears after some delay.

Results in RAO failure.

If the frame appears after some delay, it isn’t found.

**Root cause:** The frame list is collected before the actual call time, and therefore is outdated by the call time.

The following error appears: "**Unable to find the specified frame in this step, please make sure that the specified frame exists or record again with the correct configuration.**"

### The top of the page is displayed in screenshots even if action is taken in the area after scrolling.

When the action in the Recorded BBAO is taken on the area which is available after scrolling, the screenshot still displays the top of it. Therefore, the screenshot is not informative because it doesn't show the element under action.

### Unable to interact with shadow DOM.

The engine is unable to interact with web components (e.g., [fast](fast.design/,), [lit](https://lit.dev/), [stencil](https://stenciljs.com/)), which are quite often used by tech-giants in different applications (e.g., <https://www.salesforce.com/>, <https://www.microsoft.com/>, <https://www.ea.com/>, etc.).

The following error appears: **Unknown error**.

### Unable to set the same value that has been typed while recording.

The engine is unable to set the same value that has been typed while recording, which makes it impossible to fill in complex forms.

The form data sent to the mock server (i.e., POST /login) by clicking the **Log in** button is different from typed. 

> 🚧 Actual result
> 
> username=artem.derevnjuk%40neuralegion.com&password=Qwerty1234%21&consent=on&language=english&organization=neuralegion&dietary-restrictions=gluten&age=22&letter=testest+testest+testtest+test+test
> 
> vs
> 
> username=artem.derevnjuk%40neuralegion.com&password=Qwerty1234%21&consent=on&language=english&organization=bight&dietary-restrictions=gluten&dietary-restrictions=lactose&age=22&letter=test+test+test

As the request body implies, there are multiple issues:

- Chain of _ change_ events for the same element is not handled properly.
- _select_ and _select[multiple]_ don’t work at all.

### Ticket duplicates are created in integrations.

Some ticket duplicates sneak through the deduplication mechanism and are created in integrations.

To reproduce the issue, follow the steps below.

1. Ensure that there is an organization with enabled Jira and Gitlab integrations.
2. Add Gitlab and Jira boards to the project.
3. Run scan under this project with enabled Jira and Gitlab integrations and wait for it to finish.
4. Compare scan issues with issues in integrations - only unique tickets should be there.
5. Retest this scan and wait for it to finish.

# Adding Wait State to recording created with Google Chrome recorder

You can add wait state to Chrome recording manually as a custom step.

1. On the tool panel, select **Export as a JSON file** and save the recording on your PC.
2. Open the saved JSON file and add the following code snippet for the wait state.

```
{
      "type": "customStep",
      "name": "TimeoutStep",
      "parameters": {},
      "timeout": 5000
}
```



> 📘 Note
> 
> After adding the wait state, Chrome will ignore this custom step when replaying the recording.