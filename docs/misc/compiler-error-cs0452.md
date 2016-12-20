---
title: "編譯器錯誤 CS0452 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0452"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0452"
ms.assetid: 50a87734-fe07-4bce-891d-a76e131db6cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0452
類型 'type name' 必須是參考類型，才能在泛型類型或方法 'identifier of generic' 中作為參數 'parameter name' 使用  
  
 當您傳遞實值類型，例如 `struct` 或 `int`，作為泛型類型或方法的參數，而此泛型類型或方法具有參考類型條件約束，就會發生此錯誤。  
  
## 範例  
 下列程式碼會產生錯誤 CS0452：  
  
```  
// CS0452.cs using System; public class BaseClass<S> where S : class { } public class Derived1 : BaseClass<int> { } // CS0452 public class Derived2<S> : BaseClass<S> where S : struct { } // CS0452  
```  
  
## 請參閱  
 [類型參數的條件約束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)