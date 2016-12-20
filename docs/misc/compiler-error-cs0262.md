---
title: "編譯器錯誤 CS0262 | Microsoft Docs"
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
  - "CS0262"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0262"
ms.assetid: 44f8661f-c934-483f-84cd-00ca8257e50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0262
'type' 的部分宣告有衝突的存取範圍修飾詞  
  
 如果部分類型具有不一致的修飾詞 \(例如 public、private、protected、internal 或 abstract\)，則會發生這個錯誤。 在該類型的所有部分宣告中，這些修飾詞必須一致。 如需詳細資訊，請參閱[部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0262：  
  
```  
// CS0262.cs class A { public partial class C  // CS0262 { } private partial class C { } }  
```