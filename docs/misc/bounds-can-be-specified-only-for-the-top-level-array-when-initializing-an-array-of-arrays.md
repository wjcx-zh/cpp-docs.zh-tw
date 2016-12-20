---
title: "在初始化陣列的陣列時，只可以指定最上層陣列的界限 | Microsoft Docs"
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
  - "bc32014"
  - "vbc32014"
helpviewer_keywords: 
  - "BC32014"
ms.assetid: d8d7155d-82d1-4a25-b9bb-1883e1586383
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在初始化陣列的陣列時，只可以指定最上層陣列的界限
不規則陣列 \(陣列的陣列\) 的陣列初始化會設定其中一個較低層級的初始長度。 您只能在陣列宣告陳述式中指定最上層陣列的長度。  
  
 **錯誤 ID︰**BC32014  
  
### 更正這個錯誤  
  
1.  請移除最上層陣列以外的所有長度指定。  
  
2.  請在後續的指派陳述式中使用 `New` 關鍵字設定較低層級陣列的初始長度。  
  
## 請參閱  
 [NOTINBUILD 陣列變數](http://msdn.microsoft.com/zh-tw/c2da78bd-6928-46ba-805f-44f819dfaf93)   
 [NOTINBUILD Visual Basic 中的不規則陣列](http://msdn.microsoft.com/zh-tw/05c12439-ee8f-4fef-ba75-b35402b67ab9)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)