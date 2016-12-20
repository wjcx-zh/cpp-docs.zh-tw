---
title: "編譯器錯誤 CS0453 | Microsoft Docs"
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
  - "CS0453"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0453"
ms.assetid: a1bbd09e-6313-4bfd-84bf-bc15a8d214a6
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0453
類型 'Type Name' 必須是不可為 Null 的實值類型，才能在泛型類型或方法 'Generic Identifier' 中作為參數 'Parameter Name' 使用  
  
 如果具現化具有 **value** 條件約束的泛型類型或方法時使用非實值類型引數，則會發生這個錯誤。 它也可能發生於使用可為 Null 的實值類型引數時。 請參閱下列範例中的最後兩行程式碼。  
  
## 範例  
 下列程式碼會產生這個錯誤。  
  
```  
// CS0453.cs using System; public class HV<S> where S : struct { } public class H1 : HV<string> { }                   // CS0453 public class H2 : HV<H1> { }                       // CS0453 public class H3<S> : HV<S> where S : class { }     // CS0453 public class H4 : HV<int?> { }                     // CS0453 public class H5 : HV<Nullable<Nullable<int>>> { }  // CS0453  
```