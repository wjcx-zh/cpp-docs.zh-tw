---
title: "編譯器錯誤 CS1642 | Microsoft Docs"
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
  - "CS1642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1642"
ms.assetid: 2efeedf1-1839-485d-8b8c-9045df1951f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1642
固定大小緩衝區欄位必須是結構的成員。  
  
 如果不是 `struct`，而是 `class` 的緩衝區欄位使用固定大小，就會發生這個錯誤。 若要解決這個錯誤，請將 `class` 變更為 `struct`，或宣告欄位為一般陣列。  
  
## 範例  
 下列範例會產生 CS1642。  
  
```  
// CS1642.cs // compile with: /unsafe /target:library unsafe class C { fixed int a[10];   // CS1642 } unsafe struct D { fixed int a[10]; } unsafe class E { public int[] a = null; }  
```