---
title: "疑難排解例外狀況：System.Collections.Generic.KeyNotFoundException | Microsoft Docs"
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
  - "KeyNotFoundException 類別"
ms.assetid: de33f5bb-5709-46fe-b889-7105dbd24299
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Collections.Generic.KeyNotFoundException
嘗試使用不存在的機碼從集合中擷取機碼或機碼值組時，就會擲回 <xref:System.Collections.Generic.KeyNotFoundException>。  
  
## 相關秘訣  
 **請檢查您所使用的機碼，存在於您嘗試存取的集合中。**  
 當作業嘗試擷取集合中的項目，但該作業所用的機碼卻不存在這個集合中時，就會發生這個例外狀況。  
  
### 備註  
 可以使用 <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> 方法判斷機碼是否存在。  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.KeyNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)