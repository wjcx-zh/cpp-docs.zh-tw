---
title: "Option Strict On 要求所有的函式、屬性和運算子宣告都擁有 &#39;As&#39; 子句 | Microsoft Docs"
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
  - "vbc30210"
  - "bc30210"
helpviewer_keywords: 
  - "BC30210"
ms.assetid: 4d217e56-0eac-4834-bcad-234a69809390
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 要求所有的函式、屬性和運算子宣告都擁有 &#39;As&#39; 子句
宣告包含宣告的屬性或函式傳回，但沒有 `As` 子句。 當 `Option Strict` 是 `On` 時，必須使用 `As` 子句宣告每個變數、屬性、程序引數與函式傳回以指定其資料類型，例如 `Dim MyNum As Short`。  
  
 **錯誤 ID︰**BC30210  
  
### 更正這個錯誤  
  
1.  請查看 `As` 關鍵字是否拼字錯誤。  
  
2.  請提供宣告的屬性或函式傳回的 `As` 子句，或開啟 `Option Strict Off`。  
  
## 請參閱  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [函式程序](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)