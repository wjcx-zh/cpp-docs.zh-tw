---
title: "類型字元無法在類型參數宣告中使用 | Microsoft Docs"
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
  - "vbc32041"
  - "bc32041"
helpviewer_keywords: 
  - "BC32041"
ms.assetid: 24f9a514-f3d4-46c3-805c-71225f6fec59
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型字元無法在類型參數宣告中使用
類型參數宣告包含至少一個識別項類型字元。  
  
 泛型類型的類型參數必須是有效的 Visual Basic 名稱。 允許的字元不包括任何識別項類型字元 \(`%`、`&`、`@`、`!`、`#` 和 `$`\)。 請參閱 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC32041  
  
### 更正這個錯誤  
  
-   請從類型參數宣告中移除一個或多個類型識別項字元。  
  
## 請參閱  
 [Type Characters](../Topic/Type%20Characters%20\(Visual%20Basic\).md)   
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)