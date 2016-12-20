---
title: "&#39;#Else&#39; 之前必須搭配相對應的 &#39;#If&#39; 或 &#39;#ElseIf&#39; | Microsoft Docs"
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
  - "vbc30028"
  - "bc30028"
helpviewer_keywords: 
  - "BC30028"
ms.assetid: c6ed34de-d6ed-4227-9880-538055aff20a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#Else&#39; 之前必須搭配相對應的 &#39;#If&#39; 或 &#39;#ElseIf&#39;
`#Else` 是條件式編譯指示詞。`#Else` 指示詞的前面沒有對應的 `#If` 或 `#ElseIf` 指示詞。  
  
 **錯誤 ID︰**BC30028  
  
### 更正這個錯誤  
  
1.  請檢查是否未使用介入條件式編譯區塊將前面的 `#If` 或 `#ElseIf` 與這個 `#Else` 隔開，或不正確地放置 `#End If`。  
  
2.  請檢查 `#Else` 之前是否有另一個 `#Else` 指示詞。 如果是，請移除 `#Else`，或將它變更為 `#ElseIf`。  
  
3.  如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。  
  
## 請參閱  
 [\#If...Then...\#Else Directives](../Topic/%23If...Then...%23Else%20Directives.md)