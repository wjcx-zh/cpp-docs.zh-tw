---
title: "編譯器錯誤 CS0182 | Microsoft Docs"
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
  - "CS0182"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0182"
ms.assetid: a9e97bb8-f06e-499f-aadf-26abc2082f98
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0182
屬性引數必須是常數運算式、typeof 運算式或屬性參數類型的陣列建立運算式  
  
 某些限制適用於哪些類型的引數可以與屬性搭配使用。 請注意，除了錯誤訊息中所指定的限制之外，下列類型不能作為屬性引數：  
  
-   [sbyte](../Topic/sbyte%20\(C%23%20Reference\).md)  
  
-   [ushort](../Topic/ushort%20\(C%23%20Reference\).md)  
  
-   [uint](../Topic/uint%20\(C%23%20Reference\).md)  
  
-   [ulong](../Topic/ulong%20\(C%23%20Reference\).md)  
  
-   [decimal](../Topic/decimal%20\(C%23%20Reference\).md)  
  
 如需詳細資訊，請參閱[不在組建中：全域屬性 \(C\# 程式設計手冊\)](http://msdn.microsoft.com/zh-tw/7c6c41f8-f0d5-4345-8987-3d91f9bae136)。  
  
## 範例  
 下列範例會產生 CS0182：  
  
```  
// CS0182.cs public class MyClass { static string s = "Test"; [System.Diagnostics.ConditionalAttribute(s)]   // CS0182 // try the following line instead // [System.Diagnostics.ConditionalAttribute("Test")] void NonConstantArgumentToConditional() { } public static void Main() { } }  
```