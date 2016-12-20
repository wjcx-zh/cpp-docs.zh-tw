---
title: "XML 文件剖析錯誤：起始標記 &#39;&lt;標記&gt;&#39; 並沒有對稱的結束標記 | Microsoft Docs"
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
  - "vbc42316"
  - "BC42316"
helpviewer_keywords: 
  - "BC42316"
ms.assetid: 45b68176-ebf6-43af-820e-6801aabb6c57
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML 文件剖析錯誤：起始標記 &#39;&lt;標記&gt;&#39; 並沒有對稱的結束標記
XML 文件剖析錯誤：起始標記 \<標記\> 並沒有對稱的結束標記。 將會忽略 XML 註解。  
  
 XML 註解包含起始標記，但未包含對稱的結束標記。  
  
 **錯誤 ID︰**BC42316  
  
### 更正這個錯誤  
  
-   加入與起始標記對稱的結束標記。  
  
     — 或 —  
  
-   如果標記未包含內部文字 \(例如 [\<seealso\>](../Topic/%3Cseealso%3E%20\(Visual%20Basic\).md)\)，請在右角括弧前面指定正斜線。  
  
## 請參閱  
 [XML Comment Tags](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)   
 [Documenting Your Code with XML](../Topic/Documenting%20Your%20Code%20with%20XML%20\(Visual%20Basic\).md)