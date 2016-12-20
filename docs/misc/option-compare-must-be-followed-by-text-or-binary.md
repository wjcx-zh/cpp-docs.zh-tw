---
title: "&#39;Option Compare&#39; 必須在 &#39;Text&#39; 或 &#39;Binary&#39; 之前 | Microsoft Docs"
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
  - "vbc30207"
  - "bc30207"
helpviewer_keywords: 
  - "BC30207"
ms.assetid: e59cf10d-47ce-401d-8474-3b69a3a5f5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Option Compare&#39; 必須在 &#39;Text&#39; 或 &#39;Binary&#39; 之前
`Option Compare` 陳述式包含不正確的設定或沒有設定。`Option Compare` 中唯一允許的設定是 `Text` 和 `Binary`。  
  
 **錯誤 ID︰**BC30207  
  
### 更正這個錯誤  
  
1.  請檢查設定規範的拼字是否錯誤。  
  
2.  請將 `Text` 或 `Binary` 關鍵字加入 `Option Compare` 陳述式中，例如 `Option Compare Text`。  
  
## 請參閱  
 [Option Compare Statement](../Topic/Option%20Compare%20Statement.md)