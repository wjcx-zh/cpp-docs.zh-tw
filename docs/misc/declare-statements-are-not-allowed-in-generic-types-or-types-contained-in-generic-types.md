---
title: "泛型類型或包含在泛型類型中的類型不允許 &#39;Declare&#39; 陳述式 | Microsoft Docs"
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
  - "BC32075"
  - "vbc32075"
helpviewer_keywords: 
  - "BC32075"
ms.assetid: c620b67e-70f8-42ac-8292-e9ea484904c3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型類型或包含在泛型類型中的類型不允許 &#39;Declare&#39; 陳述式
`Declare` 陳述式會顯示為泛型類別或結構的一部分，或泛型類別或結構內所宣告的類別或結構。  
  
 Visual Basic 和 .NET Framework 目前不支援任何的外部參考和泛型類型組合。 編譯器需要外部程序的所有參數和傳回類型，才能正確地進行呼叫。  
  
 **錯誤 ID：**BC32075  
  
### 更正這個錯誤  
  
-   請將 `Declare` 陳述式移至任何泛型類型的範圍之外，或是完全移除它。  
  
## 請參閱  
 [Declare Statement](../Topic/Declare%20Statement.md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)