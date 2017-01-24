---
title: "運算子不是可多載的 | Microsoft Docs"
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
  - "vbc33002"
  - "bc33002"
helpviewer_keywords: 
  - "BC33002"
ms.assetid: 8628ea42-57d8-41ca-8bdc-5e4c27be543e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子不是可多載的
只有特定運算子適用於多載。 下表列出您可以定義的運算子清單。  
  
|類型|運算子|  
|--------|---------|  
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|二元|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|轉換 \(一元\)|`CType`|  
  
 請注意，二元清單中的 `=` 運算子是比較運算子，而不是指派運算子。  
  
 **錯誤 ID︰**BC33002  
  
### 更正這個錯誤  
  
1.  從一組可多載的運算子中選取運算子。  
  
2.  如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。  
  
## 請參閱  
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md)