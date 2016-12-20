---
title: "&#39;WriteOnly&#39; 屬性上不得使用 XML 註解標記 &#39;returns&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42313"
  - "bc42313"
helpviewer_keywords: 
  - "BC42313"
ms.assetid: 43dca605-187e-4b0b-b29f-5cc4dcdc5f9f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;WriteOnly&#39; 屬性上不得使用 XML 註解標記 &#39;returns&#39;
'WriteOnly' 屬性上不可使用 XML 註解標記 'returns'。 將會忽略 XML 註解。  
  
 唯寫屬性宣告的 XML 註解不能包含 \<returns\> 標記。  
  
 **錯誤 ID︰**BC42313  
  
### 更正這個錯誤  
  
-   請移除不支援的 \<returns\> 標記。  
  
## 請參閱  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML Comment Tags](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)   
 [Documenting Your Code with XML](../Topic/Documenting%20Your%20Code%20with%20XML%20\(Visual%20Basic\).md)   
 [Property Statement](../Topic/Property%20Statement.md)