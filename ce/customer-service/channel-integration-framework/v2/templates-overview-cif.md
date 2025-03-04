---
title: "Overview of templates in Dynamics 365 Channel Integration Framework 2.0 | Microsoft Docs"
description: "Use this topic to get an overview of the templates you can create as an administrator in Dynamics 365 Channel Integration Framework 2.0."
ms.date: 04/05/2021
ms.topic: overview
author: mh-jaya
ms.author: v-jmh
manager: shujoshi
ms.custom: 
  - "dyn365-a11y"
  - "dyn365-developer"
  - "intro-internal"
---

# Overview of templates in Dynamics 365 Channel Integration Framework 2.0

When you (an agent) get an incoming conversation request, Dynamics 365 Channel Integration Framework version 2.0 allows channel providers to search and open records on an incoming call. However, your organization might have different requirements and want to use different custom entities and correlate to a conversation.

Also, the **Omnichannel for Customer Service app** allows you to open third-party web applications in the application tabs. Your organization might have different line-of-business applications, and while starting a session, you might want to load the line-of-business applications for a specific conversation type.

To choose the applications the agents open for every session, according to your organization requirements, the administrator can create templates:

- [Session templates](session-templates-cif.md)
- [Application tab templates](application-tab-templates-cif.md)
- [Notification templates](notification-templates-cif.md)

These templates are managed in the [App profile manager](../../../app-profile-manager/overview.md).

> [!WARNING]
> It is recommended that you don’t edit the out-of-the-box sample templates in the package because it affects the functionality.

## See also

[App profile manager overview](../../../app-profile-manager/overview.md)

[Associate templates with scenarios](associate-templates-cif.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
