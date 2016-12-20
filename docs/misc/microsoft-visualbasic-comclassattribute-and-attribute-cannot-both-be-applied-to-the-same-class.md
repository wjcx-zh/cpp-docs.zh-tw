---
title: "無法將 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 和 &#39;&lt;屬性&gt;&#39; 同時套用至相同的類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32501"
  - "bc32501"
helpviewer_keywords: 
  - "BC32501"
ms.assetid: dc1bf4f1-f030-4df3-aae8-524af9c2fda7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 和 &#39;&lt;屬性&gt;&#39; 同時套用至相同的類別
`COMClassAttribute` 屬性區塊是與未套用至 COM 物件的屬性搭配使用。 可能的原因是混合使用 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 與 COM 屬性。  
  
 **錯誤 ID︰**BC32501  
  
### 更正這個錯誤  
  
-   請移除未套用至 COM 的 `COMClassAttribute` 屬性區塊或屬性。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)