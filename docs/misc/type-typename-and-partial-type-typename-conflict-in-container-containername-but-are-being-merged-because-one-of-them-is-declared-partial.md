---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 和部分類型 &#39;&lt;類型名稱&gt;&#39; 在容器 &#39;&lt;容器名稱&gt;&#39; 中產生衝突，但是因為其中一個宣告為部分，所以正在進行合併 | Microsoft Docs"
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
  - "bc40046"
  - "vbc40046"
helpviewer_keywords: 
  - "BC40046"
ms.assetid: c243e70b-ecd5-49ef-a260-a7bb12a4a3b1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 和部分類型 &#39;&lt;類型名稱&gt;&#39; 在容器 &#39;&lt;容器名稱&gt;&#39; 中產生衝突，但是因為其中一個宣告為部分，所以正在進行合併
類別或結構出現在相同容器類型的多個定義中，而且多個定義未標記為 `Partial`。  
  
 您必須至少在類別或結構之多個定義中的其中一個定義上使用 [Partial](../Topic/Partial%20\(Visual%20Basic\).md) 關鍵字，但建議您將它用於所有部分定義上。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40046  
  
### 更正這個錯誤  
  
-   在類別或結構的每個部分定義上使用 [Partial](../Topic/Partial%20\(Visual%20Basic\).md) 關鍵字。  
  
## 請參閱  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)