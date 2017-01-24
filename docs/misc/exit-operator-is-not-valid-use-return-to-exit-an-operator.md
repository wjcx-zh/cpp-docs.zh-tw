---
title: "&#39;Exit Operator&#39; 無效。 請使用 &#39;Return&#39; 結束運算子 | Microsoft Docs"
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
  - "bc33008"
  - "vbc33008"
helpviewer_keywords: 
  - "BC33008"
ms.assetid: 8c44456b-8fd2-4168-ad8c-b6da129242ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Operator&#39; 無效。 請使用 &#39;Return&#39; 結束運算子
`Operator` 程序中出現 `Exit Operator` 陳述式。  
  
 您必須使用 [Return Statement](../Topic/Return%20Statement%20\(Visual%20Basic\).md) 從 `Operator` 程序返回。[Exit Statement](../Topic/Exit%20Statement%20\(Visual%20Basic\).md) 不接受 `Operator` 關鍵字，而且 `End Operator` 陳述式不會將控制權傳回呼叫程式碼。  
  
 **錯誤 ID︰**BC33008  
  
### 更正這個錯誤  
  
-   以 `Return` 陳述式取代 `Exit Operator` 陳述式。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)