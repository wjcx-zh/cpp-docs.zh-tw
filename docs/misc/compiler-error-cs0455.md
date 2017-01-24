---
title: "編譯器錯誤 CS0455 | Microsoft Docs"
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
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0455
類型參數 'Type Parameter Name' 繼承了衝突的條件約束 'Constraint Name 1' 和 'Constraint Name 2'  
  
 發生這個錯誤的兩個常用方式是設定條件約束，讓類型參數衍生自兩個不相關類別，或讓它衍生自類別類型或參考類型條件約束以及 `struct` 類型或實值類型條件約束。 若要解決這個錯誤，請移除繼承階層中的衝突。  
  
## 範例  
 下列程式碼會產生錯誤 CS0455。  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```