---
title: "&#39;#ElseIf&#39; 不可以跟隨在 &#39;#Else&#39; 之後作為 &#39;#If&#39; 區塊的一部分 | Microsoft Docs"
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
  - "bc32030"
  - "vbc32030"
helpviewer_keywords: 
  - "BC32030"
ms.assetid: 248d6464-3019-4753-8a33-7070bbe5d2a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39; 不可以跟隨在 &#39;#Else&#39; 之後作為 &#39;#If&#39; 區塊的一部分
`#ElseIf` 條件式編譯指示詞是在 `#Else` 指示詞後面。`#Else` 必須是條件式區塊中 `#End If` 指示詞前面的最後一個指示詞。  
  
 **錯誤 ID︰**BC32030  
  
### 更正這個錯誤  
  
1.  請確認前一個 `#Else` 應該是 `#ElseIf`。  
  
2.  請確認已正常終止前一個 `#If` 區塊，並初始新的 `#If` 區塊。  
  
3.  如果所有項目都正確，請移動這個 `#ElseIf` 指示詞和其相對應的陳述式區塊，以將其放在 `#Else` 區塊前面。  
  
## 請參閱  
 [\#If...Then...\#Else Directives](../Topic/%23If...Then...%23Else%20Directives.md)