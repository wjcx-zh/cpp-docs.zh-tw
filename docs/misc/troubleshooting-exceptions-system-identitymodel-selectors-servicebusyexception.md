---
title: "疑難排解例外狀況：System.IdentityModel.Selectors.ServiceBusyException | Microsoft Docs"
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
  - "ServiceBusyException 例外狀況"
  - "System.IdentityModel.Selectors.ServiceBusyException 例外狀況"
ms.assetid: 88acdc6b-45ad-40c6-aa5c-3b56244edcee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IdentityModel.Selectors.ServiceBusyException
若擲回 <xref:System.IdentityModel.Selectors.ServiceBusyException> 例外狀況，表示 CardSpace 服務正忙於處理其他要求。 CardSpace 不會將要求放入佇列，並且一次只能服務一個要求。  
  
 請判斷是否有另一個 CardSpace 的執行個體正在執行。 如果有另一個執行個體正在執行，請從 \[工作管理員\] 停止 icardagt.exe 處理序，結束該處理序。  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.ServiceBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)