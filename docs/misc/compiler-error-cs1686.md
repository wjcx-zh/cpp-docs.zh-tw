---
title: "編譯器錯誤 CS1686 | Microsoft Docs"
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
  - "CS1686"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1686"
ms.assetid: 46a9e82b-57f4-416d-8e49-242bfff5433a
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1686
無法取得區域 'variable' 或其成員的位址，也無法用於匿名方法或 Lambda 運算式內部  
  
 如果您使用變數，並嘗試接受其位址，而且其中一個動作是在匿名方法內部完成，則會產生這個錯誤。  
  
## 範例  
 下列範例會產生 CS1686。  
  
```  
// CS1686.cs // compile with: /unsafe /target:library class MyClass { public unsafe delegate int * MyDelegate(); public unsafe int * Test() { int j = 0; MyDelegate d = delegate { return &j; };   // CS1686 return &j;   // OK } }  
```