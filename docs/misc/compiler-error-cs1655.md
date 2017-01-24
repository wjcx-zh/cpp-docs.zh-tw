---
title: "編譯器錯誤 CS1655 | Microsoft Docs"
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
  - "CS1655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1655"
ms.assetid: 041e9daa-c026-494f-b086-0db9a23c969b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1655
無法將 'variable' 的欄位當做 ref 或 out 引數傳遞，因為它是 'readonly variable type'  
  
 如果您嘗試將 [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) 變數、[using](../Topic/using%20Statement%20\(C%23%20Reference\).md) 變數或 [fixed](../Topic/fixed%20Statement%20\(C%23%20Reference\).md) 變數的成員當做 ref 或 out 引數傳遞給函式，則會發生這個錯誤。 因為這些變數在這些內容中視為唯讀，所以這是不允許的作業。  
  
 下列範例會產生 CS1655：  
  
```  
// CS1655.cs struct S { public int i; } class CMain { static void f(ref int iref) { } public static void Main() { S[] sa = new S[10]; foreach(S s in sa) { CMain.f(ref s.i);  // CS1655 } } }  
```