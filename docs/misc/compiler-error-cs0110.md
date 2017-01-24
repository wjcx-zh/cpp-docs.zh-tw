---
title: "編譯器錯誤 CS0110 | Microsoft Docs"
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
  - "CS0110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0110"
ms.assetid: 0bfe7071-1194-4142-a1a1-6190ee92b1d4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0110
'const declaration' 常數值的評估牽涉循環定義  
  
 [const](../Topic/const%20\(C%23%20Reference\).md) 變數 \(`a`\) 的宣告不能參考也參考 \(`a`\) 的另一個 const 變數 \(`b`\)。  
  
 下列範例會產生 CS0110：  
  
```  
// CS0110.cs namespace MyNamespace { public class A { public static void Main() { } } public class B : A { public const int i = c + 1;   // CS0110, c already references i public const int c = i + 1; // the following line would be OK // public const int c = 10; } }  
```  
  
## 請參閱  
 [常數](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)