---
title: "疑難排解例外狀況：System.ServiceModel.ServiceActivationException | Microsoft Docs"
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
  - "ServiceActivationException 例外狀況"
  - "System.ServiceModel.ServiceActivationException 例外狀況"
ms.assetid: 32a3ea87-d6da-40bf-ba04-e862ac122391
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.ServiceModel.ServiceActivationException
當服務無法啟動時，會擲回 <xref:System.ServiceModel.ServiceActivationException> 例外狀況 \(Exception\)。  
  
## 備註  
 這個例外狀況 \(Exception\) 的衍生來源是 <xref:System.ServiceModel.CommunicationException>，它會顯示可能會在端點間通訊期間擲回，並預期要由穩固的 [!INCLUDE[vsindigo](../misc/includes/vsindigo_md.md)] 用戶端和服務應用程式處理之可修復錯誤的類別。 若要避免由比較泛型的 <xref:System.ServiceModel.CommunicationException> 處理常式來攔截比較特定的 <xref:System.ServiceModel.ActionNotSupportedException>，請在處理 <xref:System.ServiceModel.CommunicationException> 之前攔截此例外狀況 \(Exception\)。  
  
## 請參閱  
 <xref:System.ServiceModel.ServiceActivationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)