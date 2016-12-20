---
title: "編譯器錯誤 CS0818 | Microsoft Docs"
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
  - "CS0818"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0818"
ms.assetid: e4941018-a10a-4636-98ea-aade29e45728
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0818
隱含類型區域變數必須初始化  
  
 宣告的同時，隱含類型的區域變數必須以一個值初始化。  
  
### 更正這個錯誤  
  
1.  請將值指派給變數，或是指定明確的類型。  
  
## 範例  
 下列程式碼會產生 CS0818：  
  
```  
// cs0818.cs class A { public static int Main() { var a; // CS0818 return -1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)