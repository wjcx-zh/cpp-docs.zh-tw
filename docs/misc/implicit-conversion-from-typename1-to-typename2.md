---
title: "從 &#39;&lt;類型名稱1&gt;&#39; 到 &#39;&lt;類型名稱2&gt;&#39; 的隱含轉換 | Microsoft Docs"
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
  - "vbc42016"
  - "BC42016"
helpviewer_keywords: 
  - "BC42016"
ms.assetid: 7dabaab0-8258-4c17-927f-28e61f50bd3a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 從 &#39;&lt;類型名稱1&gt;&#39; 到 &#39;&lt;類型名稱2&gt;&#39; 的隱含轉換
運算式或指派陳述式會接受一種資料類型的值，並將它轉換成另一種類型。 由於未使用任何轉換關鍵字，因此轉換是*隱含*的。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42016  
  
### 更正這個錯誤  
  
-   如果可能，請使用相同資料類型的值，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 便不需要執行任何轉換。  
  
-   請使用 `CType` 或其中一個轉換關鍵字，讓轉換為*「明確」*\(explicit\)。  
  
## 請參閱  
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)