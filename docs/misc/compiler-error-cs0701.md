---
title: "編譯器錯誤 CS0701 | Microsoft Docs"
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
  - "CS0701"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0701"
ms.assetid: eb844e31-00bd-468d-9f77-11d10a4ef120
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0701
'identifier' 不是有效的條件約束。 用作為條件約束的類型，必須是介面、非密封類別或類型參數。  
  
 如果密封類型用作為條件約束，就會發生這個錯誤。 若要解決此錯誤，請僅使用非密封類型作為條件約束。  
  
## 範例  
 下列範例會產生 CS0701：  
  
```  
// CS0701.cs // compile with: /target:library class C<T> where T : System.String {}   // CS0701 class D<T> where T : System.Attribute {}   // OK  
```