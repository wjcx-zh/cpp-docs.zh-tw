---
title: "編譯器錯誤 CS0689 | Microsoft Docs"
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
  - "CS0689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0689"
ms.assetid: 5c555c2e-8e71-4097-8dbf-52dbafe7bf57
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0689
無法由 'identifier' 衍生，因為它是類型參數  
  
 類型參數不能指定泛型類別的基底類別或介面。 而是衍生自特定的類別或介面，或特定的泛型類別，或是包含為成員的未知類型。  
  
 下列範例會產生 CS0689：  
  
```  
// CS0689.cs class A<T> : T   // CS0689 { }  
```