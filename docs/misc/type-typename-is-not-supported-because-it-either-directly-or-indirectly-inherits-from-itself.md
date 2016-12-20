---
title: "因為類型 &#39;&lt;類型名稱&gt;&#39; 直接或間接繼承自本身，所以不受支援 | Microsoft Docs"
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
  - "bc30916"
  - "vbc30916"
helpviewer_keywords: 
  - "BC30916"
ms.assetid: cea33daf-1971-4b70-a01d-7d8b5c9e4269
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 因為類型 &#39;&lt;類型名稱&gt;&#39; 直接或間接繼承自本身，所以不受支援
類別或介面繼承自本身，或最後繼承自它的另一個類別或介面。  
  
 Visual Basic 不支援循環繼承。  
  
 **錯誤 ID︰**BC30916  
  
### 更正這個錯誤  
  
-   請變更繼承結構，以根據未繼承自任何其他類別或介面的基底類別或介面。  
  
## 請參閱  
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)