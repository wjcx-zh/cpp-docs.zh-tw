---
title: "編譯器錯誤 CS0069 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0069"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0069"
ms.assetid: a1b32906-7773-47c6-8515-162a201a9be5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0069
介面中的事件不能有 add 或 remove 存取子  
  
 您不能在 [interface](../Topic/interface%20\(C%23%20Reference\).md) 中定義事件的存取子函式。 如需詳細資訊，請參閱[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)與[介面](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0069：  
  
```  
// CS0069.cs // compile with: /target:library public delegate void EventHandler(); public interface a { event EventHandler Click { remove {} }   // CS0069 event EventHandler Click2;   // OK }  
```