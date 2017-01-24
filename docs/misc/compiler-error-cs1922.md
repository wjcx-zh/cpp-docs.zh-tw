---
title: "編譯器錯誤 CS1922 | Microsoft Docs"
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
  - "CS1922"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1922"
ms.assetid: a4098a25-6581-4966-b61d-318cd12f76d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1922
集合初始設定式需要其類型 'type' 實作 System.Collections.IEnumerable。  
  
 若要搭配使用集合初始設定式與類型，類型必須實作 `IEnumerable`。 如果您在想要使用物件初始設定式時不小心使用到集合初始設定式語法，則會發生這個錯誤。  
  
### 更正這個錯誤  
  
-   如果類型不代表集合，請使用物件初始設定式語法，而非集合初始設定式語法。  
  
-   如果類型代表集合，請先進行修改來實作 `IEnumerable`，才能使用集合初始設定式來初始化該類型的物件。  
  
-   如果類型代表集合，而且您無法存取原始碼，則只要初始化其項目即可，方法是使用這些項目的類別建構函式或其他初始化方法。  
  
## 範例  
 下列程式碼會產生 CS1922：  
  
```  
// cs1922.cs public class Test { public static void Main() { // Collection initializer. var tc = new TestClass  {1,"hello"} ; // CS1922 // Object initalizer. var tc2 = new TestClass { memberA = 1, memberB = "hello" }; // OK } } public class TestClass { public int memberA { get; set; } public string memberB { get; set; } }  
  
```  
  
## 請參閱  
 [物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)