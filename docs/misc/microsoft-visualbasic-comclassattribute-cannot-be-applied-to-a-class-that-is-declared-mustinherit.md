---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至宣告為 &#39;MustInherit&#39; 的類別 | Microsoft Docs"
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
  - "BC32508"
  - "vbc32508"
helpviewer_keywords: 
  - "BC32508"
ms.assetid: c8af606d-f448-4703-98df-e594fd511f92
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至宣告為 &#39;MustInherit&#39; 的類別
類別是使用 <xref:Microsoft.VisualBasic.ComClassAttribute> 所宣告，但是其宣告指定 `MustInherit`。  
  
 若要適合 COM Interop，.NET Framework 類別必須滿足下列需求：  
  
-   它必須是 `Public`、它的所有容器都必須是 `Public`，而且必須公開至少一個 `Public` 成員。  
  
-   它不得是*「抽象」*\(abstract\)；亦即，不得使用 `MustInherit` 進行宣告。  
  
-   它不得是泛型或在泛型容器類型內進行宣告。  
  
 **錯誤 ID︰** BC32508  
  
### 更正這個錯誤  
  
-   請從類別宣告中移除 `MustInherit` 關鍵字。  
  
     \-或\-  
  
-   如果類別或其包含項目必須是泛型，請從類別宣告中移除 <xref:Microsoft.VisualBasic.ComClassAttribute>。 您不能將它公開至 COM。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)