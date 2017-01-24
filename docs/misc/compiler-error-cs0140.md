---
title: "編譯器錯誤 CS0140 | Microsoft Docs"
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
  - "CS0140"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0140"
ms.assetid: 61787b8a-7b69-41c1-8ee3-87f619698594
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0140
標籤 'label' 重複  
  
 具有相同名稱的標籤重複出現。 如需詳細資訊，請參閱[goto](../Topic/goto%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0140：  
  
```  
// CS0140.cs namespace MyNamespace { public class MyClass { public static void Main() { label1: int i = 0; label1: int j = 0;   // CS0140, comment this line to resolve goto label1; } } }  
```