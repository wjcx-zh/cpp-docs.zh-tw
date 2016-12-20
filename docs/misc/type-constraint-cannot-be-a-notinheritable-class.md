---
title: "類型條件約束不可以為 &#39;NotInheritable&#39; 類別 | Microsoft Docs"
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
  - "vbc32060"
  - "bc32060"
helpviewer_keywords: 
  - "BC32060"
ms.assetid: f45cc0b6-7df1-462a-b3df-c526c143e16a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型條件約束不可以為 &#39;NotInheritable&#39; 類別
條件約束清單包含標記為 [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md) 的類別。  
  
 類型參數的條件約束清單最多只能接受一個類別。 提供給該類型參數的類型引數必須繼承自該類別。 因此，類型參數無法接受*「密封」*\(sealed\) 或 `NotInheritable` 類別作為條件約束。  
  
 **錯誤 ID︰**BC32060  
  
### 更正這個錯誤  
  
-   如果類型參數必須能夠繼承自類別，而且您可以控制類別的定義，請從類別中移除 `NotInheritable` 宣告。  
  
-   如果此類別必須保持 `NotInheritable`，則不能當做條件約束來使用。 請從條件約束清單中移除類別名稱。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)