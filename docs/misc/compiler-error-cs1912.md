---
title: "編譯器錯誤 CS1912 | Microsoft Docs"
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
  - "CS1912"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1912"
ms.assetid: 6205420e-01b9-4470-89f9-5924f1e49108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1912
成員 'name' 的初始設定重複。  
  
 物件初始設定式一次只能初始化一個成員。  
  
### 更正這個錯誤  
  
1.  移除物件初始設定式中的第二個成員初始化。  
  
## 範例  
 下列程式碼會產生 CS1912，因為 `memberA` 已重複初始化：  
  
```  
// cs1912.cs using System.Linq; public class TestClass { public int memberA { get; set; } public int memberB { get; set; } } public class Test { static void Main() { TestClass tc = new TestClass() { memberA = 5, memberA = 6, memberB = 2}; // CS1912 } }  
```  
  
## 請參閱  
 [物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)