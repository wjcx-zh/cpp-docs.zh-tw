---
title: "無法合併 &#39;Widening&#39; 和 &#39;Narrowing&#39; | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法合併 &#39;Widening&#39; 和 &#39;Narrowing&#39;
[Operator Statement](../Topic/Operator%20Statement.md) 同時指定 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 和 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md)。  
  
 當您定義轉換運算子時，必須將它宣告為 `Widening` 或 `Narrowing`。 這些特性是互斥的，因此您無法同時指定兩者。  
  
 **錯誤 ID︰**BC33001  
  
### 更正這個錯誤  
  
-   從 `Operator` 陳述式中移除 `Widening` 或 `Narrowing` 關鍵字。 您必須指定其中一個。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)