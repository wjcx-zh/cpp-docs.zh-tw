---
title: "編譯器錯誤 CS0752 | Microsoft Docs"
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
  - "CS0752"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0752"
ms.assetid: f9a373d6-31ed-42db-8206-80cbe9b8c546
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0752
部分方法不可有 out 參數  
  
 部分方法不可有 [out](../Topic/out%20\(C%23%20Reference\).md) 參數。 不允許 out 參數，因為如果部分方法遭到編譯器移除，則無法保證曾經指派 out 參數。  
  
### 更正這個錯誤  
  
1.  從參數中移除 out 修飾詞並改用方法的傳回值，或者從方法宣告中移除部分修飾詞。  
  
## 範例  
 下列程式碼會產生 CS0752：  
  
```  
// cs0752.cs public partial class C { partial void Part(out int num); // CS0752 // try the following line instead // partial void Part(int num); public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)