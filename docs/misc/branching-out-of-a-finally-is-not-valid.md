---
title: "&#39;Finally&#39; 的分支無效 | Microsoft Docs"
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
  - "bc30101"
  - "vbc30101"
helpviewer_keywords: 
  - "BC30101"
ms.assetid: 16a0dc29-3657-4373-b77f-38f3cb80e6c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; 的分支無效
`Finally` 區塊內的 `GoTo` 陳述式分叉到區塊之外。 分叉進入或離開 `Catch` 或 `Finally` 區塊是無效的。  
  
 **錯誤 ID︰**BC30101  
  
### 更正這個錯誤  
  
-   請移除 `GoTo` 陳述式，並考慮使用決策或迴圈控制結構來實作程式邏輯。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [GoTo Statement](../Topic/GoTo%20Statement.md)   
 [Control Flow](../Topic/Control%20Flow%20in%20Visual%20Basic.md)