---
title: "編譯器警告 (層級 1) CS0197 | Microsoft Docs"
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
  - "CS0197"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0197"
ms.assetid: 2b5b1b8d-ce13-4bd7-b80a-abb80e9f79ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0197
將 'argument' 當做 ref 或 out 傳遞或取得它的位址可能會導致執行階段例外狀況，因為它是 marshal\-by\-reference 類別的欄位  
  
 任何直接或間接衍生自 <xref:System.MarshalByRefObject> 的類別都是 marshal\-by\-reference 類別。 這種類別可以跨處理序與電腦界限依參考封送處理。 因此，這種類別的執行個體可以是遠端物件的 Proxy。 您無法將 Proxy 物件的欄位當成 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 傳遞。 所以，您無法將這種類別的欄位當做 `ref` 或 `out` 傳遞，除非執行個體是[這個](../Topic/this%20\(C%23%20Reference\).md)，其不可為 Proxy 物件。  
  
## 範例  
 下列範例會產生 CS0197。  
  
```  
// CS0197.cs // compile with: /W:1 class X : System.MarshalByRefObject { public int i; } class M { public int i; static void AddSeventeen(ref int i) { i += 17; } static void Main() { X x = new X(); x.i = 12; AddSeventeen(ref x.i);   // CS0197 // OK M m = new M(); m.i = 12; AddSeventeen(ref m.i); } }  
```