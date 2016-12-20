---
title: "編譯器錯誤 CS1521 | Microsoft Docs"
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
  - "CS1521"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1521"
ms.assetid: 9a482b33-24f2-4654-81b4-be40bf56d624
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1521
基底類型無效  
  
 [base](../Topic/base%20\(C%23%20Reference\).md) 類別規格的格式不正確。  
  
 下列範例會產生 CS1521：  
  
```  
// CS1521.cs class CMyClass { public static void Main() { } } class CMyClass1 : CMyClass     // OK { } class CMyClass2 : CMyClass[]   // CS1521 { } class CMyClass3 : CMyClass*    // CS1521 { }  
```