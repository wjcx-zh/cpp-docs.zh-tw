---
title: "屬性存取子不可以宣告為 &#39;&lt;關鍵字&gt;&#39;。 | Microsoft Docs"
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
  - "vbc31099"
  - "bc31099"
helpviewer_keywords: 
  - "BC31099"
ms.assetid: d6f3b989-39b9-4c47-995a-bd83ec03d7b8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性存取子不可以宣告為 &#39;&lt;關鍵字&gt;&#39;。
`Get` 或 `Set` 程序宣告中包含對屬性程序無效的關鍵字。  
  
 [Get Statement](../Topic/Get%20Statement.md) 和 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md) 只允許存取修飾詞 \(`Public`、`Protected`、`Friend`、`Protected Friend`、`Private`\)。  
  
 **錯誤 ID︰**BC31099  
  
### 更正這個錯誤  
  
-   請從 `Get` 或 `Set` 陳述式中移除無效的關鍵字。  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)