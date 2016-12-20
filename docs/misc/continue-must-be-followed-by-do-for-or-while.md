---
title: "&#39;Continue&#39; 必須在 &#39;Do&#39;、&#39;For&#39; 或 &#39;While&#39; 之前 | Microsoft Docs"
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
  - "bc30781"
  - "vbc30781"
helpviewer_keywords: 
  - "BC30781"
ms.assetid: a0d5854d-ca44-4c6b-9458-4fc50d29281a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue&#39; 必須在 &#39;Do&#39;、&#39;For&#39; 或 &#39;While&#39; 之前
根據 `Continue` 陳述式出現在 `Do...Loop` 迴圈、`For...Next` 迴圈還是 `While...End While` 迴圈內，`Continue` 陳述式的結尾必須是 `Do``For` 或 `While`。  
  
 **錯誤 ID︰**BC30781  
  
### 更正這個錯誤  
  
1.  如果 `Continue` 陳述式是在 `Do...Loop` 迴圈內，請將陳述式變更為 `Continue Do`。  
  
2.  如果 `Continue` 陳述式是在 `For...Next` 迴圈內，請將陳述式變更為 `Continue For`。  
  
3.  如果 `Continue` 陳述式是在 `While...End While` 迴圈內，請將陳述式變更為 `Continue While`。  
  
4.  否則，請移除 `Continue` 陳述式。  
  
## 請參閱  
 [Continue Statement](../Topic/Continue%20Statement%20\(Visual%20Basic\).md)