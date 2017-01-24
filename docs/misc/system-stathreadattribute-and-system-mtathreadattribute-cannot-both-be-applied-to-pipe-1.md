---
title: "&#39;System.STAThreadAttribute&#39; 和 &#39;System.MTAThreadAttribute&#39; 無法同時套用至 &#39;|1&#39; | Microsoft Docs"
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
  - "bc31513"
  - "vbc31513"
helpviewer_keywords: 
  - "BC31513"
ms.assetid: 7efb4c8e-d31c-4273-9d85-8cd2bef4d120
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.STAThreadAttribute&#39; 和 &#39;System.MTAThreadAttribute&#39; 無法同時套用至 &#39;|1&#39;
`System.STAThreadAttribute` 和 `System.MTAThreadAttribute` 屬性互為獨佔模式。  
  
 **錯誤 ID︰**BC31513  
  
### 更正這個錯誤  
  
1.  請套用 `System.MTAThreadAttribute` 或 `System.STAThreadAttribute`，但兩者不能同時套用。  
  
## 請參閱  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)