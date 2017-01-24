---
title: "&#39;SyncLock&#39; 運算元不能屬於類型 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;&lt;類型名稱&gt;&#39; 不是參考類型 | Microsoft Docs"
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
  - "vbc30582"
  - "bc30582"
helpviewer_keywords: 
  - "BC30582"
ms.assetid: 953aecf2-629a-4272-94bd-abf88f785e63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;SyncLock&#39; 運算元不能屬於類型 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;&lt;類型名稱&gt;&#39; 不是參考類型
`SyncLock` 陳述式允許在單一運算式上同步處理陳述式，方法是確定多個執行緒不會同時執行相同的陳述式。`SyncLock` 陳述式中的運算式類型必須是參考類型 \(例如類別、模組、介面、陣列或委派\)。  
  
 **錯誤 ID︰**BC30582  
  
### 更正這個錯誤  
  
-   請將類型變更為適當的參考類型。  
  
## 請參閱  
 [SyncLock Statement](../Topic/SyncLock%20Statement.md)   
 [不在組建中：Visual Basic 中的多執行緒處理](http://msdn.microsoft.com/zh-tw/c731a50c-09c1-4468-9646-54c86b75d269)