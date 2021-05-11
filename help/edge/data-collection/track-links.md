---
title: Track Links Using the Adobe Experience Platform Web SDK
description: Learn how to send Link Data to Adobe Analytics with Experience Platform Web SDK
keywords: adobe analytics;analytics;sendEvent;s.t();s.tl();webPageDetails;pageViews;webInteraction;web Interaction;page views;link tracking;links;track links;clickCollection;click collection;
exl-id: d5a1804c-8f91-4083-a46e-ea8f7edf36b6
---
# Track links

Links can be set manually or tracked [automatically](#automaticLinkTracking). Manual tracking is done by adding the details under the `web.webInteraction` part of the schema. There are three required variables: 

* `web.webInteraction.name`
* `web.webInteraction.type`
* `web.webInteraction.linkClicks.value`

```javascript
alloy("sendEvent", {
  "xdm": {
    "web": {
      "webInteraction": {
        "linkClicks": {
            "value":1
      },
      "name":"My Custom Link", //Name that shows up in the custom links report
      "URL":"https://myurl.com", //the URL of the link
      "type":"other", // values: other, download, exit
      }
    }
  }
});
```

The link type can be one of three values: 

* **`other`:** A custom link
* **`download`:** A download link
* **`exit`:** An exit link

## Automatic link tracking {#automaticLinkTracking}

By default, the Web SDK captures, labels, and records clicks on qualifying link tags. Clicks are captured with a [capture](https://www.w3.org/TR/uievents/#capture-phase) click event listener that is attached to the document.

Automatic link tracking can be disabled by [configuring](../fundamentals/configuring-the-sdk.md#clickCollectionEnabled) the Web SDK.

```javascript
clickCollectionEnabled: false
```

### What tags qualify for link-tracking?{#qualifyingLinks}

Automatic link tracking is done for anchor `A` and `AREA` tags. However, these tags aren't considered for link tracking if they have an attached `onclick` handler.

### How are links labeled?{#labelingLinks}

Links are labeled as a download link if the anchor tag includes a download attribute or if the link ends with a popular file extension. The download link qualifier can be [configured](../fundamentals/configuring-the-sdk.md) with a regular expression:

```javascript
downloadLinkQualifier: "\\.(exe|zip|wav|mp3|mov|mpg|avi|wmv|pdf|doc|docx|xls|xlsx|ppt|pptx)$"
```

Links are labeled as an exit link if the link target domain differs from the current `window.location.hostname`.

Links that do not qualify as a download or exit link are labeled as "other."
