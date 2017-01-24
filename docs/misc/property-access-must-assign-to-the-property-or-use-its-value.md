---
title: "屬性的存取必須是指定值給屬性或使用屬性值 | Microsoft Docs"
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
  - "bc30545"
  - "vbc30545"
helpviewer_keywords: 
  - "BC30545"
ms.assetid: df271c05-1e7a-44e8-bf53-79f06ef916ab
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性的存取必須是指定值給屬性或使用屬性值
您已嘗試存取屬性，但未指派或使用它的值。 下列程式碼提供一個範例：  
  
 [!CODE [VbVbalrErrorSamples#1](VbVbalrErrorSamples#1)]  
  
 **錯誤 ID︰**BC30545  
  
### 更正這個錯誤  
  
-   將值指派給屬性，如下列範例所示：  
  
     [!CODE [VbVbalrErrorSamples#3](VbVbalrErrorSamples#3)]  
  
     \-或\-  
  
-   使用屬性的值，如下列範例所示：  
  
     [!CODE [VbVbalrErrorSamples#2](VbVbalrErrorSamples#2)]  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [Assignment Operators](../Topic/Assignment%20Operators%20\(Visual%20Basic\).md)