---
title: "結構中宣告的方法不能有 &#39;Handles&#39; 子句 | Microsoft Docs"
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
  - "vbc30728"
  - "bc30728"
helpviewer_keywords: 
  - "BC30728"
ms.assetid: 64c70bb5-3696-4865-8194-328394c2b4b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 結構中宣告的方法不能有 &#39;Handles&#39; 子句
結構方法不能使用 `Handles` 關鍵字來處理事件。  
  
 **錯誤 ID：**BC30728  
  
### 更正這個錯誤  
  
-   考慮將您的結構重新設計為類別。  
  
     您可以使用 `AddHandler`，將結構中的事件與事件處理常式產生關聯，條件是該結構需實作介面中定義的事件處理常式。  
  
## 請參閱  
 [Structures and Classes](../Topic/Structures%20and%20Classes%20\(Visual%20Basic\).md)   
 [不在組建中：類別：物件的藍圖](http://msdn.microsoft.com/zh-tw/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)   
 [不在組建中：AddHandler 和 RemoveHandler](http://msdn.microsoft.com/zh-tw/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)