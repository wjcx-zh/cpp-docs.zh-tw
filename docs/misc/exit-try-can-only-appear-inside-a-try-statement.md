---
title: "&#39;Exit Try&#39; 只能在 &#39;Try&#39; 陳述式內出現 | Microsoft Docs"
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
  - "vbc30393"
  - "bc30393"
helpviewer_keywords: 
  - "BC30393"
ms.assetid: b8651df3-a32f-478c-a6d8-aa0ef584155f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Try&#39; 只能在 &#39;Try&#39; 陳述式內出現
`Exit Try` 只可以出現在 `Try` 區塊陳述式內。 您有多餘的 `Exit Try` 陳述式，或您的 `Exit Try` 陳述式出現在其對應 `Try` 區塊的範圍之外。  
  
 **錯誤 ID︰**BC30393  
  
### 更正這個錯誤  
  
1.  找到並移除不必要的`Exit Try` 陳述式。  
  
2.  請將 `Exit Try`陳述式移至您程式碼中的適當位置。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)