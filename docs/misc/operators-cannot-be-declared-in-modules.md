---
title: "不能在模組中宣告運算子 | Microsoft Docs"
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
  - "bc33018"
  - "vbc33018"
helpviewer_keywords: 
  - "BC33018"
ms.assetid: 10a8fd2d-2af7-4f90-9f2a-50c07ebf7589
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能在模組中宣告運算子
[Operator Statement](../Topic/Operator%20Statement.md) 出現在模組定義中。  
  
 您可以將運算子定義為所定義類別或結構的一部分。 運算子必須採用該類別或結構作為它的至少一個運算元。  
  
 運算子必須使用程式設計項目執行個體作為它的其中一個運算元，而且只有類別和結構才具有執行個體。 因此，您無法將運算子定義為任何其他程式設計項目的一部分。  
  
 **錯誤 ID︰**BC33018  
  
### 更正這個錯誤  
  
-   如果您需要在模組上執行作業，請使用 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 來定義可執行該作業的 `Function` 程序。  
  
-   您也可以在模組內定義類別或結構，並且在該類別或結構上定義運算子。 不過，該運算子必須採用該類別或結構的執行個體作為它的至少一個運算元。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)