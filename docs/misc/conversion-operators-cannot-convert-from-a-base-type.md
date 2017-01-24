---
title: "轉換運算子無法從基底類型進行轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33030"
  - "vbc33030"
helpviewer_keywords: 
  - "BC33030"
ms.assetid: b19800ab-6a32-473f-b7ee-7de584e4ccae
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 轉換運算子無法從基底類型進行轉換
轉換運算子是以傳回類型所衍生自的參數類型進行宣告。  
  
 在編譯時期，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 會考慮存在從任何參考類型到其繼承階層架構中任何類型的預先定義轉換 \(亦即，從中衍生的任何類型，或從它衍生的任何類型\)。 這類轉換可能會在執行階段失敗，但編譯器無法預測執行階段結果，因此它可以編譯任何這類轉換。  
  
 因為編譯器認為已定義這項轉換，所以不允許您重新定義它。  
  
 **錯誤 ID︰**BC33030  
  
### 更正這個錯誤  
  
-   請完整移除這個運算子定義。 它已預先定義。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)