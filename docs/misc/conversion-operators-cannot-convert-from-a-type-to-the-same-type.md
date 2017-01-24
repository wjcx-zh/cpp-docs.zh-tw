---
title: "轉換運算子無法從類型轉換為相同的類型 | Microsoft Docs"
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
  - "bc33024"
  - "vbc33024"
helpviewer_keywords: 
  - "BC33024"
ms.assetid: 4b47bcb0-4f0c-4d1c-9274-cce5b8e2b370
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 轉換運算子無法從類型轉換為相同的類型
轉換運算子宣告時為參數和傳回值都使用相同的類型。  
  
 從任何類型轉換為自己並不具意義。  
  
 **錯誤 ID︰**BC33024  
  
### 更正這個錯誤  
  
-   請變更參數或傳回值的類型。 它們其中一個必須是定義這個運算子的類別或結構的類型。 另一個必須是不同的類型。  
  
-   如果您要在參數的內容上執行轉換，請使用[Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 來定義 `Function` 程序，而不是運算子。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)