---
title: "編譯器錯誤 CS1920 | Microsoft Docs"
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
  - "CS1920"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1920"
ms.assetid: efb4782f-a222-4fb5-9e79-8bd2d380520b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1920
項目初始設定式不可為空白。  
  
 集合初始設定式是由一連串的項目初始設定式所組成。 除非包含指派運算式，否則項目初始設定式不必括在大括弧中。 不過，如果您提供大括弧，它們不能是空的。 如果項目初始設定式是物件初始設定式，那麼只要初始設定式包含新的物件建立運算式，就可能是空的大括弧。  
  
### 更正這個錯誤  
  
-   請在括弧之間加入遺漏的運算式。  
  
-   如果運算式是要作為物件初始設定式，請在大括弧前面加入新的物件建立運算式。  
  
## 範例  
 下列範例會產生 CS1920：  
  
```  
// cs1920.cs using System.Collections.Generic; public class Test { public static int Main() { // Error. Empty initializer // for inner list. List<List<int>> collection = new List<List<int>>() { { } }; // CS1920 // OK. No initializer for inner list. List<List<int>> collection2 = new List<List<int>>() {  }; // OK. Inner list is initialized // to one List<int> with zero elements. List<List<int>> collection3 = new List<List<int>>() { new List<int> { } }; return 0; } }  
```  
  
## 請參閱  
 [物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)