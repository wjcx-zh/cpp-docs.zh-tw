---
title: "疑難排解例外狀況：System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "System.Workflow.Activities.EventDeliveryFailedException 例外狀況"
  - "EventDeliveryFailedException 例外狀況"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Workflow.Activities.EventDeliveryFailedException
因為主應用程式 \(Host\) 無法傳遞至工作流程執行個體而引發某個事件時，就會擲回 <xref:System.Workflow.Activities.EventDeliveryFailedException> 例外狀況。 通常這個事件是針對工作流程執行個體，從 <xref:System.Workflow.Activities.ExternalDataExchangeService> 引發的。 這個類別無法被繼承。  
  
## 備註  
 擲回此例外狀況時，下列字串會新增至事件記錄檔中：`Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered`。  
  
 使用狀態機器工作流程時，您可能會收到含`Queue '{0}' is not enabled` 訊息的例外狀況。 當狀態機器的目前狀態無法處理特定事件時，就會發生這種情形。 例如，這個訊息會在狀態 \(除了目前狀態包含 <xref:System.Workflow.Activities.EventDrivenActivity>\) 含有佇列 <xref:System.Workflow.Activities.HandleExternalEventActivity> 所表示的 `'{0}'` 時發生。  
  
## 請參閱  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)