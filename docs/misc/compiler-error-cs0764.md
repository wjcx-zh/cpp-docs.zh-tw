---
title: "編譯器錯誤 CS0764 | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0764
兩個部分方法宣告必須都是 unsafe，或者都不是 unsafe  
  
 部分方法是由定義宣告 \(特徵標記\) 和選擇性的實作宣告 \(主體\) 所組成。 如果定義宣告有 `unsafe` 修飾詞，實作宣告就必須也有。 反之，如果實作宣告有 `unsafe` 修飾詞，定義宣告也必須有。  
  
### 更正這個錯誤  
  
1.  假設定義宣告是正確的，請從實作宣告新增或移除 `unsafe` 修飾詞使符合定義宣告。  
  
## 範例  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)