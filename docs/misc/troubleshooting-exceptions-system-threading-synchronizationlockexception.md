---
title: "疑難排解例外狀況：System.Threading.SynchronizationLockException | Microsoft Docs"
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
  - "SynchronizationLockException 例外狀況"
  - "System.Threading.SynchronizationLockException 例外狀況"
ms.assetid: 82d80643-fc5c-40ae-a579-46869772d25c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Threading.SynchronizationLockException
當方法要求呼叫端必須在指定 `Monitor` 的上具有鎖定，且方法是由未擁有該鎖定的呼叫端所叫用 \(Invoke\) 時，所擲回的例外狀況。  
  
## 備註  
 從程式碼的未同步化區塊中呼叫 <xref:System.Threading.SynchronizationLockException> 類別的 <xref:System.Threading.Monitor.Exit%2A>、<xref:System.Threading.Monitor.Pulse%2A>、<xref:System.Threading.Monitor.PulseAll%2A> 及 <xref:System.Threading.Monitor.Wait%2A> 方法，就會擲回 `Monitor`。  
  
## 請參閱  
 <xref:System.Threading.SynchronizationLockException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)