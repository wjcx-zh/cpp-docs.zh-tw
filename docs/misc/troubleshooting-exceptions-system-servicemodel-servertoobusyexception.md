---
title: "疑難排解例外狀況：System.ServiceModel.ServerTooBusyException | Microsoft Docs"
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
  - "System.ServiceModel.ServerTooBusyException 例外狀況"
  - "ServerTooBusyException 例外狀況"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.ServiceModel.ServerTooBusyException
當伺服器過於忙碌，無法接受訊息時，就會擲回 <xref:System.ServiceModel.ServerTooBusyException> 例外狀況。  
  
## 備註  
 此例外狀況是衍生自 <xref:System.ServiceModel.CommunicationException>，表示可能會在端點間通訊期間，擲回可修復錯誤的類別。 這些例外狀況必須由更穩定的用戶端和服務 [!INCLUDE[vsindigo](../misc/includes/vsindigo_md.md)] 應用程式處理。 若要防止 <xref:System.ServiceModel.CommunicationException> 的處理常式攔截更特定的 <xref:System.ServiceModel.ServerTooBusyException>，可在處理 <xref:System.ServiceModel.CommunicationException> 之前攔截此例外狀況。  
  
## 請參閱  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)