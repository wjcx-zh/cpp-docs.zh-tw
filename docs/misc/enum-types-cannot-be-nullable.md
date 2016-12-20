---
title: "列舉類型不可為 Null | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32129"
  - "bc32129"
helpviewer_keywords: 
  - "BC32129"
ms.assetid: 9e0fe5c9-72c7-4905-b177-d00cc3469ea9
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 列舉類型不可為 Null
用來宣告列舉的基礎類型不可為 Null。 例如，下列程式碼會造成此錯誤：  
  
```vb#  
'' Not valid. ' Enum exampleEnum As Integer? '     Member declarations. ' End Enum  
```  
  
 **錯誤 ID︰**BC32129  
  
### 更正這個錯誤  
  
-   請不要在 `Enum` 宣告中使用可為 Null 的基礎類型。  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)   
 [Enum Statement](../Topic/Enum%20Statement%20\(Visual%20Basic\).md)