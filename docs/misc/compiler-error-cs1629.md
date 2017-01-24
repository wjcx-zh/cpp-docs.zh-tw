---
title: "編譯器錯誤 CS1629 | Microsoft Docs"
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
  - "CS1629"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1629"
ms.assetid: 907eae46-0265-4cd0-b27b-ff555d004259
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1629
Unsafe 程式碼不可出現在迭代器中  
  
 C\# 語言規格不容許迭代器中有 Unsafe 程式碼。  
  
 下列範例會產生 CS1629：  
  
```  
// CS1629.cs // compile with: /unsafe using System.Collections.Generic; class C { IEnumerator<int> IteratorMeth() { int i; unsafe  // CS1629 { int *p = &i; yield return *p; } } }  
```