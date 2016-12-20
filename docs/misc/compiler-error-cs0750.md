---
title: "編譯器錯誤 CS0750 | Microsoft Docs"
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
  - "CS0750"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0750"
ms.assetid: 84fb6841-7f47-405a-ae05-95567692f73d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0750
部分方法不可有存取修飾詞或 virtual、abstract、override、new、sealed 或 extern 修飾詞。  
  
 由於其特殊行為，部分方法可以接受的修飾詞有限。  
  
### 更正這個錯誤  
  
1.  從方法宣告中移除未授權的修飾詞。  
  
## 範例  
 下列範例會產生 CS0750：  
  
```  
// cs0750.cs using System; public class Base { protected virtual void PartG() { } protected void PartH() { } protected virtual void PartI() { } } public partial class C:Base { // All these partial method declarations // will generate CS0750. public partial void PartA(); private partial void PartB(); protected partial void PartC(); internal partial void PartD(); virtual partial void PartE(); abstract partial void PartF(); override partial void PartG(); new partial void PartH(); sealed override partial void PartI(); extern partial void PartJ(); public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)