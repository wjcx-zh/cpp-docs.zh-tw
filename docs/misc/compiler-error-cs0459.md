---
title: "編譯器錯誤 CS0459 | Microsoft Docs"
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
  - "CS0459"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0459"
ms.assetid: 01b058dd-8d65-4e9d-9de1-d47f9488d22a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0459
無法取得唯讀區域變數的位址  
  
 使用 C\# 語言時，有三種常見的案例會產生唯讀區域變數：`foreach`、`using` 和 `fixed`。 在上述每一種情況下，不允許您寫入唯讀區域變數，或取得它的位址。 編譯器發現您正在嘗試取得唯讀區域變數的位址時，會產生這個錯誤。  
  
## 範例  
 嘗試在 `foreach` 迴圈和 `fixed` 陳述式區塊中取得唯讀區域變數的位址時，下列範例會產生 CS0459。  
  
```  
// CS0459.cs // compile with: /unsafe class A { public unsafe void M1() { int[] ints = new int[] { 1, 2, 3 }; foreach (int i in ints) { int *j = &i;  // CS0459 } fixed (int *i = &_i) { int **j = &i;  // CS0459 } } private int _i = 0; }  
```