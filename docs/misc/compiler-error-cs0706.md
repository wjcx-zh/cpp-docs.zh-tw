---
title: "編譯器錯誤 CS0706 | Microsoft Docs"
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
  - "CS0706"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0706"
ms.assetid: bc3ac5c0-8c96-43c8-b10a-69bd31b38e4a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0706
條件約束類型無效。 用作為條件約束的類型，必須是介面、非密封類別或類型參數。  
  
 當條件約束子句中使用無效的建構時，就會發生這個錯誤。 若要避免這個錯誤，請使用介面或非密封類別，而不是造成錯誤的建構。  
  
## 範例  
 下列範例會產生 CS0706。  
  
```  
// CS0706.cs // compile with: /target:library class A {} class C<T> where T : int[] {}  // CS0706 class D<T> where T : A {}  // OK  
```