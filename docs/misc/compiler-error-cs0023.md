---
title: "編譯器錯誤 CS0023 | Microsoft Docs"
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
  - "CS0023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0023"
ms.assetid: 7a30073c-99de-41fa-ac6d-4a0dfbb76de9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0023
無法將運算子 'operator' 套用至類型 'type' 的運算元  
  
 嘗試將運算子套用至類型不應與運算子一起使用的變數。 如需詳細資訊，請參閱 [類型](../Topic/Types%20\(C%23%20Programming%20Guide\).md) 與 [C\# 運算子](../Topic/C%23%20Operators.md)。  
  
 下列範例會產生 CS0023：  
  
```  
// CS0023.cs namespace x { public class a { public static void Main() { string s = "hello"; s = -s;   // CS0023, minus operator not allowed on strings } } }  
```