---
title: "&#39;#Region&#39; 陳述式之後必須搭配相對應的 &#39;#End Region&#39; | Microsoft Docs"
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
  - "bc30681"
  - "vbc30681"
helpviewer_keywords: 
  - "BC30681"
ms.assetid: 05a0402b-da68-4ab8-b6d6-940379bc5973
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#Region&#39; 陳述式之後必須搭配相對應的 &#39;#End Region&#39;
使用 `#Region` 指示詞來指定程式碼區段，以在使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 程式碼編輯器的大綱功能時展開或摺疊。`#Region` 陳述式的開頭和結尾必須在相同的程式碼區塊中。  
  
 **錯誤 ID：**BC30681  
  
### 更正這個錯誤  
  
1.  請在 `#Region` 陳述式後面之程式碼的適當位置插入 `#End Region`。  
  
## 請參閱  
 [\#Region Directive](../Topic/%23Region%20Directive.md)