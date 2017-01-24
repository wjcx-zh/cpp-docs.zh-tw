---
title: "在模組中不當使用 &lt;關鍵字&gt; 關鍵字 | Microsoft Docs"
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
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在模組中不當使用 &lt;關鍵字&gt; 關鍵字
模組沒有執行個體、支援繼承或實作介面。 因此，下列關鍵字不適用於模組宣告：  
  
-   [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)  
  
-   [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md)  
  
-   [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)  
  
-   [Private](../Topic/Private%20\(Visual%20Basic\).md)  
  
-   [Protected](../Topic/Protected%20\(Visual%20Basic\).md)  
  
-   [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)  
  
-   [Shared](../Topic/Shared%20\(Visual%20Basic\).md)  
  
-   [Static](../Topic/Static%20\(Visual%20Basic\).md)  
  
 [Module Statement](../Topic/Module%20Statement.md) 中唯一支援的關鍵字是 [Public](../Topic/Public%20\(Visual%20Basic\).md) 和 [Friend](../Topic/Friend%20\(Visual%20Basic\).md)。  
  
 此外，您不能在模組的陳述式區塊中使用 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md) 陳述式或 [Inherits Statement](../Topic/Inherits%20Statement.md)。  
  
 根據預設，這個訊息是一個警告。 如需如何隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42028  
  
### 更正這個錯誤  
  
-   如果您想要這個程式設計項目成為模組，請只在其宣告中使用 `Public` 或 `Friend` 關鍵字。 根據預設，如果未指定其存取層級，則模組會使用 `Friend`。  
  
-   如果您想要建立這個程式設計項目的執行個體，請將它宣告為類別。 然後，您可以使用套用至類別宣告的關鍵字。  
  
## 請參閱  
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)