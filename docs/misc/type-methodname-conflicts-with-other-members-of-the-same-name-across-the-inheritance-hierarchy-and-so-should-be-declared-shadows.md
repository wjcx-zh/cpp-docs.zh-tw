---
title: "&lt;類型&gt; &#39;&lt;方法名稱&gt;&#39; 與繼承階層中的其他同名成員互相衝突，因此應該宣告為 &#39;Shadows&#39; | Microsoft Docs"
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
  - "vbc42000"
  - "bc42000"
helpviewer_keywords: 
  - "BC42000"
ms.assetid: 3081635f-99a9-4e90-997f-82251144d80f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;類型&gt; &#39;&lt;方法名稱&gt;&#39; 與繼承階層中的其他同名成員互相衝突，因此應該宣告為 &#39;Shadows&#39;
繼承自兩個或多個介面的介面會定義程序時使用的名稱，和已在多個基底介面中定義的程序名稱相同。 這個介面中的程序應該會遮蔽其中一個基底介面程序。  
  
 這個訊息是一個警告。 預設會假設為 `Shadows`。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID：**BC42000  
  
### 更正這個錯誤  
  
-   如果您想要隱藏其中一個基底介面程序，請將 `Shadows` 關鍵字加入新程序宣告中。  
  
-   如果您不想要隱藏任何基底介面程序，請變更新程序的名稱。  
  
## 請參閱  
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)