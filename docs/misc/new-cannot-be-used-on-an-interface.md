---
title: "&#39;New&#39; 無法在介面上使用 | Microsoft Docs"
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
  - "vbc30375"
  - "bc30375"
helpviewer_keywords: 
  - "BC30375"
ms.assetid: c1e06108-1b52-4cbe-8cae-e816a0dbac0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; 無法在介面上使用
將變數宣告為介面類型時，[Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md) 會使用 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md) 子句。  
  
 雖然介面是參考類型，但是您無法建立介面的執行個體。 您可以使用 `New` 僅建立類別或結構的執行個體。  
  
 **錯誤 ID︰**BC30375  
  
### 更正這個錯誤  
  
1.  如果變數是介面類型，請移除 `New` 關鍵字。  
  
2.  如果變數是要參考執行個體，請將它宣告為類別或結構類型。 請保留 `New` 關鍵字來建立執行個體。  
  
## 請參閱  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Structure Statement](../Topic/Structure%20Statement.md)