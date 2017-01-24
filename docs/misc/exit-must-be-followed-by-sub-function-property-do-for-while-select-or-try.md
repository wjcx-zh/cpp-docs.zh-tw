---
title: "&#39;Exit&#39; 必須在 &#39;Sub&#39;、&#39;Function&#39;、&#39;Property&#39;、&#39;Do&#39;、&#39;For&#39;、&#39;While&#39;、&#39;Select&#39; 或 &#39;Try&#39; 之前 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30240"
  - "vbc30240"
helpviewer_keywords: 
  - "BC30240"
ms.assetid: 91078689-f4bf-4331-a475-10bc9fe7cd0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit&#39; 必須在 &#39;Sub&#39;、&#39;Function&#39;、&#39;Property&#39;、&#39;Do&#39;、&#39;For&#39;、&#39;While&#39;、&#39;Select&#39; 或 &#39;Try&#39; 之前
`Exit` 陳述式包含無效的關鍵字。`Exit` 必須指定區塊，以將其中的控制項轉移到區塊後面的陳述式，例如 `End While`。  
  
 **錯誤 ID︰**BC30240  
  
### 更正這個錯誤  
  
-   在 `Exit` 後面加入有效的關鍵字，或移除 `Exit` 陳述式。  
  
## 請參閱  
 [Exit Statement](../Topic/Exit%20Statement%20\(Visual%20Basic\).md)