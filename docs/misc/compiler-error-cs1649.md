---
title: "編譯器錯誤 CS1649 | Microsoft Docs"
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
  - "CS1649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1649"
ms.assetid: 6355c7f2-157c-441d-8925-500062988636
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1649
無法傳遞 ref 或 out 給唯讀欄位 'identifier' 的成員 \(除非是在建構函式中\)  
  
 如果您將變數傳遞給某個函式，該函式是以 `ref` 或 `out` 引數作為 `readonly` 欄位的成員，就會發生此錯誤。 由於該函式可修改 `ref` 和 `out` 參數，因此不允許這種情況。 若要解決此錯誤，請移除欄位的 `readonly` 關鍵字，或不要將 `readonly` 欄位的成員傳遞給函式。 例如，您可能會嘗試建立可以修改的暫存變數，並將其作為 `ref` 引數傳遞，如下列範例所示。  
  
## 範例  
 下列範例會產生 CS1649：  
  
```  
// CS1649.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { Outer outer = new Outer(); f(ref outer.inner.i);  // CS1649 // Try this code instead: // int tmp = outer.inner.i; // f(ref tmp); } }  
```