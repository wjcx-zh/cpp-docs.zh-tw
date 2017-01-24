---
title: "Option Strict On 要求所有的方法參數都必須有 &#39;As&#39; 子句 | Microsoft Docs"
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
  - "vbc30211"
  - "bc30211"
helpviewer_keywords: 
  - "BC30211"
ms.assetid: 855795ce-8499-4525-a1de-cbb8ba364cd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 要求所有的方法參數都必須有 &#39;As&#39; 子句
方法包含不含 `As` 子句的參數。 開啟 `Option Strict` 時，必須使用 `As` 子句宣告每個變數、屬性、程序引數與函式傳回以指定其資料類型，例如 `Sub GetData(ByVal filter As String)`。  
  
 **錯誤 ID︰**BC30211  
  
### 更正這個錯誤  
  
-   請查看 `As` 關鍵字是否拼字錯誤。  
  
-   針對宣告的變數提供 `As` 子句，或關閉 `Option Strict`。  
  
## 請參閱  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Sub Statement](../Topic/Sub%20Statement%20\(Visual%20Basic\).md)   
 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md)