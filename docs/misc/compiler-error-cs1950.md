---
title: "編譯器錯誤 CS1950 | Microsoft Docs"
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
  - "CS1950"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1950"
ms.assetid: e37fb5b1-09e0-47a6-9db5-a48f90ea7bbb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1950
集合初始設定式的最佳多載 Add 方法 'name' 有一些無效的引數。  
  
 若要支援集合初始設定式，類別必須實作 IEnumerable，並且具有公開的 `Add` 方法。 若要使用集合初始設定式來初始化類型，`Add` 方法的輸入參數必須與您嘗試加入的物件類型相容。  
  
### 更正這個錯誤  
  
-   請在集合初始設定式中使用相容的類型。  
  
-   修改集合類型中之 `Add` 方法的輸入參數及\/或可存取性。  
  
-   加入新的 `Add` 方法，且它的輸入參數符合您要傳遞的輸入參數。  
  
-   請讓您的集合類別成為泛型，以便它可以有接受您傳入之任何類型的 `Add` 方法。  
  
## 範例  
 下列範例會產生 CS1950：  
  
```  
// cs1950.cs using System.Collections; class TestClass : CollectionBase { public void Add(int c) { } } class Test { static void Main() { TestClass t = new TestClass { "hi" }; // CS1950 } }  
```  
  
## 請參閱  
 [物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)