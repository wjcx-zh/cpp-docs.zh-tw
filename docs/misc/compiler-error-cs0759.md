---
title: "編譯器錯誤 CS0759 | Microsoft Docs"
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
  - "CS0759"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0759"
ms.assetid: 96f0e178-adbf-4327-8934-ac282c428184
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0759
找不到用以實作部分方法 'method' 之宣告的定義宣告。  
  
 部分方法必須具備定義方法簽章 \(名稱、傳回類型和參數\) 的定義宣告。 實作或方法的主體是選擇性的。  
  
### 更正這個錯誤  
  
1.  針對部分類別或結構之其他部分中的部分方法提供定義宣告。  
  
## 範例  
 下列範例會產生 CS0759：  
  
```  
// cs0759.cs using System; public partial class C { partial void Part() // CS0759 { } public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)