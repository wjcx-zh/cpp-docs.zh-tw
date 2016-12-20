---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至 &#39;Declare&#39; | Microsoft Docs"
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
  - "bc31523"
  - "vbc31523"
helpviewer_keywords: 
  - "BC31523"
ms.assetid: 04c8a14f-9286-4f9a-aad5-a0555e5f09f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至 &#39;Declare&#39;
`DllImportAttribute` 屬性已套用至 `Declare` 函式。 這個屬性只能與空白 `Function` 或 `Sub` 搭配使用。  
  
 **錯誤 ID︰**BC31523  
  
### 更正這個錯誤  
  
1.  請從 `Declare` 陳述式中移除 `DllImportAttribute` 屬性。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Declare Statement](../Topic/Declare%20Statement.md)