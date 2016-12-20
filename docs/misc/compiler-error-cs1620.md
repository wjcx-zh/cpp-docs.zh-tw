---
title: "編譯器錯誤 CS1620 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1620"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1620"
ms.assetid: 13933976-218a-4fe2-8fde-5b9af522e2e5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1620
傳遞引數 'number' 時必須包含 'keyword' 關鍵字  
  
 如果您要將引數傳遞給採用 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 參數的函式，但未在呼叫點包括 `ref` 或 `out` 關鍵字或所包括的關鍵字錯誤，則會發生這個錯誤。 錯誤文字表示要使用適當的關鍵字，以及造成失敗的引數。  
  
 下列範例會產生 CS1620：  
  
```  
// CS1620.cs class C { void f(ref int i) {} public static void Main() { int x = 1; f(out x);  // CS1620 – f takes a ref parameter, not an out parameter // Try this line instead: // f(ref x); } }  
```