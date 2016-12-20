---
title: "編譯器錯誤 CS0466 | Microsoft Docs"
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
  - "CS0466"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0466"
ms.assetid: db6be72b-120a-4b48-b41c-a738d02adae0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0466
'method1' 不應有 params 參數，因為 'method2' 沒有此參數  
  
 您不能在類別成員上使用 `params` 參數，如果實作的介面未使用它。  
  
## 範例  
 下列範例會產生 CS0466：  
  
```  
// CS0466.cs interface I { void F1(params int[] a); void F2(int[] a); } class C : I { void I.F1(params int[] a) {} void I.F2(params int[] a) {}   // CS0466 void I.F2(int[] a) {}   // OK public static void Main() { I i = (I) new C(); i.F1(new int[] {1, 2} ); i.F2(new int[] {1, 2} ); } }  
```