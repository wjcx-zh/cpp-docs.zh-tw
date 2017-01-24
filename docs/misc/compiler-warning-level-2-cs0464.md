---
title: "編譯器警告 (層級 2) CS0464 | Microsoft Docs"
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
  - "CS0464"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0464"
ms.assetid: 3dff97d4-e1f6-4a71-91e2-68cffc38d49a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0464
與類型 'type' 的 null 進行比較，一律會產生 'false'  
  
 如果您執行可為 Null 的變數與 Null 的比較，而且比較不是 `==` 或 `!=`，則會產生這個警告。 若要解決這個錯誤，請確認您是否確實要檢查 `null` 的值。`i == null` 這類比較可以是 true 或 false。`i > null` 這類比較一律為 false。  
  
## 範例  
 下列範例會產生 CS0464。  
  
```  
// CS0464.cs class MyClass { public static void Main() { int? i = 0; if (i < null) ;   // CS0464 i++; } }  
```