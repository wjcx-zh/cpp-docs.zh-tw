---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至 &#39;&lt;類別名稱&gt;&#39;，因為它並未宣告為 &#39;Public&#39; | Microsoft Docs"
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
  - "bc32509"
  - "vbc32509"
helpviewer_keywords: 
  - "BC32509"
ms.assetid: ac46851f-53ab-4ce6-87b1-4c4d29508527
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至 &#39;&lt;類別名稱&gt;&#39;，因為它並未宣告為 &#39;Public&#39;
類別是使用 <xref:Microsoft.VisualBasic.ComClassAttribute> 宣告，但其宣告未指定 `Public`。  
  
 若要適合 COM Interop，.NET Framework 類別必須滿足下列需求：  
  
-   它必須是 `Public`、它的所有容器都必須是 `Public`，而且必須公開至少一個 `Public` 成員。  
  
-   它不得是*「抽象」*\(abstract\)；亦即，不得使用 `MustInherit` 進行宣告。  
  
-   它不得是泛型或在泛型容器類型內進行宣告。  
  
 **錯誤 ID：**BC32509  
  
### 更正這個錯誤  
  
-   將 `Public` 關鍵字加入類別宣告中。  
  
     \-或\-  
  
-   如果類別或其包含項目不能是 `Public`，請從類別宣告中移除 <xref:Microsoft.VisualBasic.ComClassAttribute>。 您不能將它公開至 COM。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)