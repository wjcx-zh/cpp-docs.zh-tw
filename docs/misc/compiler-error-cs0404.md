---
title: "編譯器錯誤 CS0404 | Microsoft Docs"
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
  - "CS0404"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0404"
ms.assetid: 60bef49e-e0b7-4e9e-aab3-7afc20a19cb8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0404
未預期的 '\<' : 屬性不可為泛型  
  
 屬性中不允許泛型類型參數。 請移除類型參數和角括弧。  
  
 下列範例會產生 CS0404：  
  
```  
// CS0404.cs [MyAttrib<int>]  // CS0404 class C { public static void Main() { } }  
```