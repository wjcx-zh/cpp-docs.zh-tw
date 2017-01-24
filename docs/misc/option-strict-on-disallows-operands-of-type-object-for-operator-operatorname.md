---
title: "Option Strict On 不允許運算子 &#39;&lt;運算子名稱&gt;&#39; 中 Object 類型的運算元 | Microsoft Docs"
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
  - "bc32013"
  - "vbc32013"
helpviewer_keywords: 
  - "BC32013"
ms.assetid: cd197da8-2676-453b-884b-3231fb6f909d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 不允許運算子 &#39;&lt;運算子名稱&gt;&#39; 中 Object 類型的運算元
Option Strict On 不允許運算子 '\<運算子名稱\>' 中 Object 類型的運算元。 請使用 Is 運算子測試物件識別。  
  
 `Option Strict` 是 `On` 時，算術比較運算子 \(例如 `=`\) 是與一個或多個物件變數搭配使用。  
  
 **錯誤 ID︰**BC32013  
  
### 更正這個錯誤  
  
1.  如果物件變數包含數值，而您想要進行算術比較，請開啟 `Option Strict Off`。  
  
2.  請使用 `Is` 運算子比較物件識別。  
  
## 請參閱  
 [Comparison Operators](../Topic/Comparison%20Operators%20\(Visual%20Basic\).md)   
 [Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md)   
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)