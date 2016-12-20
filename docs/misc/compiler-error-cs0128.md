---
title: "編譯器錯誤 CS0128 | Microsoft Docs"
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
  - "CS0128"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0128"
ms.assetid: 35db9025-2bed-437f-a78a-f2862766bde2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0128
已經在此範圍定義名為 'variable' 的區域變數  
  
 編譯器偵測到兩個同名區域變數的宣告。 如需詳細資訊，請參閱[方法](../Topic/Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0128：  
  
```  
// CS0128.cs namespace MyNamespace { public class MyClass { public static void Main() { char i; int i;   // CS0128 } } }  
```