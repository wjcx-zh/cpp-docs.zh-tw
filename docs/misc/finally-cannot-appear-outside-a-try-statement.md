---
title: "&#39;Finally&#39; 不可以出現在 &#39;Try&#39; 陳述式之外 | Microsoft Docs"
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
  - "vbc30382"
  - "bc30382"
helpviewer_keywords: 
  - "BC30382"
ms.assetid: 0314d8d2-18bc-4bbd-858c-0a18408b52fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; 不可以出現在 &#39;Try&#39; 陳述式之外
`Finally` 用來完成 `Try...Catch...Finally` 區塊，因此它只能出現在區塊結尾一次。 您有不必要的 `Finally`，或您的 `Finally` 陳述式出現在其對應 `Try` 區塊的範圍之外。  
  
 **錯誤 ID︰**BC30382  
  
### 更正這個錯誤  
  
1.  請找到並移除不必要的 `Finally`陳述式。  
  
2.  請將 `Finally` 陳述式移至您程式碼中的適當位置。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)