---
title: "編譯器錯誤 CS0416 | Microsoft Docs"
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
  - "CS0416"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0416"
ms.assetid: 61bfe40d-5e87-47e5-933f-3491e28ace42
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0416
'類型參數': 屬性引數不可使用類型參數  
  
 使用了類型參數作為屬性引數，這是不允許的做法。 請使用非泛型類型。  
  
 下列範例會產生 CS0416：  
  
```  
// CS0416.cs public class MyAttribute : System.Attribute { public MyAttribute(System.Type t) { } } class G<T> { [MyAttribute(typeof(G<T>))]  // CS0416 public void F() { } }  
```