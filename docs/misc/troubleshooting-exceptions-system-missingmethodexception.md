---
title: "疑難排解例外狀況：System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "MissingMethodException 類別"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.MissingMethodException
嘗試動態存取不存在的方法時，就會擲回 <xref:System.MissingMethodException> 例外狀況。  
  
## 相關秘訣  
 **如果類別庫 \(Class Library\) 中的方法被移除或重新命名，請重新編譯參照該方法的任何組件。**  
 擲回這個例外狀況的原因，通常是因為嘗試對未以強式名稱 \(Strong Name\) 參照的組件，動態存取其被刪除或重新命名的方法。  
  
## 備註  
 如果呼叫 Unmanaged 函式，而 CLR 找不到該模組或函式時，就會擲回這個例外狀況。  
  
## 請參閱  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Troubleshooting Interoperability](../Topic/Troubleshooting%20Interoperability%20\(Visual%20Basic\).md)