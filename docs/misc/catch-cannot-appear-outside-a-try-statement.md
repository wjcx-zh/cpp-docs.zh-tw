---
title: "&#39;Catch&#39; 不可以出現在 &#39;Try&#39; 陳述式之外。 | Microsoft Docs"
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
  - "bc30380"
  - "vbc30380"
helpviewer_keywords: 
  - "BC30380"
ms.assetid: 73ce950d-881f-4532-8024-40a4930abd32
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; 不可以出現在 &#39;Try&#39; 陳述式之外。
`Catch` 必須出現在 `Try...Catch...Finally` 陳述式區塊內。`Try` 區塊中有不必要的 `Catch` 陳述式，或 `Catch` 陳述式出現在其對應 `Try` 區塊的範圍之外。  
  
 **錯誤識別碼：**BC30380  
  
### 更正這個錯誤  
  
1.  如果 `Catch` 陳述式不是必要的，請刪除它，或放在 `Try...Catch...Finally` 陳述式區塊中。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)