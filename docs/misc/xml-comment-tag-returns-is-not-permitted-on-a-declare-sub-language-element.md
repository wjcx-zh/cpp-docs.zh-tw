---
title: "&#39;declare sub&#39; 語言項目上不可使用 XML 註解標記 &#39;returns&#39; | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;declare sub&#39; 語言項目上不可使用 XML 註解標記 &#39;returns&#39;
'declare sub' 語言元素上不可使用 XML 註解標記 'returns'。 將會忽略 XML 註解。  
  
 `Declare Sub` 宣告的 XML 註解不能包含 `<`returns`>` 標記。  
  
 **錯誤 ID︰**BC42315  
  
### 更正這個錯誤  
  
-   請移除不支援的 `<`returns`>` 標記。  
  
## 請參閱  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML Comment Tags](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)   
 [Documenting Your Code with XML](../Topic/Documenting%20Your%20Code%20with%20XML%20\(Visual%20Basic\).md)   
 [Declare Statement](../Topic/Declare%20Statement.md)