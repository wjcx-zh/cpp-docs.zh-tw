---
title: "編譯器錯誤 CS0314 | Microsoft Docs"
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
  - "CS0314"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0314"
ms.assetid: 12f68f51-0568-4e80-b0fd-15899807477d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0314
'type1' 類型不能作為泛型類型或 'name' 方法中的類型參數 'name' 使用。 沒有從 'type1' 到 'type2' 的 Boxing 轉換或類型參數轉換。  
  
 泛型類型使用受限的類型參數時，新的類別也必須滿足這些相同的條件約束。  
  
### 更正這個錯誤  
  
1.  在下面的範例中，將 `where T : ClassConstraint` 加入類別 `B`。  
  
## 範例  
 下列程式碼會產生 CS0314：  
  
```  
// cs0314.cs // Compile with: /target:library public class ClassConstraint { } public class A<T> where T : ClassConstraint { } public class B<T> : A<T> //CS0314 { } // Try using this instead. public class C<T> : A<T> where T : ClassConstraint { }  
```  
  
## 請參閱  
 [類型參數的條件約束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)