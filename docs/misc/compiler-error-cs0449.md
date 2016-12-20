---
title: "編譯器錯誤 CS0449 | Microsoft Docs"
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
  - "CS0449"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0449"
ms.assetid: 32c07a2c-4c48-4d07-b643-72422a6b9fac
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0449
class' 或 'struct' 條件約束必須在所有其他條件約束之前  
  
 泛型類型或方法之類型參數的條件約束必須以特定順序發生：`class` 或 `struct` 必須是第一個 \(如果存在\)，接著是任何介面條件約束，最後是任何建構函式條件約束。 這個錯誤是 `class` 或 `struct` 條件約束未第一個出現所造成。 若要解決這個錯誤，請重新排列條件約束子句。  
  
## 範例  
 下列範例會產生 CS0449。  
  
```  
// CS0449.cs // compile with: /target:library interface I {} public class C4 { public void F1<T>() where T : class, struct, I {}   // CS0449 public void F2<T>() where T : I, struct {}   // CS0449 public void F3<T>() where T : I, class {}   // CS0449 // OK public void F4<T>() where T : class {} public void F5<T>() where T : struct {} public void F6<T>() where T : I {} }  
```