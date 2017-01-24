---
title: "編譯器錯誤 CS0718 | Microsoft Docs"
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
  - "CS0718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0718"
ms.assetid: f18ea7b7-7495-4039-9876-409e9fe98ba1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0718
'type': 靜態類型不能當做類型引數使用  
  
 靜態類型無法具現化，因為它不能作為泛型引數。 若要解決此錯誤，請從泛型引數移除靜態類型。  
  
## 範例  
 下列範例會產生 CS0718：  
  
```  
// CS0718.cs public static class SC { public static void F() { } } public class G<T> { } public class CMain { public static void Main() { G<SC> gsc = new G<SC>();  // CS0718 } }  
```