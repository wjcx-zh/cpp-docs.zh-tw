---
title: "編譯器錯誤 CS1611 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1611"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1611"
ms.assetid: 48bfba77-6be2-4242-b1d2-98bf471b6d1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1611
params 參數不可宣告為 ref 或 out  
  
 關鍵字 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 不能與 [params](../Topic/params%20\(C%23%20Reference\).md) 關鍵字搭配使用。  
  
 下列範例會產生 CS1611：  
  
```  
// CS1611.cs public class MyClass { public static void Test(params ref int[] a)   // CS1611, remove ref { } public static void Main() { Test(1); } }  
```