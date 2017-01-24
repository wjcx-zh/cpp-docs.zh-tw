---
title: "編譯器錯誤 CS0152 | Microsoft Docs"
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
  - "CS0152"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0152"
ms.assetid: 4915ca16-6485-4e1f-ace0-c71a7b339ba4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0152
此 switch 陳述式中已有標籤 'label'  
  
 [switch](../Topic/switch%20\(C%23%20Reference\).md) 陳述式中的標籤重複。 如需詳細資訊，請參閱[switch](../Topic/switch%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0152：  
  
```  
// CS0152.cs namespace MyNamespace { public class MyClass { public static void Main() { int i = 0; switch (i) { case 1: i++; return; case 1:   // CS0152, two case 1 statements i++; return; } } } }  
```