---
title: "&#39;System.STAThreadAttribute&#39; 和 &#39;System.MTAThreadAttribute&#39; 無法同時套用至同一個方法 | Microsoft Docs"
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
  - "vbc31512"
  - "bc31512"
helpviewer_keywords: 
  - "BC31512"
ms.assetid: ee27e834-707d-4f02-86d4-831fa9bd2359
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.STAThreadAttribute&#39; 和 &#39;System.MTAThreadAttribute&#39; 無法同時套用至同一個方法
`System.STAThreadAttribute` 和 `System.MTAThreadAttribute` 屬性互為獨佔模式。  
  
 **錯誤 ID︰**BC31512  
  
### 更正這個錯誤  
  
1.  請套用 `System.MTAThreadAttribute` 或 `System.STAThreadAttribute`，但兩者不能同時套用。  
  
## 請參閱  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)