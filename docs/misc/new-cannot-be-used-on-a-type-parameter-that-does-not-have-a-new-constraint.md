---
title: "&#39;New&#39; 無法在沒有 &#39;New&#39; 條件約束的類型參數上使用 | Microsoft Docs"
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
  - "bc32046"
  - "vbc32046"
helpviewer_keywords: 
  - "BC32046"
ms.assetid: 7ec6b52d-6fd5-47a0-b4a2-163bfd3dae35
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; 無法在沒有 &#39;New&#39; 條件約束的類型參數上使用
宣告陳述式使用 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md) 子句指定類型參數作為要建立的類型，而類型參數宣告時沒有 `New` 條件約束。  
  
 類型參數上的*「條件約束」*\(constraint\)，在建立泛型類型時，對於傳遞給該類型參數的任何類型引數會加諸需求。`New` 條件約束指定類型引數必須公開建立程式碼可以存取的無參數建構函式。 這允許宣告陳述式中的 `New` 子句建立該類型的執行個體。  
  
 **錯誤 ID︰**BC32046  
  
### 更正這個錯誤  
  
-   如果您要求類型引數公開可存取的無參數建構函式，請將 `New` 條件約束加入類型參數的宣告。  
  
-   如果您無法要求類型引數公開可存取的無參數建構函式，請從宣告陳述式移除 `New` 子句。 您無法保證傳遞給該類型參數的任何類型引數都允許建立執行個體。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)