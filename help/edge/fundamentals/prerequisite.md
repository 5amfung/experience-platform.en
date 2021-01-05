---
title: Prerequisites for using Adobe Experience Platform Web SDK
seo-title: Prerequisites for using Adobe Experience Platform Web SDK
description: Prerequisites for using Adobe Experience Platform Web SDK
seo-description: Prerequisites for using Adobe Experience Platform Web SDK
keywords: 1st-party domain;CNAME;schema;create schema;launch;aep web sdk extension;extension;configuration id;configuration tool;data element;create data element;XDM Object;sendEvent;send Event;
---

# Prerequisites for using Adobe Experience Platform Web SDK

To use the Platform Web SDK, you must first:

- Have your organization provisioned for this feature. (Access to the Platform Web SDK is free, if you would like to get access please reach out to your Customer Success Manager (CSM)).
- Have a 1st-party domain (CNAME) enabled. If you already have a CNAME for Adobe Analytics, you should use that one. Testing in development works without a CNAME, but you need one before you go to production.

>[!IMPORTANT]
>
>**Please note that as of 11/10/20, 1st-party CNAME implementations have a 7-day expiry on all Safari browsers and mobile iOS devices.** 

- Be entitled to Adobe Experience Platform. If you have not purchased Adobe Experience Platform, Adobe will provision you with the necessary access to use in a limited fashion with the SDK at no extra charge.
- If your website is already using the [Experience Cloud ID Service](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/overview.html) on your website--either through Visitor API or the Experience Cloud ID Service extension within Adobe Experience Platform Launch--and you would like to continue using it while migrating to Adobe Experience Platform Web SDK, you must be using the latest version of Visitor API or the Experience Cloud ID Service extension. See [ID Migration](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/overview.html?lang=en#identity) for more information. 
