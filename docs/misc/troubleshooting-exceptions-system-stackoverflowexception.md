---
title: "疑難排解例外狀況：System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "StackOverflowException 類別"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.StackOverflowException
因為過多的巢狀方法呼叫而導致執行堆疊溢位 \(Stack Overflow\) 時，就會擲回 <xref:System.StackOverflowException> 例外狀況。  
  
## 相關秘訣  
 請確定沒有無限迴圈或無限遞迴的情況。  
 過多的方法呼叫通常指示非常深或未受限制的遞迴。  
  
## 備註  
 您不能攔截堆疊溢位例外狀況，因為例外狀況處理程式碼可能需要此堆疊， 當正常的應用程式中發生了堆疊溢位時，Common Language Runtime \(CLR\) 就會終止處理序。  
  
 裝載 CLR 的應用程式可以變更預設行為，並指定 CLR 在發生例外狀況的地方卸載應用程式定義域，但仍會繼續處理序。 如需詳細資訊，請參閱[ICLRPolicyManager 介面](../Topic/ICLRPolicyManager%20Interface.md)。  
  
## 請參閱  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Loop Structures](../Topic/Loop%20Structures%20\(Visual%20Basic\).md)