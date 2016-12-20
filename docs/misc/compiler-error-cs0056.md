---
title: "編譯器錯誤 CS0056 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0056"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0056"
ms.assetid: 8878b09c-5b7b-40e0-be0d-61ef5b36c151
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0056
不一致的存取範圍: 傳回類型 'type' 比運算子 'operator' 的存取範圍小  
  
 公用建構必須傳回可公開存取的物件。 如需詳細資訊，請參閱[存取修飾詞](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0056：  
  
```  
// CS0056.cs class MyClass // try the following line instead // public class MyClass { } public class A { public static implicit operator MyClass(A a)   // CS0056 { return new MyClass(); } public static void Main() { } }  
```