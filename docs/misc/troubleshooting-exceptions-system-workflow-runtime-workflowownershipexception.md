---
title: "疑難排解例外狀況：System.Workflow.Runtime.WorkflowOwnershipException | Microsoft Docs"
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
  - "EHWRWorkflowOwnership"
helpviewer_keywords: 
  - "System.Workflow.Runtime.WorkflowOwnershipException 例外狀況"
  - "WorkflowOwnershipException 例外狀況"
ms.assetid: 20291283-dfc8-4e34-b84d-f380e04be376
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Workflow.Runtime.WorkflowOwnershipException
當工作流程執行階段引擎嘗試載入工作流程執行個體 \(Instance\)，但是該執行個體目前已由另一個工作流程執行階段引擎執行個體載入時，便會擲回 <xref:System.Workflow.Runtime.WorkflowOwnershipException> 例外狀況 \(Exception\)。 此外，當工作流程執行階段引擎嘗試於載入工作流程時指定之擁有權逾時已過期之後儲存工作流程時，便會擲回此例外狀況。  
  
## 請參閱  
 <xref:System.Workflow.Runtime.WorkflowOwnershipException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)