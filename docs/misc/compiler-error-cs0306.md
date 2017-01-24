---
title: "編譯器錯誤 CS0306 | Microsoft Docs"
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
  - "CS0306"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0306"
ms.assetid: f340a3ce-6140-4001-bb00-628a2985ddd6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0306
類型 'type' 不能用來作為類型引數  
  
 此類型不可當做類型參數來使用。 這可能是因為此類型為指標類型。  
  
 下列範例會產生 CS0306：  
  
```  
// CS0306.cs class C<T> { } class M { // CS0306 – int* not allowed as a type parameter C<int*> f; }  
```