---
title: "編譯器錯誤 CS1012 | Microsoft Docs"
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
  - "CS1012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1012"
ms.assetid: 4acc5fe0-da47-4882-b7d8-557767d7cf03
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1012
字元常值中有太多字元  
  
 已嘗試初始化多個字元的 [char](../Topic/char%20\(C%23%20Reference\).md) 常數。  
  
 進行資料繫結時，也可能發生 CS1012。 例如，下面這行會產生錯誤：  
  
 `<%# DataBinder.Eval(Container.DataItem, 'doctitle') %>`  
  
 請改嘗試下面這行：  
  
 `<%# DataBinder.Eval(Container.DataItem, "doctitle") %>`  
  
 下列範例會產生 CS1012：  
  
```  
// CS1012.cs class Sample { static void Main() { char a = 'xx';   // CS1012 char a2 = 'x';   // OK System.Console.WriteLine(a2); } }  
```