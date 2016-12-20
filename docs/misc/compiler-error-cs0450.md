---
title: "編譯器錯誤 CS0450 | Microsoft Docs"
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
  - "CS0450"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0450"
ms.assetid: 8eb0e98b-d7a1-49a7-8e55-36e2eb0057ff
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0450
'類型參數名稱': 不能指定了條件約束類別，又同時指定 'class' 或 'struct' 條件約束  
  
 如果類型參數受到結構類型條件約束的限制，又同時受到特定類別類型的限制，由於結構和類別是互斥的分類，因此這會在邏輯上產生衝突。 如果類型參數受到特定類別類型條件約束的限制，則依定義它會受到類別類型條件約束的限制，因此指定類別類型條件約束是多餘的。  
  
## 範例  
  
```  
// CS0450.cs // compile with: /t:library public class GenericsErrors { public class B { } public class G3<T> where T : struct, B { } // CS0450 // To resolve, use the following line instead: // public class G3<T> where T : B { } }  
```