---
title: "&lt;類型1&gt; &#39;&lt;成員名稱&gt;&#39; 與基底類別 &lt;類型3&gt; &#39;&lt;classname&gt;&#39; 上的 &lt;類型2&gt; &#39;&lt;成員名稱&gt;&#39; 衝突，應該宣告為 &#39;Shadows&#39; | Microsoft Docs"
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
  - "bc40004"
  - "vbc40004"
helpviewer_keywords: 
  - "BC40004"
ms.assetid: 24d10f31-3b3d-448c-b928-fc937e1f4a92
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;類型1&gt; &#39;&lt;成員名稱&gt;&#39; 與基底類別 &lt;類型3&gt; &#39;&lt;classname&gt;&#39; 上的 &lt;類型2&gt; &#39;&lt;成員名稱&gt;&#39; 衝突，應該宣告為 &#39;Shadows&#39;
宣告的程式設計項目與基底類別中所定義的項目同名。 在這種情況下，這個類別中的項目應該會遮蔽基底類別項目。  
  
 這個訊息是一個警告。 預設會假設為 `Shadows`。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40004  
  
### 更正這個錯誤  
  
-   將 `Shadows` 關鍵字加入宣告中，或變更所宣告項目的名稱。  
  
## 請參閱  
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)