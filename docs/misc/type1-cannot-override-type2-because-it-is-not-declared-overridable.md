---
title: "&#39;&lt;類型1&gt;&#39; 無法覆寫 &lt;類型2&gt;，因為其未宣告為 &#39;Overridable&#39; | Microsoft Docs"
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
  - "bc31086"
  - "vbc31086"
helpviewer_keywords: 
  - "BC31086"
ms.assetid: ce071994-2e32-4460-a65d-f48f914386c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型1&gt;&#39; 無法覆寫 &lt;類型2&gt;，因為其未宣告為 &#39;Overridable&#39;
衍生類別中的成員會覆寫未標記為 `Overridable` 修飾詞的基底類別成員。  
  
 **錯誤 ID︰**BC31086  
  
### 更正這個錯誤  
  
1.  將 `Overridable` 修飾詞加入基底類別中的覆寫成員。  
  
2.  使用 `Shadows` 關鍵字遮蔽基底類別中的項目。  
  
## 請參閱  
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)