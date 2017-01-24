---
title: "編譯器錯誤 CS0594 | Microsoft Docs"
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
  - "CS0594"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0594"
ms.assetid: a3d6bde1-db63-4c5c-a425-8c6a39e00999
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0594
浮點常數的值超出類型 'type' 的範圍  
  
 已將值指派給對這個資料類型的變數而言太大的浮點變數。 如需資料類型中所允許之值範圍的詳細資訊，請參閱[整數類型表](../Topic/Integral%20Types%20Table%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0594：  
  
```  
// CS0594.cs namespace MyNamespace { public class MyClass { public static void Main() { float f = 6.77777777777E400;   // CS0594, value too large } } }  
```