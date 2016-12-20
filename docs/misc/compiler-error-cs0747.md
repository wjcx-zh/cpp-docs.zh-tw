---
title: "編譯器錯誤 CS0747 | Microsoft Docs"
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
  - "CS0747"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0747"
ms.assetid: dc1b7e38-cee5-406c-b193-a60ec4faebe1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0747
初始設定式成員宣告子無效。  
  
 物件初始設定式用來將值指派給屬性或欄位。 任何不是屬性或欄位指派的運算式都是編譯時期錯誤。  
  
### 更正這個錯誤  
  
1.  確定初始設定式中的所有運算式都是該類型的屬性或欄位指派。 在下列範例中，第二個運算式是錯誤，因為值 `1` 未指派給 `List<int>` 的任何屬性或欄位。  
  
## 範例  
 下列程式碼會產生 CS0747：  
  
```  
// cs0747.cs using System.Collections.Generic; public class C { public static int Main() { var t = new List<int> { Capacity = 2, 1 }; // CS0747 return 1; } }  
```  
  
## 請參閱  
 [物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)