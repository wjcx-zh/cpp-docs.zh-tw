---
title: "編譯器錯誤 CS0451 | Microsoft Docs"
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
  - "CS0451"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0451"
ms.assetid: e73544f8-856b-4a92-90e0-dd6cb9d688b1
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0451
new\(\)' 條件約束不能和 'struct' 條件約束一起使用  
  
 指定泛型類型的條件約束時，`new()` 條件約束只能與類別類型條件約束、介面類型條件約束、參考類型條件約束和類型參數條件約束一起使用，而不是與實值類型條件約束一起使用。  
  
## 範例  
 下列範例會產生 CS0451：  
  
```  
// CS0451.cs using System; public class C4 { public void F4<T>() where T : struct, new() {}   // CS0451 } // OK public class C5 { public void F5<T>() where T : struct {} } public class C6 { public void F6<T>() where T : new() {} }  
  
```