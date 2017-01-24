---
title: "&#39;&lt;關鍵字&gt;&#39; 在結構中無效 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30044"
  - "vbc30044"
helpviewer_keywords: 
  - "BC30044"
ms.assetid: 252510cf-e084-47e4-9592-4aa8f94fabe4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;關鍵字&gt;&#39; 在結構中無效
結構是實值類型，而不是參考類型。 結構不是從類別建立的執行個體，因此 `Me`、`MyClass` 和 `MyBase` 關鍵字在結構中沒有意義。  
  
 **錯誤 ID︰**BC30044  
  
### 更正這個錯誤  
  
-   請將結構變更為類別，或從程序中移除關鍵字。  
  
## 請參閱  
 [我](http://msdn.microsoft.com/zh-tw/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass \- delete](http://msdn.microsoft.com/zh-tw/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [MyBase \- delete](http://msdn.microsoft.com/zh-tw/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)