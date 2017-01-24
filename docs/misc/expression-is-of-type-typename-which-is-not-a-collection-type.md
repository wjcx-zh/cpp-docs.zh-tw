---
title: "此運算式屬於類型 &#39;&lt;類型名稱&gt;&#39;，不是集合類型 | Microsoft Docs"
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
  - "bc32023"
  - "vbc32023"
helpviewer_keywords: 
  - "BC32023"
ms.assetid: d0f151be-6b65-498b-b571-03faf24df0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此運算式屬於類型 &#39;&lt;類型名稱&gt;&#39;，不是集合類型
`For Each` 陳述式中所指定的群組變數不是集合物件或陣列，而且其類型未實作 <xref:System.Collections.IEnumerable> 介面。 類型必須支援 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 集合設計模式，或實作 <xref:System.Collections.IEnumerable>。  
  
 **錯誤 ID：**BC32023  
  
### 更正這個錯誤  
  
-   將群組變數宣告為支援 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 集合設計或實作 <xref:System.Collections.IEnumerable> 的類別類型。  
  
## 請參閱  
 <xref:System.Collections.IEnumerable>   
 [For Each...Next 陳述式](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic Collection 類別](http://msdn.microsoft.com/zh-tw/0cb2d1ad-c58d-42c0-8e69-d81f5a15e532)