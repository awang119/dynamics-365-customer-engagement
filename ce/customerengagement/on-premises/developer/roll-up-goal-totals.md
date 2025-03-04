---
title: "Roll up goal totals (Developer Guide for Dynamics 365 Customer Engagement (on-premises))| MicrosoftDocs"
description: "RecalculateRequest message can be used to roll up data in a goal hierarchy. It recalculates the goal rollup field values, such as Goal.ActualMoney or Goal.ActualInteger, for all goals in the hierarchy"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: pehecke

ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to: 
  - Dynamics 365 Customer Engagement (on-premises)
helpviewer_keywords: 
  - goal management entities, rolling up goal totals
  - overriding values for rollup goal totals
  - goal management entities, recalculating goal rollup values
  - goal management entities, expiration time for goal rollup fields
  - goal management entities, rolling up data in goal hierarchies
  - rolling up goal totals
  - expiration time for goal rollup fields
  - goal management entities, overriding values for rollup goal totals
  - rolling up data in goal hierarchies
  - recalculating goal rollup values
ms.assetid: e7e706f7-0f65-480a-87bc-e11857ad084f
caps.latest.revision: 25
author: JimDaly
ms.author: jdaly
manager: amyla
search.audienceType: 
  - developer

---
# Roll up goal totals

To roll up data in the goal hierarchy, use the <xref:Microsoft.Crm.Sdk.Messages.RecalculateRequest> message. It recalculates the goal rollup field values, such as `Goal.ActualMoney` or `Goal.ActualInteger`, for all goals in the hierarchy. A rollup for each goal is performed in the context of the goal manager. This means that only the records that a manager of a goal has Read access to participate in the rollup. The system automatically switches the manager’s context for each goal during rollup, as every goal may have a different goal manager.  
  
 The totals are rolled up from the child goals to the parent goals, from the bottom of the hierarchy to the top. The ending total for the root goal at the top of the hierarchy is an aggregate sum of all totals in the hierarchy. For example, if revenue metric is used, the total is an aggregate sum of the money amounts. If a count metric is used, the total is an aggregate count of the actual records in the system, such as telephone calls. Regardless of which particular goal is a target of the recalculate operation, all totals in a given hierarchy are updated.  
  
 If you set `Goal.RollupOnlyFromChildGoals` to `true`, only child goal records are used in the rollup. If you set it to `false`, the rollup includes the child records and other goal’s participating records. A participating record must satisfy the following conditions:  
  
-   The source date of the record must be between the start date and the end date of the goal time period, or fall on the start date or the end date of the goal period.  
  
-   The state and status of the record must match the values defined in the goal metric.  
  
-   If a rollup query is specified for the goal, all query conditions must be met.  
  
-   The goal manager must have Read access to the record.  
  
> [!NOTE]
>  The goal rollup fields that do not participate in the rollup are not updated, their values are **null**.  
  
 To specify the rollup expiration time, use the `Organization.GoalRollupExpiryTime` attribute. For example, if the rollup expiration time is set to six months, the goals older than six months will not be rolled up automatically. To specify the frequency of goal rollup, use the `Organization.GoalRollupFrequency` attribute. The frequency can be set on an hourly basis. By default, the goal actual values are recalculated every 24 hours.  
  
 **Override Calculated Values**  
  
 To override the system calculated actual, in-progress, or custom goal rollup field values, use the <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> message to update the goal record. You must set the `Goal.IsOverride` attribute to `true` to notify the system that the rollup field values can be updated. To signal the system that the goal’s rollup field values were overridden and must not be updated during next recalculate operation, set the `Goal.IsOverridden` attribute to `true`. If `Goal.IsOverride` is `false`, an exception is thrown during the update operation. If `Goal.IsOverridden` is `false`, the goal rollup field values will be overwritten during next recalculate operation with system calculated values.  
  
### See also  
 [Goal Management Entities](goal-management-entities.md)   
 [Sample: Roll Up Goal Data for a Custom Period Against the Target Revenue](sample-rollup-goal-data-custom-period-target-revenue.md)   
 [Sample: Roll Up Goal Data for a Fiscal Period Against the Stretch Target Count](sample-rollup-goal-data-fiscal-period-stretch-target-count.md)   
 [Goal Entity](entities/goal.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]