---
title: "委派無法處理事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30019"
  - "vbc30019"
helpviewer_keywords: 
  - "BC30019"
ms.assetid: 7f0c7bb9-8e81-44bf-acc5-80d9785708aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 委派無法處理事件
委派是一種參考類型，指向共用程序或指向物件上的執行個體。 因為透過指派可以變更它所指向的程序，所以 `Delegate` 陳述式不支援 `Handles` 或 `Implements` 子句。  
  
 **錯誤 ID︰**BC30019  
  
### 更正這個錯誤  
  
-   請從 `Delegate` 陳述式中移除 `Handles` 子句。  
  
## 請參閱  
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)