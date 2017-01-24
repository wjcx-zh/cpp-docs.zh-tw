---
title: "編譯器錯誤 CS0698 | Microsoft Docs"
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
  - "CS0698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0698"
ms.assetid: 68211652-fdfa-4d37-9451-f0b4238f9fe6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0698
泛型類型不能衍生自 'class'，因為它是屬性類別  
  
 任何衍生自屬性類別的類別皆必須為屬性。 屬性不可以是泛型類型。  
  
 下列範例會產生 CS0698：  
  
```  
// CS0698.cs class C<T> : System.Attribute  // CS0698 { }  
```