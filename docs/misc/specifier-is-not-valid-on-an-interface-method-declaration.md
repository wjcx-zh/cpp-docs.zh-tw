---
title: "&#39;&lt;規範&gt;&#39; 在介面方法宣告中無效 | Microsoft Docs"
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
  - "bc30270"
  - "vbc30270"
helpviewer_keywords: 
  - "BC30270"
ms.assetid: 598f2944-3e5d-4686-b6f7-2b4bcaf5c211
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;規範&gt;&#39; 在介面方法宣告中無效
介面內的 `Function` 或 `Sub` 陳述式包含無效的關鍵字，例如 `Implements`。 介面只會定義成員，無法實作它們。  
  
 **錯誤識別碼：**BC30270  
  
### 更正這個錯誤  
  
1.  請從宣告陳述式中移除無效的關鍵字。  
  
2.  請將介面成員實作移至實作介面的類別。  
  
## 請參閱  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)