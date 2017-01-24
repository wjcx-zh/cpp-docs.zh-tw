---
title: "編譯器錯誤 CS0263 | Microsoft Docs"
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
  - "CS0263"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0263"
ms.assetid: 94fe3eb0-10e9-4602-a993-68fe125c8565
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0263
'type' 的部分宣告不可指定不同的基底類別  
  
 在部分宣告中定義類型時，請在每個部分宣告中指定相同的基底類型。 如需詳細資訊，請參閱[部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0263：  
  
```  
  
// CS0263.cs // compile with: /target:library class B1 { } class B2 { } partial class C : B1  // CS0263 – is the base class B1 or B2? { } partial class C : B2 { }  
```