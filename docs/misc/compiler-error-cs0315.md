---
title: "編譯器錯誤 CS0315 | Microsoft Docs"
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
  - "CS0315"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0315"
ms.assetid: 9bb1cab3-1dca-4467-978b-1ab310901a70
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0315
'valueType' 類型不能作為泛型類型或 'TypeorMethod\<T\>' 方法中的類型參數 'T' 使用 沒有從 'valueType' 到 'referenceType' 的 Boxing 轉換。  
  
 如果您將泛型類型限制為特定類別，並嘗試使用無法對其進行隱含 Box 處理的實值類型來建構該類別的執行個體，則會發生這個錯誤。  
  
### 更正這個錯誤  
  
1.  其中一個解決方案是將結構重新定義為類別。  
  
## 範例  
 下列範例會產生 CS0315：  
  
```  
// cs0315.cs public class ClassConstraint { } public struct ViolateClassConstraint { } public class Gen<T> where T : ClassConstraint { } public class Test { public static int Main() { Gen<ViolateClassConstraint> g = new Gen<ViolateClassConstraint>(); //CS0315 return 1; } }  
```  
  
## 請參閱  
 [類型參數的條件約束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)   
 [Boxing 和 Unboxing](../Topic/Boxing%20and%20Unboxing%20\(C%23%20Programming%20Guide\).md)