---
title: "類型參數 &#39;&lt;類型參數名稱&gt;&#39; 不可以限制為本身：&#39;&lt;錯誤訊息&gt;&#39; | Microsoft Docs"
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
  - "bc32113"
  - "vbc32113"
helpviewer_keywords: 
  - "BC32113"
ms.assetid: a74128ae-11d0-46bf-8c0b-c7a2bf881d17
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型參數 &#39;&lt;類型參數名稱&gt;&#39; 不可以限制為本身：&#39;&lt;錯誤訊息&gt;&#39;
類型參數的條件約束清單包含該相同的類型參數。  
  
 類型參數的條件約束清單可以指定任意數目的介面，而且最多可以指定一個類別。 提供給該類型參數的類型引數必須實作每個指定的介面，並繼承自指定的類別。 編譯器需要在發現條件約束清單時已定義的介面和類別。 類型參數不會視為已定義的類型，除非取代為建立泛型類型的程式碼所提供的適當類型引數。  
  
 **錯誤 ID︰**BC32113  
  
### 更正這個錯誤  
  
1.  請檢查其條件約束清單中類型參數和條件約束的拼字。  
  
2.  如果沒有拼字錯誤，請從條件約束清單中移除類型參數的名稱。 它不可以限制為本身。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)