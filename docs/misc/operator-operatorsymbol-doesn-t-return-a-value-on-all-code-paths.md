---
title: "運算子 &#39;&lt;運算子符號&gt;&#39; 在所有程式碼路徑上皆不會傳回值 | Microsoft Docs"
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
  - "vbc42106"
  - "bc42106"
helpviewer_keywords: 
  - "BC42106"
ms.assetid: 175b2bc9-5233-462d-97de-9d97b003cc46
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子 &#39;&lt;運算子符號&gt;&#39; 在所有程式碼路徑上皆不會傳回值
運算子 '\<運算子符號\>' 在所有程式碼路徑上皆不會傳回值。 使用結果時，Null 參考例外狀況可能在執行階段時發生。  
  
 運算子程序有至少一個通過程式碼的可能路徑不會傳回值。  
  
 您只能藉由將運算子程序包含在 [Return Statement](../Topic/Return%20Statement%20\(Visual%20Basic\).md)，以從運算子程序傳回值。  
  
 如果控制權傳遞給 `End Operator` 陳述式，運算子程序會傳回屬性資料類型的預設值。 如需詳細資訊，請參閱 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md)中的＜行為＞。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42106  
  
### 更正這個錯誤  
  
-   請檢查控制項流程邏輯，確定每個可能路徑的結尾為 `Return` 陳述式。 特別是 `End Operator` 之前的最後一個陳述式應該是 `Return` 陳述式。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)