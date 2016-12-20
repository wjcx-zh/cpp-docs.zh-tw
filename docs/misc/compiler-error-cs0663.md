---
title: "編譯器錯誤 CS0663 | Microsoft Docs"
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
  - "CS0663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0663"
ms.assetid: 9f96c42b-dcc8-4a0f-8404-289fc88dba5e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0663
不可定義只有 ref 和 out 不同的多載方法。  
  
 不允許只有在參數上使用不同 [ref](../Topic/ref%20\(C%23%20Reference\).md) 和 [out](../Topic/out%20\(C%23%20Reference\).md) 的方法。  
  
 下列範例會產生 CS0663：  
  
```  
// CS0663.cs class TestClass { public static void Main() { } public void Test(ref int i) { } public void Test(out int i)   // CS0663 { } }  
```