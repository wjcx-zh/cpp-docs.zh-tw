---
title: "類型參數 &#39;&lt;類型參數名稱&gt;&#39; 只能有一個類別條件約束。 | Microsoft Docs"
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
  - "bc32047"
  - "vbc32047"
helpviewer_keywords: 
  - "BC32047"
ms.assetid: ac7ab76b-5300-4c79-b519-5a1287ed5fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型參數 &#39;&lt;類型參數名稱&gt;&#39; 只能有一個類別條件約束。
條件約束清單包含多個類別。  
  
 類型參數的條件約束清單可以接受任意數目的介面，但只能有一個類別。 提供給該類型參數的類型引數必須繼承自該類別，而 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 不支援多重繼承。  
  
 **錯誤 ID：**BC32047  
  
### 更正這個錯誤  
  
-   選取一個類別，且條件約束清單中只包含該類別。  
  
-   您也許可以定義其他的類型參數，以滿足這份條件約束清單中不能包含的一或多個類別。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)