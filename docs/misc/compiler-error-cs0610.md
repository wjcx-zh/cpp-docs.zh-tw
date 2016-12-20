---
title: "編譯器錯誤 CS0610 | Microsoft Docs"
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
  - "CS0610"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0610"
ms.assetid: 6cdce74c-5c00-4539-9df1-32be70e9912d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0610
欄位或屬性不可為類型 'type'  
  
 有一些不能當成欄位或屬性使用的類型。 這些類型包括 **System.ArgIterator** 和 **System.TypedReference**。  
  
 使用 **System.TypedReference** 作為欄位之後，下列範例會產生 CS0610：  
  
```  
// CS0610.cs public class MainClass { System.TypedReference i;   // CS0610 public static void Main () { } public static void Test(System.TypedReference i)   // OK { } }  
```