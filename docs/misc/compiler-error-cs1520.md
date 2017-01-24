---
title: "編譯器錯誤 CS1520 | Microsoft Docs"
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
  - "CS1520"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1520"
ms.assetid: 1aeeee83-52a6-45dc-b197-a9a6de3a220c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1520
方法必須要有傳回類型  
  
 在類別、結構或介面中宣告的方法必須有明確的傳回類型。 在下列範例中，Square 方法具有[字串](../Topic/string%20\(C%23%20Reference\).md)的傳回值：  
  
```  
class Test { string IntToString(int i) { return i.ToString(); } }  
```  
  
 下列範例會產生 CS1520：  
  
```  
// CS1520a.cs public class x { // Method declaration missing a return type MyMethod()   // CS1520 {} // Add the desired return type: // void MyMethod2() // { } public static void Main() { } }  
```  
  
 或者，當建構函式名稱的大小寫與類別或結構宣告的大小寫不同時，可能會發生此錯誤，如下列範例所示。 因為名稱不完全與類別名稱相同，編譯器會將它解譯為一般方法，而不是建構函式，因此產生錯誤：  
  
```  
// CS1520b.cs public class Class1 { // Should be Class1, not class1 public class1()   // CS1520 { } static void Main() { } }  
```  
  
## 請參閱  
 [方法](../Topic/Methods%20\(C%23%20Programming%20Guide\).md)   
 [建構函式](../Topic/Constructors%20\(C%23%20Programming%20Guide\).md)