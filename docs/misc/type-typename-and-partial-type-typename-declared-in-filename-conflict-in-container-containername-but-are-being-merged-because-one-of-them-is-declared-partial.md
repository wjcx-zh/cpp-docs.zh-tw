---
title: "在容器 &#39;&lt;容器名稱&gt;&#39; 中，類型 &#39;&lt;類型名稱&gt;&#39; 與 &#39;&lt;檔案名稱&gt;&#39; 中宣告的部分類型 &#39;&lt;類型名稱&gt;&#39; 相衝突，但將予以合併，因為其中一個已宣告為部分類型 | Microsoft Docs"
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
  - "vbc40047"
  - "bc40047"
helpviewer_keywords: 
  - "BC40047"
ms.assetid: 05f62dd9-f97d-4893-8904-76ecd2da474c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在容器 &#39;&lt;容器名稱&gt;&#39; 中，類型 &#39;&lt;類型名稱&gt;&#39; 與 &#39;&lt;檔案名稱&gt;&#39; 中宣告的部分類型 &#39;&lt;類型名稱&gt;&#39; 相衝突，但將予以合併，因為其中一個已宣告為部分類型
類別或結構出現在相同容器類型的多個定義中，而且多個定義未標記為 `Partial`。  
  
 您必須至少在類別或結構之多個定義中的其中一個定義上使用 [Partial](../Topic/Partial%20\(Visual%20Basic\).md) 關鍵字，但建議您將它用於所有部分定義上。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40047  
  
### 更正這個錯誤  
  
-   在類別或結構的每個部分定義上使用 [Partial](../Topic/Partial%20\(Visual%20Basic\).md) 關鍵字。