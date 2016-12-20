---
title: "在 Sub 或 Set 中的 &#39;Return&#39; 陳述式無法傳回值 | Microsoft Docs"
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
  - "bc30647"
  - "vbc30647"
helpviewer_keywords: 
  - "BC30647"
ms.assetid: d4c05c28-d650-4f49-976e-650d84802036
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 Sub 或 Set 中的 &#39;Return&#39; 陳述式無法傳回值
`Sub` 程序和屬性 `Set` 程序無法傳回值。  
  
 **錯誤 ID：**BC30647  
  
### 更正這個錯誤  
  
-   請將目前的程序變更為或函式，如果目前的程序是屬性的一部分，則變更為 `Get` 屬性程序。  
  
-   您可以藉由使用 `ByRef` 關鍵字修改參考所傳遞的參數值，有效地從 `Sub` 程序傳回值。  
  
## 請參閱  
 [Return Statement](../Topic/Return%20Statement%20\(Visual%20Basic\).md)   
 [Sub Procedures](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [函式程序](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)