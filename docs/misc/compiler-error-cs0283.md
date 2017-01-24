---
title: "編譯器錯誤 CS0283 | Microsoft Docs"
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
  - "CS0283"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0283"
ms.assetid: f94a5b84-92c5-4602-894d-6f856d57e0e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0283
類型 'type' 不能宣告為 const  
  
 在常數宣告中指定的類型必須是 `byte`、`char`、`short`、`int`、`long`、`float`、`double`、`decimal`、`bool`、`string`、列舉類型，或指派值為 Null 的參考類型。 每個常數運算式必須產生目標類型的值，或可以隱含轉換方式轉換成目標類型之類型的值。  
  
## 範例  
 下列範例會產生 CS0283。  
  
```  
// CS0283.cs struct MyTest { } class MyClass { // To resolve the error but retain the "const-ness", // change const to readonly. const MyTest test = new MyTest();   // CS0283 public static int Main() { return 1; } }  
```