---
title: "疑難排解例外狀況：System.DuplicateWaitObjectException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DuplicateWaitObjectException 類別"
ms.assetid: b9ff6932-a7cf-4a89-bd7d-e4ef1a3ff353
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.DuplicateWaitObjectException
如果傳遞至 <xref:System.DuplicateWaitObjectException> 或 <xref:System.Threading.WaitHandle> 的 <xref:System.Threading.WaitHandle.WaitAll%2A> 物件陣列中包含任何重複的作業系統控制代碼，就會擲回 <xref:System.Threading.WaitHandle.WaitAny%2A> 例外狀況。  
  
## 相關秘訣  
 **請確定傳遞至 WaitAll 或 WaitAny 的 WaitHandle 物件是唯一的。**  
 <xref:System.Threading.WaitHandle> 陣列無法將多個參考包含至同一物件中。  
  
### 備註  
 Common Language Runtime \(CLR\) 提供了執行緒同步機制，這個機制是以 <xref:System.Threading.WaitHandle> 物件陣列中等待執行的同步物件為基礎。  
  
## 請參閱  
 <xref:System.DuplicateWaitObjectException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)