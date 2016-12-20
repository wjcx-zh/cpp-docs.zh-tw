---
title: "實作介面成員的方法或事件不可以宣告為 &#39;Shared&#39; | Microsoft Docs"
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
  - "bc30505"
  - "vbc30505"
helpviewer_keywords: 
  - "BC30505"
ms.assetid: a24937c5-aeac-47de-a08b-d8696dd8221a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 實作介面成員的方法或事件不可以宣告為 &#39;Shared&#39;
您已嘗試將實作介面成員的方法或事件宣告為 `Shared`。 類別中所實作的方法和事件不能指定為 `Shared` 或 `Private` \(在不可繼承的類別中除外\)。  
  
 **錯誤 ID︰**BC30505  
  
### 更正這個錯誤  
  
-   請移除 `Shared` 關鍵字。  
  
## 請參閱  
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)