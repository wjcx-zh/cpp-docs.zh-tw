---
title: "&#39;Finally&#39; 之後必須搭配相對應的 &#39;End Try&#39; | Microsoft Docs"
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
  - "vbc30442"
  - "bc30442"
helpviewer_keywords: 
  - "BC30442"
ms.assetid: 36cce657-186c-4ba0-a760-abcef9529f18
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; 之後必須搭配相對應的 &#39;End Try&#39;
`Finally` 陳述式出現在您的程式碼中，但沒有對應的 `End Try`陳述式。`Finally` 陳述式必須以 `End Try` 陳述式為結尾。  
  
 **錯誤 ID︰**BC30442  
  
### 更正這個錯誤  
  
1.  請移除 `Finally` 陳述式。  
  
2.  加入 `End Try` 陳述式，以作為區塊的結尾。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)