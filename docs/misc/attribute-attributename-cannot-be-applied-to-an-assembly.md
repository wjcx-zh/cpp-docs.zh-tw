---
title: "無法將屬性 &#39;&lt;屬性名稱&gt;&#39; 套用至組件 | Microsoft Docs"
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
  - "bc30548"
  - "vbc30548"
helpviewer_keywords: 
  - "BC30548"
ms.assetid: bc36f094-626a-4907-b80b-f195155fa5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將屬性 &#39;&lt;屬性名稱&gt;&#39; 套用至組件
您嘗試將屬性套用至其 `AttributeUsageAttribute` 未指定 `AttributeTargets.Assembly` 的組件。 當宣告屬性時，不會將其定義為適用於組件。  
  
 **錯誤 ID︰**BC30548  
  
### 更正這個錯誤  
  
1.  檢查屬性宣告，並指定 `AttributeTargets.Assembly` 或 `AttributeTargets.All`。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>