---
title: "方法/多行 Lambda 外的標籤無效 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30016"
  - "bc30016"
helpviewer_keywords: 
  - "BC30016"
ms.assetid: 17d12a96-d759-4df9-882c-5e45c1d814a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法/多行 Lambda 外的標籤無效
您只能在 `Sub`、`Function`、屬性 `Get` 或屬性 `Set` 程序內將標籤加入陳述式。 只有可執行的陳述式可以有標籤，且所有可執行的陳述式都必須在程序內。  
  
 **錯誤 ID︰**BC30016  
  
### 更正這個錯誤  
  
1.  請移除陳述式中的標籤，或將陳述式移到程序內。  
  
## 請參閱  
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)   
 [Sub Statement](../Topic/Sub%20Statement%20\(Visual%20Basic\).md)   
 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md)   
 [Get Statement](../Topic/Get%20Statement.md)   
 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md)