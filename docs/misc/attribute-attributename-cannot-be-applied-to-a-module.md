---
title: "無法將屬性 &#39;&lt;屬性名稱&gt;&#39; 套用至模組 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30549"
  - "bc30549"
helpviewer_keywords: 
  - "BC30549"
ms.assetid: b38fea31-6b0b-4c54-9518-b59226505802
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將屬性 &#39;&lt;屬性名稱&gt;&#39; 套用至模組
您嘗試將屬性套用至其 `AttributeUsageAttribute` 未指定 `AttributeTargets.Module` 的模組。 當宣告屬性時，不會定義將屬性套用至模組。  
  
 **錯誤 ID︰**BC30549  
  
### 更正這個錯誤  
  
1.  檢查屬性宣告，並指定 `AttributeTargets.Module`或`AttributeTargets.All`。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>