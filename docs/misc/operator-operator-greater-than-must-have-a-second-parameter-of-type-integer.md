---
title: "運算子 &#39;&lt;運算子&gt;&#39; 的第二個參數類型必須為 &#39;Integer&#39; | Microsoft Docs"
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
  - "BC33041"
  - "vbc33041"
helpviewer_keywords: 
  - "BC33041"
ms.assetid: 5cd56f6d-2f0f-49de-a8e6-59bdb57bdb1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子 &#39;&lt;運算子&gt;&#39; 的第二個參數類型必須為 &#39;Integer&#39;
位元移位運算子和不是 `Integer` 的第二個類型參數一起宣告。  
  
 當您在運算式中使用右移 \(`>>`\) 或左移 \(`<<`\) 運算子時，您可以在第二個運算元中指定移位量。 因為這個運算元的緣故，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 允許您提供任何可擴展為 `Integer` 的資料類型。 不過，第二個運算元的定義嚴定為 `Integer`。 如果用類別或結構上的位元移位運算子定義該類別或結構，第二個運算元的定義必須指定 `Integer`。  
  
 **錯誤識別碼：**BC33041  
  
### 更正這個錯誤  
  
-   變更位元移位運算子的定義以傳回 `Integer` 值。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Bit Shift Operators](../Topic/Bit%20Shift%20Operators%20\(Visual%20Basic\).md)