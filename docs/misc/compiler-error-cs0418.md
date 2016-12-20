---
title: "編譯器錯誤 CS0418 | Microsoft Docs"
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
  - "CS0418"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0418"
ms.assetid: b78fafde-428b-4fa2-a933-c4614760bb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0418
'class name': 抽象類別不能是 sealed 或 static  
  
 抽象類別不能用來建立物件，除非是衍生物件，因此密封沒有任何意義。 抽象類別也無法有意義地設為靜態；抽象類別的設計是為了支援物件階層架構，此階層架構將會使用抽象類別作為基底。  
  
## 範例  
 下列範例會產生 CS0418：  
  
```  
// CS0418.cs public abstract sealed class C  // CS0418 { } sealed static class S  // CS0418 { } public class MyClass { public static void Main() { } }  
```