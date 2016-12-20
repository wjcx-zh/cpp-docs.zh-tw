---
title: "類型引數 &#39;&lt;類型引數名稱&gt;&#39; 並未繼承或實作條件約束類型 &#39;&lt;類型引數名稱&gt;&#39; | Microsoft Docs"
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
  - "bc32044"
  - "vbc32044"
helpviewer_keywords: 
  - "BC32044"
ms.assetid: be91f648-c07d-4991-8ed1-28b1327619c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型引數 &#39;&lt;類型引數名稱&gt;&#39; 並未繼承或實作條件約束類型 &#39;&lt;類型引數名稱&gt;&#39;
提供給泛型類型的類型引數未滿足其對應類型參數的繼承或實作條件約束。  
  
 條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。 可能的需求如下：  
  
-   類型引數必須實作一或多個介面  
  
-   類型引數最多只能繼承自一個類別  
  
 您可以合併單一類型參數的上述需求。[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法建構類型，除非程式碼所提供的類型引數滿足泛型類型上所定義之每個類型參數的每個條件約束。  
  
 **錯誤 ID︰**BC32044  
  
### 更正這個錯誤  
  
-   請選取可實作針對類型參數所指定的每個介面之類型的類型引數，以及繼承自所指定類別 \(如果有的話\) 之類型的類型引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [如何：使用泛型類別](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)