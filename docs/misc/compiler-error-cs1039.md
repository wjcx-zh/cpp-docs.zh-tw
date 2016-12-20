---
title: "編譯器錯誤 CS1039 | Microsoft Docs"
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
  - "CS1039"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1039"
ms.assetid: 266e9f7f-fe17-445a-aefd-6b7795167d68
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1039
未結束的字串常值  
  
 編譯器偵測到格式不正確的[字串](../Topic/string%20\(C%23%20Reference\).md)常值。  
  
## 範例  
 下列範例會產生 CS1039。 若要解決這個錯誤，請加入右引號。  
  
```  
// CS1039.cs public class MyClass { public static void Main() { string b = @"hello, world;   // CS1039 } }  
```