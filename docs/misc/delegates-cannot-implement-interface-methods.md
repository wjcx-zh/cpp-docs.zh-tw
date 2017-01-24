---
title: "委派 (Delegate) 無法實作介面方法 | Microsoft Docs"
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
  - "bc30018"
  - "vbc30018"
helpviewer_keywords: 
  - "BC30018"
ms.assetid: 71851072-c0c7-4131-aaf7-f3e9e6a2a448
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 委派 (Delegate) 無法實作介面方法
委派是一種參考類型，指向共用程序或指向物件上的執行個體。 因為透過指派可以變更它所指向的程序，所以 `Delegate` 陳述式不支援 `Handles` 或 `Implements` 子句。  
  
 **錯誤 ID︰**BC30018  
  
### 更正這個錯誤  
  
-   請從 `Delegate` 陳述式中移除 `Implements` 子句。  
  
## 請參閱  
 [不在組建中：Delegates 和 AddressOf 運算子](http://msdn.microsoft.com/zh-tw/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)