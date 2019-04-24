---
title: Create An SCF Sandbox
seo-title: Create An SCF Sandbox
description: This tutorial is primarily for developers, new to AEM, who are interested in using SCF components.  It walks through the creation of An SCF Sandbox site
seo-description: This tutorial is primarily for developers, new to AEM, who are interested in using SCF components.  It walks through the creation of An SCF Sandbox site
uuid: ee52e670-e1e6-4bcd-9548-c963142e6704
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e1b5c25d-cbdd-421c-b81a-feb6039610a3
---

# Create An SCF Sandbox{#create-an-scf-sandbox}

As of AEM 6.1 Communities, the easiest way to quickly create a sandbox is to create a community site. See [Getting Started with AEM Communities](/help/communities/getting-started.md).

Another useful tool for developers is the [Community Components guide](/help/communities/components-guide.md), which allows for exploration and quick prototyping of Communities components and features.

The exercise of creating a website can be useful for understanding the structure of an AEM website which may include Communities features, while also providing simple pages on which to explore working with the [social component framework (SCF)](/help/communities/scf.md).

This tutorial is primarily for developers, new to AEM, who are interested in using SCF components. It walks through the creation of An SCF Sandbox site, similar to the tutorial for [How to Create a Fully Featured Internet Website](/help/sites-developing/website.md) which focuses on site structures, such as navigation, logo, search, toolbar, and listing child pages.

Development takes place on an author instance, while experimenting with the site is best on a publish instance.

The steps in this tutorial are:

* [Setup Website Structure](/help/communities/setup-website.md)
* [Initial Sandbox Application](/help/communities/initial-app.md)
* [Initial Sandbox Content](/help/communities/initial-content.md)
* [Develop Sandbox Application](/help/communities/develop-app.md)
* [Add Clientlibs](/help/communities/add-clientlibs.md)
* [Develop Sandbox Content](/help/communities/develop-content.md)

>[!CAUTION]
>
>This tutorial does not create a community site with the functionality created using the [Communities Sites console](/help/communities/sites-console.md). For example, this tutorial does not describe how to setup login, self-registration, [social login](/help/communities/social-login.md), messaging, profiles, and so on.
>
>If a simple community site is preferred, follow the [Create a Sample Page](/help/communities/create-sample-page.md) tutorial.

## Prerequisites {#prerequisites}

This tutorial assumes you have one AEM author and one AEM publish instance installed that has the [latest release](/help/communities/deploy-communities.md#latest-releases) of Communities.

Following are some helpful links for developers new to the AEM platform:

* [Getting Started](/help/sites-deploying/deploy.md#getting-started) - for deploying AEM instances

    * [The Basics](/help/sites-developing/the-basics.md) - for developers of websites and features
    * [First Steps for Authors](/help/sites-authoring/first-steps.md) - for authoring page content

## Using CRXDE Lite Development Environment {#using-crxde-lite-development-environment}

AEM developers spend much of their time in the [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) development environment on an author instance. CRXDE Lite provides a less restricted access to the CRX repository. Classic UI tools and touch-enabled UI consoles provide more structured access to specific portions of the CRX repository.

After signing in with administrative privileges, there are various ways to access CRXDE Lite:

1. From global navigation, select **navigation**, **Tools**, **CRXDE Lite**.

   ![](assets/chlimage_1-350.png)

1. From the** ** [classic UI wecome page](http://localhost:4502/welcome.html), scroll down and click **CRXDE Lite** in the right panel.

   ![](assets/chlimage_1-351.png)

1. Browse directly to `CRXDE Lite`: `<server>:<port>/crx/de`

   For example, on a local author instance: ` [http://localhost:4502/crx/de](http://localhost:4502/crx/de)`

To work with CRXDE Lite, you must sign in with developer or administrator priveleges. For the default localhost instance, you can login with

* username: admin
* password: admin

***Be aware** *that this login will timeout and you will need to re-login periodically using the pull down on the right end of the CRXDe Lite tool bar.

If not logged in, you will be unable to navigate the JCR repository or perform any edit/save operations.

***When in doubt, re-login!***

![](assets/chlimage_1-352.png) 

|   |**[Setup Website Structure ⇒](/help/communities/setup-website.md)** |
|---|---|
