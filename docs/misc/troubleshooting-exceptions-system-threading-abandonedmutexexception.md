---
title: "疑難排解例外狀況：System.Threading.AbandonedMutexException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Threading.AbandonedMutexException 例外狀況"
  - "AbandonedMutexException 例外狀況"
ms.assetid: 11157066-32ed-492c-83af-29983f915eec
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Threading.AbandonedMutexException
當一個執行緒正在等候 Mutex 物件，而另一個執行緒卻以結束但未釋放 Mutex 的方式放棄 Mutex 時，所擲回的例外狀況。  
  
## 備註  
 放棄的 Mutex 通常表示程式碼中的嚴重錯誤。 當執行緒結束但未釋放 Mutex 時，Mutex 所保護的資料結構便可能處於不一致的狀態。 如果能夠確認資料結構的完整性，要求 Mutex 擁有權的下一個執行緒就可以處理這個例外狀況並繼續進行。  
  
## 請參閱  
 <xref:System.Threading.AbandonedMutexException>   
 <xref:System.Threading.Mutex>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)