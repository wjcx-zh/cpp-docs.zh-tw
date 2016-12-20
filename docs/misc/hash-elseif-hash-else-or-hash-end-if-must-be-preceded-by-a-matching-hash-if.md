---
title: "&#39;#ElseIf&#39;、&#39;#Else&#39; 或 &#39;#End If&#39; 之前必須搭配相對應的 &#39;#If&#39; | Microsoft Docs"
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
  - "vbc30013"
  - "bc30013"
helpviewer_keywords: 
  - "BC30013"
ms.assetid: 8fe2d23c-8b8f-46d8-90f2-7f8857ea43bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39;、&#39;#Else&#39; 或 &#39;#End If&#39; 之前必須搭配相對應的 &#39;#If&#39;
`#ElseIf`、`#Else` 和 `#End If` 都是條件式編譯指示詞。`#ElseIf`、`#Else` 或 `#End If` 的前面沒有對應的 `#If` 指示詞。  
  
 **錯誤 ID︰**BC30013  
  
### 更正這個錯誤  
  
1.  檢查是否未使用介入條件式編譯區塊將預期的 `#If` 與問題中的子句隔開，或不正確地放置 `#End If`。  
  
    > [!NOTE]
    >  每個 `#If` 區塊中只能有一個 `#Else`，因此兩個連續的 `#Else` 指示詞會造成這個錯誤。  
  
2.  檢查舊版 `#If` 指示詞中未遺漏前置 `#`。  
  
3.  如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。  
  
## 請參閱  
 [\#If...Then...\#Else Directives](../Topic/%23If...Then...%23Else%20Directives.md)