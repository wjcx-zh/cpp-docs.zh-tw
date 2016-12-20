---
title: "編譯器錯誤 CS0153 | Microsoft Docs"
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
  - "CS0153"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0153"
ms.assetid: 3a0791e9-0ab9-4eaa-a230-d39aabaa9d5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0153
goto case 只有在 switch 陳述式中有效  
  
 嘗試在 **switch** 陳述式外部使用 [switch](../Topic/switch%20\(C%23%20Reference\).md) 語法。 如需詳細資訊，請參閱[switch](../Topic/switch%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0153：  
  
```  
// CS0153.cs public class a { public static void Main() { goto case 5;   // CS0153 } }  
```