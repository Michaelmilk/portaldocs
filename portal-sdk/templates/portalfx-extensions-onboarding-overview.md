## Introduction

If you are working on an Azure service and want to expose UI to your customers in the Azure portal then this is the right starting point. The portal has an extension model where each team that builds UI creates and deploys an extension. This process requires a relationship to be established between your team and the central portal team. This document walks you through the process of onboarding your team and starting that relationship. 
   
## Step by Step Process overview

Onboarding a service, or developing a Portal extension, has three phases: onboarding, development, and deployment. The process is specified in the following image.

![alt-text](../media/portalfx-extensions-onboarding/azure-onboarding.png "Azure Onboarding Process")

# Phase 1 - Onboarding

## Kickoff Meeting
 
There are lots of docs here. We recommend you send mail to <a href="mailto:ibiza-onboarding-kick@microsoft.com?subject=Kickoff Meeting Request&body=My team would like to meet with you to learn about the Azure onboarding process.">ibiza-onboarding-kick@microsoft.com</a> and request a kickoff meeting. Someone from our team will spend 30 minutes walking through the process at a high level. We can point you in the right direction regarding the latest patterns and practices. We can also answer any questions you have. Finally, we can talk about how the relationship between our teams is managed.

{"gitdown": "include-file", "file": "../templates/portalfx-extensions-onboarding-with-related-teams.md"}

## Join DLs and request permissions

Request the following permissions to stay current on product roadmaps, get news on latest features, and read workshop announcements.

