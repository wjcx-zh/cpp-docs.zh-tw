---
title: "編譯器錯誤 CS0123 | Microsoft Docs"
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
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0123"
ms.assetid: 57be2c58-6d87-40af-9376-cd7f91023044
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0123
'method' 沒有任何多載符合委派 'delegate'  
  
 建立委派的嘗試失敗，因為未使用正確的特徵標記。 委派的執行個體必須使用和委派宣告一樣的特徵標記宣告。  
  
 您可以調整方法或委派特徵標記來解決這個錯誤。 如需詳細資訊，請參閱[委派](../Topic/Delegates%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0123。  
  
```  
// CS0123.cs delegate void D(); delegate void D2(int i); public class C { public static void f(int i) {} public static void Main() { D d = new D(f);   // CS0123 D2 d2 = new D2(f);   // OK } }  
```