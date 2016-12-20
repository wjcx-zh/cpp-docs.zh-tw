---
title: "在 &#39;Try&#39; 陳述式中，&#39;Catch&#39; 不可以出現在 &#39;Finally&#39; 之後 | Microsoft Docs"
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
  - "vbc30379"
  - "bc30379"
helpviewer_keywords: 
  - "BC30379"
ms.assetid: 33d1278b-cf10-4c66-aaf8-08a4372f370b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;Try&#39; 陳述式中，&#39;Catch&#39; 不可以出現在 &#39;Finally&#39; 之後
`Catch` 陳述式會出現在結尾為 `Try` 陳述式區塊之 `Finally` 後面的程式碼中。`Catch` 必須出現在 `Try...Catch...Finally` 陳述式區塊內。  
  
 **錯誤 ID︰**BC30379  
  
### 更正這個錯誤  
  
1.  請將 `Catch` 陳述式移至程式碼中的更適當位置。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)