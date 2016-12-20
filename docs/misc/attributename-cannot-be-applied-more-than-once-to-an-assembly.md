---
title: "&#39;&lt;屬性名稱&gt;&#39; 不可以重複套用到組件。 | Microsoft Docs"
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
  - "bc31521"
  - "vbc31521"
helpviewer_keywords: 
  - "BC31521"
ms.assetid: 7312570f-8afb-4afe-992f-b6f7796f5f26
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;屬性名稱&gt;&#39; 不可以重複套用到組件。
屬性只能套用一次指定的屬性。  
  
 **錯誤識別碼：**BC31521  
  
### 更正這個錯誤  
  
1.  移除這個屬性多餘的應用。  
  
2.  如果使用自行開發的自訂屬性，請修改 `AttributeUsageAttribute` ，並將 `AllowMultiple` 屬性設為 `True`。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName>