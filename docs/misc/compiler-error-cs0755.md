---
title: "編譯器錯誤 CS0755 | Microsoft Docs"
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
  - "CS0755"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0755"
ms.assetid: 80613029-a009-4bdf-b1c2-1eec1e60c7b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0755
兩個部分方法宣告必須都是擴充方法，或者都不是擴充方法。  
  
 部分方法是由定義宣告 \(特徵標記\) 和選擇性的實作宣告 \(主體\) 所組成。 如果定義宣告是擴充方法，則實作宣告，如果有定義，也必須是擴充方法。 如果定義方法不是擴充方法，實作也不得是擴充方法。  
  
### 更正這個錯誤  
  
1.  請從其中一個組件移除 `this` 修飾詞，或將它加入另一者。  
  
## 範例  
 下列範例會產生 CS0755：  
  
```  
// cs0755.cs public static partial class Ext { static partial void Part(this C c); //Extension method // Typically the implementing declaration is in a separate file. static partial void Part(C c) //CS0755 { } } public partial class C { public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)