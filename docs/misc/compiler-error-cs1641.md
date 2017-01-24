---
title: "編譯器錯誤 CS1641 | Microsoft Docs"
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
  - "CS1641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1641"
ms.assetid: ba6eab47-c28b-4531-b6a0-6d538b236d19
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1641
固定大小緩衝區欄位在欄位名稱後面必須有陣列大小規範  
  
 不同於標準陣列，固定大小的緩衝區必須在宣告點指定常數大小。 若要解決這個錯誤，請加入一個正整數常值或常數正整數，並在識別項之後放置方括弧。  
  
 下列範例會產生 CS1641：  
  
```  
// CS1641.cs // compile with: /unsafe /target:library unsafe struct S { fixed int [] a;  // CS1641 // OK fixed int b [10]; const int c = 10; fixed int d [c]; }  
```