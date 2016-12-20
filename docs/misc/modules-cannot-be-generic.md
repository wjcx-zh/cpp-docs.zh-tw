---
title: "模組不可以是泛型的 | Microsoft Docs"
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
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模組不可以是泛型的
`Module` 陳述式使用 `Of` 關鍵字來引入泛型類型參數。  
  
 您可以定義和使用泛型類別、結構、介面、程序和委派。 您無法定義泛型模組。  
  
 **錯誤 ID︰**BC32073  
  
### 更正這個錯誤  
  
1.  請從 `Module` 陳述式中移除 `Of` 關鍵字。  
  
2.  如果您想要泛型模組的功能，則最接近的近似值就是泛型類別。 請使用 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md) 而非 `Module` 陳述式。  
  
## 請參閱  
 [Module Statement](../Topic/Module%20Statement.md)   
 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [如何：定義可以在不同資料類型上提供完全相同功能的類別](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)