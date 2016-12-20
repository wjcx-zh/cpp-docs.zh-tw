---
title: "編譯器錯誤 CS1003 | Microsoft Docs"
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
  - "CS1003"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1003"
ms.assetid: 59f4d053-13c0-4f79-830e-263acdbe94fa
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1003
語法錯誤，應為 'char'  
  
 編譯器會因為數種錯誤狀況的任何一種而產生這個錯誤。 請檢閱您的程式碼，找出語法錯誤。  
  
 下列範例會產生 CS1003：  
  
```  
// CS1003.cs public class b { public static void Main() { int[] a; a[);   // CS1003 } }  
```