---
title: "Option Strict On 禁止使用 Object 類型 (屬於運算子 &#39;&lt;運算子名稱&gt;&#39;) 的運算元 | Microsoft Docs"
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
  - "bc30038"
  - "vbc30038"
helpviewer_keywords: 
  - "BC30038"
ms.assetid: eb047d36-1fb4-460d-ae98-c76f31a89bed
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 禁止使用 Object 類型 (屬於運算子 &#39;&lt;運算子名稱&gt;&#39;) 的運算元
針對物件變數唯一定義的運算子是 `Is` 和 `TypeOf...Is`。 當 `Option Strict` 是 `On` 時，所有的運算元必須屬於為指定運算子所定義的資料類型。  
  
 **錯誤 ID︰**BC30038  
  
### 更正這個錯誤  
  
-   請使用適當的類型轉換函式，例如 `CInt` 或 `CStr`，將運算元轉換成為運算子定義的資料類型。  
  
## 請參閱  
 [Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md)   
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)   
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)