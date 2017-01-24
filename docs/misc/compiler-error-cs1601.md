---
title: "編譯器錯誤 CS1601 | Microsoft Docs"
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
  - "CS1601"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1601"
ms.assetid: 5efa1d2d-c70c-446d-a51f-d23d8a3be22e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1601
方法或委派參數不能屬於類型 'type'  
  
 .NET Framework 類別庫中的某些類型 \(例如 <xref:System.TypedReference>、<xref:System.RuntimeArgumentHandle> 和 <xref:System.ArgIterator>\) 不能當做 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 參數使用，因為它們可能用來執行不安全的作業。  
  
 下列範例會產生 CS1601：  
  
```  
// CS1601.cs using System; class MyClass { public void Test1 (ref TypedReference t)   // CS1601 { } public void Test2 (out ArgIterator t)   // CS1601 { } }  
```