---
title: "疑難排解例外狀況：System.Windows.Xps.XpsWriterException | Microsoft Docs"
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
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "System.Windows.Xps.XpsWriterException 例外狀況"
  - "XpsWriterException 例外狀況"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Windows.Xps.XpsWriterException
當呼叫 <xref:System.Windows.Xps.XpsWriterException> 或 <xref:System.Windows.Xps.XpsDocumentWriter> 物件的方法與物件的目前狀態不相容時，會擲回 <xref:System.Windows.Xps.VisualsToXpsDocument> 例外狀況 \(Exception\)。  
  
## 備註  
 例如，如果在任一物件型別在物件未執行非同步寫入作業時呼叫物件的 `CancelAsync` 方法，則會擲回這個例外狀況。  
  
## 請參閱  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)