---
title: "編譯器錯誤 CS0081 | Microsoft Docs"
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
  - "CS0081"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0081"
ms.assetid: a5649abc-89ea-4f64-8c3c-eb36df926561
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0081
類型參數宣告必須是識別項，而非類型。  
  
 當您宣告泛型方法或類型時，請指定類型參數作為識別項 \(例如 "T" 或 "inputType"\)。 用戶端程式碼呼叫方法時，會提供類型，以取代方法或類別主體中的所有識別項。 如需詳細資訊，請參閱[泛型類型參數](../Topic/Generic%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
```  
// CS0081.cs class MyClass { public void F<int>() {}   // CS0081 public void F<T>(T input) {}   // OK public static void Main() { MyClass a = new MyClass(); a.F<int>(2); a.F<double>(.05); } }  
```  
  
## 請參閱  
 [泛型](../Topic/Generics%20\(C%23%20Programming%20Guide\).md)