---
title: "多個基底介面中宣告的多載化方法無效 | Microsoft Docs"
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
  - "bc31410"
  - "vbc31410"
helpviewer_keywords: 
  - "BC31410"
ms.assetid: 7d1831c2-837c-4b02-8492-d0fc038fe184
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 多個基底介面中宣告的多載化方法無效
多個繼承介面隱含地多載相同方法。  
  
 **錯誤 ID︰**BC31410  
  
### 更正這個錯誤  
  
-   請使用 `Shadows` 修飾詞，而不要使用 `Overloads` 修飾詞。  
  
## 請參閱  
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)