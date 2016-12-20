---
title: "&#39;End Try&#39; 之前必須搭配相對應的 &#39;Try&#39; | Microsoft Docs"
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
  - "bc30383"
  - "vbc30383"
helpviewer_keywords: 
  - "BC30383"
ms.assetid: 1d13357a-ab44-4082-b204-6e2e94f4774e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Try&#39; 之前必須搭配相對應的 &#39;Try&#39;
`End` `Try` 用來完成 `Try` 區塊，因此它只能出現在區塊結尾。 您有多餘的 `End Try` 陳述式，或您的 `End``Try` 陳述式出現在其對應 `Try` 區塊的範圍之外。  
  
 **錯誤 ID︰**BC30383  
  
### 更正這個錯誤  
  
1.  找到並移除不必要的 `End Try`。  
  
2.  請將 `End Try` 移至您程式碼中的適當位置。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)