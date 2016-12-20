---
title: "&#39;&lt;成員名稱&gt;&#39; 無法實作 &#39;&lt;介面名稱&gt;.&lt;介面成員名稱&gt;&#39;，因為它們的類型參數條件約束不同 | Microsoft Docs"
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
  - "vbc32078"
  - "BC32078"
helpviewer_keywords: 
  - "BC32078"
ms.assetid: 2c971345-edb4-491e-9202-8eb8286b66f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;成員名稱&gt;&#39; 無法實作 &#39;&lt;介面名稱&gt;.&lt;介面成員名稱&gt;&#39;，因為它們的類型參數條件約束不同
泛型事件、屬性或程序嘗試實作介面中所定義的類似成員，但是它們具有其類型參數的不同條件約束清單。  
  
 若要實作介面成員，實作成員不僅必須符合介面成員的完整簽章，也必須符合每個參數的傳遞機制。  
  
 若要實作泛型介面成員，實作成員必須額外符合類型參數的數目以及每個類型參數的條件約束清單。  
  
 如需介面實作的詳細資訊，請參閱[不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)。  
  
 **錯誤 ID︰**BC32078  
  
### 更正這個錯誤  
  
-   如果您想要實作介面成員，請修改類型參數條件約束，使其完全符合介面成員的類型參數條件約束。  
  
-   如果類型參數條件約束必須保持原狀，則不能在這個宣告中實作介面成員。 請從宣告中移除 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md) 關鍵字。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [不在組建中：在 Visual Basic 中的介面實作範例](http://msdn.microsoft.com/zh-tw/50bf2a30-73b6-4126-a921-075fd6eec278)