---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至泛型類別，或套用至巢狀位於泛型類型內的類別 | Microsoft Docs"
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
  - "vbc31527"
  - "bc31527"
helpviewer_keywords: 
  - "BC31527"
ms.assetid: ea125bff-d020-4933-b277-6e24943eea88
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至泛型類別，或套用至巢狀位於泛型類型內的類別
類別以 <xref:Microsoft.VisualBasic.ComClassAttribute> 宣告，但它是泛型，或包含在泛型類別或結構中。  
  
 若要適合 COM Interop，.NET Framework 類別必須滿足下列需求：  
  
-   它必須是 `Public`、它的所有容器都必須是 `Public`，而且必須公開至少一個 `Public` 成員。  
  
-   它不得是*「抽象」*\(abstract\)；亦即，不得使用 `MustInherit` 進行宣告。  
  
-   它不得是泛型或在泛型容器類型內進行宣告。  
  
 **錯誤 ID︰**BC31527  
  
### 更正這個錯誤  
  
-   請變更類別的宣告，使它不是泛型，並確定其包含項目不是泛型。  
  
     \-或\-  
  
-   如果類別或其包含項目必須是泛型，請從類別宣告中移除 <xref:Microsoft.VisualBasic.ComClassAttribute>。 您不能將它公開至 COM。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)