---
title: "&#39;AddressOf&#39; 運算式在 &#39;Select Case&#39; 陳述式的第一個運算式中無效 | Microsoft Docs"
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
  - "bc36636"
  - "vbc36636"
helpviewer_keywords: 
  - "BC36636"
ms.assetid: 2ccc0ccc-d4d0-4910-8859-dedfa57c8126
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddressOf&#39; 運算式在 &#39;Select Case&#39; 陳述式的第一個運算式中無效
您不能使用 `AddressOf` 運算式來測試 `Select Case` 陳述式中的運算式。`AddressOf` 運算式會傳回函式委派，因此 `Select Case` 陳述式的測試運算式必須是基本資料類型。  
  
 **錯誤 ID︰**BC36636  
  
### 更正這個錯誤  
  
-   檢查您的程式碼，以判斷不同的條件式建構 \(例如 `If...Then...Else` 陳述式\) 是否可行。  
  
## 請參閱  
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [If...Then...Else Statement](../Topic/If...Then...Else%20Statement%20\(Visual%20Basic\).md)   
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)