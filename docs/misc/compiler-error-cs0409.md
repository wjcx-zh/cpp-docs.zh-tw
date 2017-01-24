---
title: "編譯器錯誤 CS0409 | Microsoft Docs"
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
  - "CS0409"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0409"
ms.assetid: 23d86c13-7978-41b7-a087-ffcea52476fa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0409
已為類型參數 'type parameter' 指定了條件約束子句。 類型參數的所有條件約束，都必須在單一 where 子句中指定。  
  
 找到單一類型參數的多個條件約束子句 \(where 子句\)。 請移除多餘的 where 子句，或更正 where 子句，讓每個子句都有唯一類型參數。  
  
```  
// CS0409.cs interface I { } class C<T1, T2> where T1 : I where T1 : I  // CS0409 – T1 used twice { }  
```