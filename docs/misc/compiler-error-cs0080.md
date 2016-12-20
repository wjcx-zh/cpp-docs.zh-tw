---
title: "編譯器錯誤 CS0080 | Microsoft Docs"
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
  - "CS0080"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0080"
ms.assetid: 99035371-37d1-48b2-a8b9-e8a1ebd04f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0080
非泛型宣告中不可使用條件約束  
  
 找到的語法只能用於泛型宣告中，以將條件約束套用至類型參數。 如需詳細資訊，請參閱[泛型](../Topic/Generics%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0080，因為 MyClass 不是泛型類別，而且 Foo 不是泛型方法。  
  
```  
namespace MyNamespace { public class MyClass where MyClass : System.IDisposable // CS0080    //the following line shows an example of correct syntax //public class MyClass<T> where T : System.IDisposable { public void Foo() where Foo : new() // CS0080 //the following line shows an example of correct syntax //public void Foo<U>() where U : struct { } } public class Program { public static void Main() { } } }  
```