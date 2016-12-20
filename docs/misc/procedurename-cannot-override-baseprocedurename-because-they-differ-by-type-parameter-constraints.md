---
title: "&#39;&lt;程序名稱&gt;&#39; 無法覆寫 &#39;&lt;基底程序名稱&gt;&#39;，因為其類型參數條件約束不同 | Microsoft Docs"
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
  - "BC32077"
  - "vbc32077"
helpviewer_keywords: 
  - "BC32077"
ms.assetid: 9be1a88d-c1a4-4f12-8e72-74abb2be565d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;程序名稱&gt;&#39; 無法覆寫 &#39;&lt;基底程序名稱&gt;&#39;，因為其類型參數條件約束不同
泛型程序嘗試覆寫泛型基底類別程序，但是它們具有其類型參數的不同條件約束清單。  
  
 若要覆寫基底類別程序，覆寫程序不只要符合基底類別程序的完整簽章，還必須符合程序的存取層級以及每個參數的傳遞機制。  
  
 若要覆寫泛型基底類別程序，覆寫程序必須額外符合類型參數的數目以及每個類型參數的條件約束清單。  
  
 如需覆寫需求的詳細資訊，請參閱[Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC32077  
  
### 更正這個錯誤  
  
-   如果您想要覆寫基底類別程序，請修改類型參數條件約束，使其完全符合基底類別程序的類型參數條件約束。  
  
-   如果類型參數條件約束必須保持原狀，則不能覆寫基底類別程序。 請從宣告中移除 `Overrides` 關鍵字。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)