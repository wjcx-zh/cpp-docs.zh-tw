---
title: "引數無法傳遞至類型參數上所使用的 &#39;New&#39; | Microsoft Docs"
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
  - "BC32085"
  - "vbc32085"
helpviewer_keywords: 
  - "BC32085"
ms.assetid: a60bf62d-2b2e-4621-b8db-e67720b918fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引數無法傳遞至類型參數上所使用的 &#39;New&#39;
宣告或指派陳述式會叫用泛型類型，並將建構函式引數提供給具有 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md) 條件約束的類型參數。  
  
 類型參數的條件約束清單可以指定傳遞至該類型參數的類型引數必須公開建立程式碼可以存取的無參數建構函式。 類型參數不能要求可採用參數的建構函式，而具有 `New` 條件約束的類型參數無法接受這類建構函式。  
  
 **錯誤 ID︰**BC32085  
  
### 更正這個錯誤  
  
-   請移除叫用泛型類型之陳述式中類型引數後面的引數清單。 您無法將建構函式引數傳遞至相對應的類型參數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)