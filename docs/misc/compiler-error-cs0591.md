---
title: "編譯器錯誤 CS0591 | Microsoft Docs"
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
  - "CS0591"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0591"
ms.assetid: b8acbcdb-dc66-4338-9ddd-d606e5a2c57e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0591
對 'attribute' 屬性的引數值無效  
  
 將無效的引數或兩個互斥的引數傳遞至屬性。  
  
## 範例  
 下列範例會產生 CS0591：  
  
```  
// CS0591.cs using System; [AttributeUsage(0)]   // CS0591 class I: Attribute { } public class a { public static void Main() { } }  
```