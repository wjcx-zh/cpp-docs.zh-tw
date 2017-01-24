---
title: "編譯器錯誤 CS0133 | Microsoft Docs"
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
  - "CS0133"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0133"
ms.assetid: b5be456f-824d-4e6d-802b-0b1b5889efbd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0133
指派給 'variable' 的運算式必須為常數  
  
 [const](../Topic/const%20\(C%23%20Reference\).md) 變數無法接受非常數運算式作為其值。 如需詳細資訊，請參閱[常數](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0133：  
  
```  
// CS0133.cs public class MyClass { public const int i = c;   // CS0133, c is not constant public static int c = i; // try the following line instead // public const int i = 6; public static void Main() { } }  
```