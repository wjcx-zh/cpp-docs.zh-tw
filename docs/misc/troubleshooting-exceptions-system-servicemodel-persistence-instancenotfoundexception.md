---
title: "疑難排解例外狀況：System.ServiceModel.Persistence.InstanceNotFoundException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "InstanceNotFoundException 例外狀況"
  - "System.ServiceModel.Persistence.InstanceNotFoundException 例外狀況"
ms.assetid: e3905352-dff0-41d4-b970-8e1b26d85a83
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.ServiceModel.Persistence.InstanceNotFoundException
在下列情況下，會擲回 <xref:System.ServiceModel.Persistence.InstanceNotFoundException> 例外狀況 \(Exception\)：  
  
-   對已標記為完成的永久性服務執行個體執行作業。  
  
-   <xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory> 建立的永續性提供者嘗試要鎖定、解除鎖定，或處理資料庫內找不到的狀態資料。  
  
## 請參閱  
 <xref:System.ServiceModel.Persistence.InstanceNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)