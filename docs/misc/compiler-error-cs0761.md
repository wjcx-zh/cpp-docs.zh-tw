---
title: "編譯器錯誤 CS0761 | Microsoft Docs"
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
  - "CS0761"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0761"
ms.assetid: b16ac1df-0ddc-44d2-89f1-8d9c32af87ad
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0761
'method\<T\>' 的部分方法宣告有不一致的類型參數條件約束。  
  
 如果部分方法具有實作，泛型類型條件約束必須與方法簽章上所定義的條件約束完全相同。  
  
### 更正這個錯誤  
  
1.  使部分方法之每部分的泛型類型條件約束皆相同。  
  
## 範例  
 下列程式碼會產生 CS0761：  
  
```  
// cs0761.cs using System; public partial class C { partial void Part<T>() where T : class; partial void Part<T>() where T : struct // CS0761 { } public static int Main() { return 1; } }  
  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [類型參數的條件約束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)