---
title: "轉換運算子無法從物件進行轉換 | Microsoft Docs"
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
  - "bc33032"
  - "vbc33032"
helpviewer_keywords: 
  - "BC33032"
ms.assetid: 877f626f-7aa1-41d8-b7ca-eb4337d012d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 轉換運算子無法從物件進行轉換
轉換運算子是以[Object Data Type](../Topic/Object%20Data%20Type.md)的參數進行宣告。  
  
 在編譯時期，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 會考慮存在從任何參考類型到其繼承階層架構中任何類型的預先定義轉換 \(亦即，從中衍生的任何類型，或從它衍生的任何類型\)。`Object` 是 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 中的通用資料類型，讓每種類型衍生自 `Object`。  
  
 因為編譯器認為已定義這項轉換，所以不允許您重新定義它。  
  
 **錯誤 ID︰**BC33032  
  
### 更正這個錯誤  
  
-   請完整移除這個運算子定義。 它已預先定義。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [作為通用資料類型的物件 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/5315bf21-2b22-45ab-98cd-5631dffbcb2f)