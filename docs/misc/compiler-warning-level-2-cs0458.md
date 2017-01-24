---
title: "編譯器警告 (層級 2) CS0458 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0458"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0458"
ms.assetid: 0986c620-b4bc-4e4b-976f-88359cfa3a45
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0458
運算式的結果一律會是類型 'type name' 的 'null'  
  
 這個警告是由一律會導致 `null` 的 `nullable` 運算式所造成。  
  
 下列程式碼會產生警告 CS0458。  
  
## 範例  
 這個範例說明 `nullable` 類型將導致這個錯誤的數個不同作業。  
  
```  
// CS0458.cs using System; public  class Test { public static void Main() { int a = 5; int? b = a + null;    // CS0458 int? qa = 15; b = qa + null;        // CS0458 b -= null;            // CS0458 int? qa2 = null; b = qa2 + null;       // CS0458 qa2 -= null;          // CS0458 } }  
```