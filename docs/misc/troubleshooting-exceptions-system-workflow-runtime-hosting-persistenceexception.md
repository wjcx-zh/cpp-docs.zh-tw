---
title: "疑難排解例外狀況：System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
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
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "PersistenceException 例外狀況"
  - "System.Workflow.Runtime.Hosting.PersistenceException 例外狀況"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Workflow.Runtime.Hosting.PersistenceException
當持續性服務無法完成要求時，就會擲回 <xref:System.Workflow.Runtime.Hosting.PersistenceException> 例外狀況。  
  
## 備註  
 如果服務無法完成要求 \(將完成的範圍或工作流程執行個體認可至其資料庫\)，<xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> 就會擲回 <xref:System.Workflow.Runtime.Hosting.PersistenceException>。  
  
 如果您藉由衍生自 <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> 類別或 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> 類別的方式實作持續性服務，則可以擲回含適當訊息的 <xref:System.Workflow.Runtime.Hosting.PersistenceException>，指出您的服務碰到了錯誤情況，無法完成工作流程執行階段引擎建立的要求。  
  
 如需詳細資訊，請參閱 <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>。  
  
## 請參閱  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)