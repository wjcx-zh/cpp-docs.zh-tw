---
title: "&#39;AddHandler&#39; 和 &#39;RemoveHandler&#39; 方法必須剛好有一個參數 | Microsoft Docs"
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
  - "vbc31133"
  - "bc31133"
helpviewer_keywords: 
  - "BC31133"
ms.assetid: f6295626-dd63-408c-ab5f-76367f94d6ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39; 和 &#39;RemoveHandler&#39; 方法必須剛好有一個參數
自訂事件宣告必須有 `AddHandler` 或 `RemoveHandler` 宣告，每個宣告會接受自訂事件的 `As` 子句所指定之委派類型的單一參數。  
  
 **錯誤 ID︰**BC31133  
  
### 更正這個錯誤  
  
-   從參數清單中移除額外的參數，並將參數類型變更為與自訂事件的 `As` 子句所指定之委派類型相同的類型。  
  
## 範例  
 這個範例示範具有 `AddHandler` 和 `RemoveHandler` 宣告之正確參數類型的自訂事件。  
  
 [!CODE [VbVbalrEventError#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#1)]  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)