---
title: "&#39;SyncLock&#39; 陳述式中的 &#39;On Error&#39; 陳述式無效 | Microsoft Docs"
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
  - "bc30752"
  - "vbc30752"
helpviewer_keywords: 
  - "BC30752"
ms.assetid: 5c726627-b0fc-4edf-bd29-a83a0009f44d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;SyncLock&#39; 陳述式中的 &#39;On Error&#39; 陳述式無效
`On Error` 陳述式不能用於 `SyncLock` 區塊中，因為它們會干擾執行緒同步處理。  
  
 **錯誤識別碼：**BC30752  
  
### 更正這個錯誤  
  
1.  將 `On Error` 陳述式放在 `SyncLock` 區塊之外。  
  
## 請參閱  
 [On Error Statement](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)