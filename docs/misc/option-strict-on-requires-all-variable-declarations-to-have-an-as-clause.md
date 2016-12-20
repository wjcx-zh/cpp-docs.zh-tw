---
title: "Option Strict On 要求所有的變數宣告皆須有 &#39;As&#39; 子句 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30209"
  - "vbc30209"
helpviewer_keywords: 
  - "BC30209"
ms.assetid: 69c2e32a-86aa-4075-a142-440605a7063a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 要求所有的變數宣告皆須有 &#39;As&#39; 子句
宣告中包含宣告的變數，但不含 `As` 子句。 當 `Option Strict` 是 `On` 時，必須使用 `As` 子句宣告每個變數、屬性、程序引數與函式傳回以指定其資料類型，例如 `Dim MyNum As Short`。  
  
 **錯誤 ID：**BC30209  
  
### 更正這個錯誤  
  
1.  請查看 `As` 關鍵字是否拼字錯誤。  
  
2.  針對宣告的變數提供 `As` 子句，或轉為 `Option Strict Off`。  
  
## 請參閱  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [變數宣告](../Topic/Variable%20Declaration%20in%20Visual%20Basic.md)