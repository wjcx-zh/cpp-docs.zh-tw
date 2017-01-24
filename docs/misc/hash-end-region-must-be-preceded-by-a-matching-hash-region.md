---
title: "&#39;#End Region&#39; 之前必須搭配相對應的 &#39;#Region&#39; | Microsoft Docs"
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
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End Region&#39; 之前必須搭配相對應的 &#39;#Region&#39;
透過 `#Region`，您可以在使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 程式碼編輯器的大綱功能時，指定要展開或摺疊程式碼區塊。`#Region` 陳述式的開頭和結尾必須在相同的程式碼區塊中。  
  
 **錯誤 ID：**BC30680  
  
### 更正這個錯誤  
  
-   請在對應 `#End``Region` 陳述式之前的適當位置插入 `#Region`。  
  
## 請參閱  
 [\#Region Directive](../Topic/%23Region%20Directive.md)