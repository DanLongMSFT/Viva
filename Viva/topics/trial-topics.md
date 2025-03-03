---
title: Run a trial of Microsoft Viva Topics
ms.author: daisyfeller
author: daisyfell
manager: pamgreen
ms.reviewer: lauris; jaeccles
ms.date: 11/15/2021
audience: admin
ms.topic: article
ms.custom:
ms.collection:
  - m365initiative-viva-topics
  - Tier1
ms.service: viva 
ms.subservice: viva-topics 
search.appverid:
    - MET150  
ms.localizationpriority:  medium
description: Learn how to plan and run a trial pilot program for Microsoft Viva Topics in your organization.
---

# Run a trial of Microsoft Viva Topics

This article describes how to set up and run a trial pilot program to deploy Viva Topics to your organization. This article also recommends best practices for the trial.

## Sign up for a trial

Trials are publicly available from one of the following sources. These trials offer 50 users access to Viva Topics for 60 days, with an option to extend the trial another 30 days.

- The [Viva Topics product page](https://www.microsoft.com/microsoft-viva/topics?activetab=pivot:overviewtab)

- The [Microsoft 365 admin center](https://admin.microsoft.com)
    1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
    2. Go to **Billing** > **Purchase Services**.
    3. Scroll down to the **Add-Ons** section.
    4. On the **Topic Experiences** tile, select **Details**.
    5. Select **Get free trial**.
    6. Follow the remaining wizard steps to confirm the trial.

You must be a Microsoft 365 global administrator or billing administrator to activate a trial.

> [!NOTE]
- Public trials can only be added once for each Microsoft 365 tenant.
- Trials aren’t available for development or educational licenses. 

### Who should be involved in a trial

|Role|Activity|
|---|---|
|Microsoft 365 global admin or billing admin|Activate the trial and assign licenses|
|Microsoft 365 global admin or SharePoint admin|Configure  Viva Topics and create topic centers|
|Business user|Perform knowledge manager, topic contributor, and topic consumer roles|

### Before you activate a trial

Planning is essential for an effective trial of Viva Topics. The trial period is limited and must include topic discovery and exploring topic quality, management, and end-user experiences.

#### Discovery

There are two high-level strategy options for configuration of topic discovery during a trial:

- Index all or most of your SharePoint Online content.
  - Large tenants can take up to two weeks to fully index. While topics will be generated incrementally throughout this period, full indexing could consume up to half the trial period.
  - For tenants with a significant volume of data, this option can produce a very large number of topics, perhaps tens of thousands.

- Identify a subset of your SharePoint sites for indexing.

The choice of these strategies is a balance of the following two factors:

- Having enough data to generate meaningful topics. The AI in Viva Topics is tuned to work on large datasets, ideally ones that have more than 10,000 documents.
- Not generating so many topics during the trial period that evaluating them during the available time period is overwhelming.

For most organizations, the second strategy produces the best outcome.

> [!NOTE]
> Due to the number of documents required by the AI, we recommend that you run Viva Topics trials on a production tenant. There's no impact on the performance of the tenant during this period. Only users who have a trial license can access Viva Topics user experiences.

#### Roles

During the trial, there are three roles that must be active, which are described in the following table.

|Role|Activity|
|---|---|
|Knowledge manager|Control the lifecycle stages of topics; confirm and remove topics; act as a community manager for topic contributors|
|Topic contributor|Content subject matter experts, who can:<br> Review topics to evaluate the quality of AI-defined content<br>Curate discovered topics with additional content<br>Create additional topics that weren't discovered by AI|
|Topic consumer|Consume topics through page highlights and search<br>Provide feedback on the value of the topics presented|

#### Expected topics

It can be useful to document the topics you expect to be generated by the AI, even if this is based only on assumptions. This task is most easily completed when you index a defined subset of your SharePoint sites for which SMEs can be easily identified.

Having a documented list will help you to:

- Review the list of AI-generated topics, which might be larger than you expect.
- Know the topics you might need to manually create or that are priorities for curation.

There will always be a need for a mixture of AI-defined and human-created topics in a successful deployment or trial of Viva Topics.

## Activate a trial

When you initiate a trial, you need to:

- Assign licenses to the relevant users.
- Perform [additional setup](set-up-topic-experiences.md) of Viva Topics.

When the trial is activated, the topic discovery process begins.

## During a trial

The trial period should be used to evaluate the following components of Viva Topics:

- The AI-suggested topics and topic content
- The end-user experiences, surfacing topic cards on modern SharePoint pages and in Microsoft Search

Consider these factors:

- For Viva Topics to deliver the maximum value, the content in topics needs to be a combination of AI-defined content and human-curated content.
- All user experiences are “permission trimmed” (including the knowledge manager's view on the **Manage topics** page). Users will only see a topic if they have permissions to view some of the resources that were used to generate the topic. This means that different users might see different content on the same topic page.
- Users might see multiple topics that have the same name in the **Manage topics** page. These topics aren't necessarily duplicates but might be because of a single term that's used in multiple contexts in the data, such as a project code name that's used by two distinct projects.

## After a trial

Based on the outcome of the trial, you can decide whether to proceed to production use of Viva Topics.

### Proceed to production use

To ensure continuity of service, you must purchase the required number of licenses and assign those licenses to users. Trial users who don't have a full license at the end of the trial period won't be able to access any Viva Topics experiences.

### Don't proceed to production use

If you don't purchase licenses following the trial:

- Topic discovery will stop.
- Users will no longer see topic highlights or cards.
- The topic center won't be deleted, but the suggested topics and manage topics experiences won't be available.
- Any AI-defined topics will be lost.
- Topics that have been edited by a topic contributor will remain in the topic center pages library. Only the manually provided content will remain on these pages, not any AI-suggested content.

## See also

[Get started driving adoption of Microsoft Viva Topics](topics-adoption-getstarted.md)
