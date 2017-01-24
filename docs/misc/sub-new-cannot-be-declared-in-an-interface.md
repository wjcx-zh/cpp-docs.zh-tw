---
title: "無法在介面中宣告 &#39;Sub New&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30363"
  - "vbc30363"
helpviewer_keywords: 
  - "BC30363"
ms.assetid: 371d9aa8-a935-48ce-ada2-0a69ba20e070
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法在介面中宣告 &#39;Sub New&#39;
您已嘗試在介面內宣告 `Sub New`。 因為它是建構函式，所以 `Sub New` 只能在建立類別時執行一次。 不能在相同類別或衍生類別的其他建構函式的第一行程式碼以外的任何地方明確呼叫它。  
  
 **錯誤 ID︰**BC30363  
  
### 更正這個錯誤  
  
-   請移除 `Sub New`，或將它移至您程式碼中的更適當位置。  
  
## 請參閱  
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)