* PMs and Developer Leads need to join the `ibizapartners PM`  group by clicking on this link: [http://igroup/join/ibizapartners-pm](http://igroup/join/ibizapartners-pm). 

* Developers should join the  `ibizapartners DEV` group by clicking on this  link:  [http://igroup/join/ibizapartners-dev](http://igroup/join/ibizapartners-dev). 

* Developers should join the appropriate group listed on [http://aka.ms/standardaccess](http://aka.ms/standardaccess) to get access to portal telemetry. All groups on this page receive access. 

* Developers should join the  `Azure Portal Core Team - 15003(15003)` group by using this link: [http://ramweb](http://ramweb).

* PMs, Developers, and Developer Leads should subscribe to the partner request process by joining the ```Uservoice ``` group at this link:  [https://aka.ms/portalfx/uservoice](https://aka.ms/portalfx/uservoice). For more information about the partner request process, see [portalfx-extension-partner-request-process.md](portalfx-extension-partner-request-process.md).

* PMs, Developers, and Developer Leads should receive notifications on breaking changes by joining the ```ibizabreak ``` group at  this  link:  [http://igroup/join/ibizabreak](http://igroup/join/ibizabreak).

* PMs, Developers, and Developer Leads  should join Stackoverflow Forums that are located at [https://stackoverflow.microsoft.com](https://stackoverflow.microsoft.com)  to let us know if you have any questions. Remember to tag questions with ```ibiza``` or related tag.  For more information about the supported tags that are monitored by the Ibiza team, see [portalfx-stackoverflow.md](portalfx-stackoverflow.md).

* Developers who want to contribute to the Azure documentation or test framework should join groups from the site located at [http://aka.ms/azuregithub](http://aka.ms/azuregithub).

Ask an onboarding question on [Stackoverflow](https://stackoverflow.microsoft.com/questions/tagged/ibiza-onboarding).

## Get the SDK, docs, and samples to your developers

 The [development guide](top-extensions-getting-started.md) located in the main documentation index has all the right pointers.

# Phase 2 - Development

## Develop your extension

 The [development guide](top-extensions-getting-started.md) located in the main documentation index has all the right pointers.

## Learn about the hosting service / plan your deployment strategy

The Ibiza team provides and operates a common extension hosting service that makes it easy to get your extension into a globally distributed system without having to manage your own infrastructure. For more information see [top-extensions-hosting-service.md](top-extensions-hosting-service.md).

For less common scenarios, you might need to do a custom deployment.

For example, if you need to talk to backend services using certificate-based authentication then you'll need controller code on the server. This is not supported with our hosting service. You should be very sure you require a custom hosting solution before going down this path. 

**NOTE**: The deployment can be configured in such a way that the client portion of the extension uses the hosting service while the custom controller code can be deployed separately.
For more information, see [portalfx-extensions-custom-deployment.md](portalfx-extensions-custom-deployment.md).

## Register the extension with the portal product configuration

Once the name of the extension is finalized, it is time to register the extension in all environments. This requires a portal deployment and can take time. Our Service Level Agreements are located at [portalfx-extensions-svc-lvl-agreements.md](portalfx-extensions-svc-lvl-agreements.md).  Please plan accordingly.

* For internal partners, the request to register an extension is a pull request, as specified in [top-extensions-publishing.md](top-extensions-publishing.md).
 
* External teams can submit their requests by reaching out to the <a href="mailto:ibizafxpm@microsoft.com?subject=Onboarding Request: Add <extensionName> to the Portal&body=Extension Name:  <br><br>Company:  <br><br>Brand or Suite:  <br><br>Product or Component:  <br><br> URLs: <br><br>Production: main.<extensionName>.ext.<company>.com<br><br>  Contact info: <br><br>Business Contacts <br><br> Dev leads: <br><br> PROD on-call email for live site incidents: <br><br>">ibizafxpm team</a> with an onboarding request.

* **NOTE**: Extension names must use standard extension name format, as in the example located at [portalfx-extensions-configuration-overview.md#name](portalfx-extensions-configuration-overview.md#name).

* **NOTE**:  Extension URLs adhere to the naming requirements located in [portalfx-extensions-cnames.md](portalfx-extensions-cnames.md).

* Enable the extension in all environments. 

# Phase 3 - Deployment

## Release kind

There are three typical release kinds: private preview, public preview, and Global Availability (GA). For the purposes of deployment public preview and GA are the same. The only difference is that the UI may show preview labels and disclaimers where appropriate. For more information about the three kinds of releases, see  [top-extensions-developmentPhases.md](top-extensions-developmentPhases.md).

## Private preview

For a private preview, the goal is to hide your experience to the general public, but show it to a limited audience. This procedure assumes that the discoverable entry point in the product is the All Services menu, also known as the Browse menu.

Hiding or showing items in the all services menu is controlled by the extension configuration that gets deployed with your extension. The following  example shows how to set it up. 
<!--
TODO - Example here - Add after the feature is ready (ETA is March or April) -->

When in the hidden state, users will not be able to browse to or search for the entry point of the extension. However, you can distribute a special link like the following one that enables the entry point by using a feature flag.

<!-- 
TODO - Example here - Add after the feature is ready (ETA is March or April)
-->

A few notes about this path:
* Any user that receives this URL will be able to see your entry point.
* Any users who receives a deep link to blades within your extension will be able to see that experience even without the feature flag
* If the extension is integrated into the Marketplace, then that team has its own way of hiding Marketplace items. Contact <a href="mailto:1store@microsoft.com?subject=Integrating a New Extension into the Marketplace">1store@microsoft.com </a> for more details.

## Public preview or GA

You are required to check the quality of your extension. We have standardized ways of measuring reliability and performance at key areas. If you have a private preview then we have already collected this data for you. For more information about the quality checks and the tools that the portal team provides, see [portalfx-extensions-qualityEssentials.md](portalfx-extensions-qualityEssentials.md).

There is no blocking exit criteria, which means you do not have to prove that the extension's performance and reliability are in the required range. However, once you ship, the Portal team will monitor the quality of the extension. Extensions that do not meet the required quality bar will be flagged in executive reviews and will be asked to improve their quality as soon as possible.

When you are ready for all users to see your experience, you will enable your entry point as shown in the following example and then deploy your extension.
<!--
TODO - Add an example after the feature is ready (ETA is March or April )
-->

You can ask developer community questions on Stackoverflow with the tag [ibiza-onboarding](https://stackoverflow.microsoft.com/questions/tagged/ibiza-onboarding).