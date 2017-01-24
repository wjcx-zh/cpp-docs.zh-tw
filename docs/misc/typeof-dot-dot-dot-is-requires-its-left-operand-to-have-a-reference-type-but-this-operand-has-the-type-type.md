---
title: "&#39;TypeOf ... Is&#39; 的左運算元必須有參考類型，但此運算元有類型 &#39;&lt;類型&gt;&#39; | Microsoft Docs"
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
  - "bc30021"
  - "vbc30021"
helpviewer_keywords: 
  - "BC30021"
ms.assetid: a6e76fc8-9c7f-4e55-8b68-e6e7b03a6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;TypeOf ... Is&#39; 的左運算元必須有參考類型，但此運算元有類型 &#39;&lt;類型&gt;&#39;
`TypeOf...Is` 運算式會檢查物件變數的執行階段類型相容性。 未定義實值類型的這項相容性。  
  
 **錯誤 ID︰**BC30021  
  
### 更正這個錯誤  
  
-   如果 `Option Strict` 是 `Off`，請使用 `TypeName` 或 `VarType` 函式來取得變數的資料類型資訊。  
  
-   如果 `Option Strict` 是 `On`，變數宣告會決定變數的資料類型。  
  
## 請參閱  
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)   
 [不在組建中：TypeName 函式 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/6197bc6c-e8a6-4711-883c-0c95e94e272c)   
 [不在組建中：VarType 函式 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/e820b6fc-faa6-4de4-836a-0466032dc190)   
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)