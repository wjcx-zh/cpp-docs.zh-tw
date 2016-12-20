---
title: "Try 至少必須有一個 &#39;Catch&#39; 或 &#39;Finally&#39; | Microsoft Docs"
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
  - "bc30030"
  - "vbc30030"
helpviewer_keywords: 
  - "BC30030"
ms.assetid: d6eadd58-3788-42ae-8cc0-59aba86c7c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Try 至少必須有一個 &#39;Catch&#39; 或 &#39;Finally&#39;
`Try` 區塊必須在 `End Try` 陳述式之前包含 `Finally` 區塊，或至少一個 `Catch` 區塊。  
  
 **錯誤 ID︰**BC30030  
  
### 更正這個錯誤  
  
-   請在 `Try` 區塊內加入 `Catch` 或 `Finally` 區塊。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)