---
title: "已經為此類型參數指定的條件約束類型 &#39;&lt;類型名稱&gt;&#39; | Microsoft Docs"
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
  - "BC32071"
  - "vbc32071"
helpviewer_keywords: 
  - "BC32071"
ms.assetid: 6b0e85e9-3ac8-4181-97de-ca690b95a63c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 已經為此類型參數指定的條件約束類型 &#39;&lt;類型名稱&gt;&#39;
條件約束清單多次包括類別或介面條件約束。  
  
 條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。 您可以利用任意組合指定下列需求：  
  
-   類型引數必須實作一或多個介面  
  
-   類型引數最多只能繼承自一個類別  
  
 類型無法實作或繼承自相同的類型多次，而且您無法在相同的條件約束清單中多次指定類型。  
  
 **錯誤 ID︰**BC32071  
  
### 更正這個錯誤  
  
-   請移除相同類別或介面的任何多餘指定。 它只應該出現在條件約束清單中一次。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)