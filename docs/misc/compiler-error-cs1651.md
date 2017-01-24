---
title: "編譯器錯誤 CS1651 | Microsoft Docs"
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
  - "CS1651"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1651"
ms.assetid: ce1043e3-b453-4b4c-b949-f344834e3845
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1651
不能傳遞靜態唯讀欄位 'identifier' 的欄位給 ref 或 out \(除非在靜態建構函式中\)  
  
 如果您將變數傳遞給某個函式，該函式是以 ref 引數作為靜態唯讀欄位的成員，則會發生這個錯誤。 因為函式可能會修改 ref 參數，所以不允許這種情況。 若要解決這個錯誤，請移除欄位的 **readonly** 關鍵字，或不要將唯讀欄位的成員傳遞給函式。 例如，您可能會嘗試建立可修改的暫存變數，並將暫存變數作為 ref 引數傳遞，如下列範例所示。  
  
 下列範例會產生 CS1651：  
  
```  
// CS1651.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { f(ref Outer.inner.i);  // CS1651 // Try this instead: // int tmp = Outer.inner.i; // f(ref tmp); } }  
```