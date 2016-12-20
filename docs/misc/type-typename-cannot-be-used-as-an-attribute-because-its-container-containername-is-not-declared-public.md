---
title: "無法在屬性中使用類型 &#39;&lt;類型名稱&gt;&#39;，因為其容器 &#39;&lt;容器類型&gt;&#39; 未宣告為 &#39;Public&#39; | Microsoft Docs"
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
  - "bc31517"
  - "vbc31517"
helpviewer_keywords: 
  - "BC31517"
ms.assetid: 3d1a8f41-8652-4e37-a6bd-40b0ad306c6f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法在屬性中使用類型 &#39;&lt;類型名稱&gt;&#39;，因為其容器 &#39;&lt;容器類型&gt;&#39; 未宣告為 &#39;Public&#39;
未使用 `Public` 修飾詞來宣告在其中定義這個屬性的類別或模組。 未指定存取修飾詞的類別和模組預設會宣告為 `Friend`。  
  
 **錯誤 ID：**BC31517  
  
### 更正這個錯誤  
  
1.  將 `Public` 修飾詞加入在其中定義這個屬性的類別或模組。  
  
## 請參閱  
 [Public](../Topic/Public%20\(Visual%20Basic\).md)