---
title: "疑難排解例外狀況：System.OperationCanceledException | Microsoft Docs"
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
  - "OperationCanceledException 類別"
ms.assetid: 275e2887-7491-432b-9b80-a21bb794be29
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.OperationCanceledException
當您進行一項作業，而且將其 <xref:System.OperationCanceledException> 設定為 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>，其後又取消該作業時，就會擲回 `ThrowException`。  
  
## 相關秘訣  
 如果您不希望擲回這個例外狀況，請將 <xref:System.OperationCanceledException> 設定為 `DoNothing`。  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption> 的預設值為 `ThrowException`。 如果您不希望使用者取消該作業時擲回這個例外狀況，請將其列舉值設定為 `DoNothing`。  
  
## 請參閱  
 <xref:System.OperationCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)