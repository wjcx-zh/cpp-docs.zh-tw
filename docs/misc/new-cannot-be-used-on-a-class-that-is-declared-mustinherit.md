---
title: "&#39;New&#39; 不可以使用在宣告為 &#39;MustInherit&#39; 的類別上 | Microsoft Docs"
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
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; 不可以使用在宣告為 &#39;MustInherit&#39; 的類別上
無法直接具現化 `MustInherit` 類別，因此，`New` 運算子不能用在 `MustInherit` 類別上。 雖然您可以有編譯時間類型為 `MustInherit` 的變數和值，但是這類變數和值一定會是 Null 值或包含衍生自 `MustInherit` 類型之一般類別的執行個體參考。  
  
 **錯誤 ID︰**BC30569  
  
### 更正這個錯誤  
  
-   請移除 `New` 運算子。  
  
## 請參閱  
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)