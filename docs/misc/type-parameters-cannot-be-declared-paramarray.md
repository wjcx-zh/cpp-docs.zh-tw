---
title: "&lt;類型&gt; 參數不可以宣告為 &#39;ParamArray&#39; | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;類型&gt; 參數不可以宣告為 &#39;ParamArray&#39;
委派、事件或運算子的定義宣告了 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md) 參數。  
  
 只有 `Declare`、`Function`、`Property` 和 `Sub` 參數可以使用 `ParamArray` 參數。  
  
 **錯誤 ID︰**BC33009  
  
### 更正這個錯誤  
  
-   請從參數清單中移除 `ParamArray` 關鍵字。  
  
-   如果定義運算子，可以透過一系列多載取得 `ParamArray` 功能。  
  
-   如果定義委派或事件，則必須修改這部分應用的整體邏輯。 您無法在委派或事件參數上使用 [Optional](../Topic/Optional%20\(Visual%20Basic\).md) 或 `ParamArray` 參數，或是其多載版本。  
  
## 請參閱  
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)