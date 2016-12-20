---
title: "&#39;Namespace&#39; 陳述式只可以發生在檔案或命名空間層級 | Microsoft Docs"
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
  - "bc30618"
  - "vbc30618"
helpviewer_keywords: 
  - "BC30618"
ms.assetid: bcd365a4-5d84-4c3c-83dc-40cb4c47f73b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Namespace&#39; 陳述式只可以發生在檔案或命名空間層級
`Namespace` 陳述式必須出現在 `Option` 陳述式、`Imports` 陳述式和全域屬性後面，但在原始程式檔中的所有其他宣告前面。  
  
 **錯誤 ID︰**BC30618  
  
### 更正這個錯誤  
  
-   將 `Namespace` 陳述式移至命名空間宣告或原始程式檔的上方。  
  
## 請參閱  
 [Namespace Statement](../Topic/Namespace%20Statement.md)   
 [Visual Basic 中的命名空間](../Topic/Namespaces%20in%20Visual%20Basic.md)