---
title: "編譯器錯誤 CS0456 | Microsoft Docs"
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
  - "CS0456"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0456"
ms.assetid: d714ec06-a7f4-405e-bf32-423696848319
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0456
類型參數 '類型參數名稱 1' 具有 'struct' 條件約束，因此 '類型參數名稱 1' 不能作為 '類型參數名稱 2' 的條件約束  
  
 實值類型條件約束隱含地密封，因此這些條件約束不能作為第二個類型參數的條件約束。 這是因為不能覆寫實值類型。 若要解決這個錯誤，請將實值類型條件約束直接放在第二個類型參數，而不要間接透過第一個類型參數進行。  
  
## 範例  
 下列範例會產生 CS0456。  
  
```  
// CS0456.cs // compile with: /target:library public class GenericsErrors { public class G5<T> where T : struct { public class N<U> where U : T {}   // CS0456 public class N2<U> where U : struct {}   // OK } }  
```