---
title: "&#39;&lt;規範&gt;&#39; 在介面屬性宣告中無效 | Microsoft Docs"
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
  - "vbc30273"
  - "bc30273"
helpviewer_keywords: 
  - "BC30273"
ms.assetid: f10c4f5f-6176-4dba-99a9-b58f3b390fba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;規範&gt;&#39; 在介面屬性宣告中無效
介面內的 `Property` 陳述式包含無效的關鍵字，例如 `Implements`。 介面只會定義成員，無法實作它們。  
  
 **錯誤 ID︰**BC30273  
  
### 更正這個錯誤  
  
-   請從宣告陳述式中移除無效的關鍵字。  
  
-   請將介面成員實作移至實作介面的類別。  
  
## 請參閱  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)