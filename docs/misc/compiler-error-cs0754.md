---
title: "編譯器錯誤 CS0754 | Microsoft Docs"
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
  - "CS0754"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0754"
ms.assetid: c83e04b5-6ab5-45c2-805e-0ba4f041d506
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0754
部分方法不可明確地實作介面方法。  
  
 部分方法不可以宣告為介面中所定義方法的明確實作。  
  
### 更正這個錯誤  
  
1.  請從方法宣告中移除明確介面限定性條件。  
  
## 範例  
 下列程式碼會產生 CS0754：  
  
```  
// cs0754.cs using System; public interface IF { void Part(); } public partial class C : IF { partial void IF.Part(); //CS0754 public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [明確介面實作](../Topic/Explicit%20Interface%20Implementation%20\(C%23%20Programming%20Guide\).md)   
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)