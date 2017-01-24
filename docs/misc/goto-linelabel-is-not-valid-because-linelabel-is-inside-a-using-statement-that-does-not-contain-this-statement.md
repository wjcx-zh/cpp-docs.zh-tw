---
title: "&#39;GoTo &lt;行標籤&gt;&#39; 無效，因為 &#39;&lt;行標籤&gt;&#39; 位於不包含此陳述式的 &#39;Using&#39; 陳述式內 | Microsoft Docs"
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
  - "bc36009"
  - "vbc36009"
helpviewer_keywords: 
  - "BC36009"
ms.assetid: ebec3cac-d378-4e9b-a792-12e9ece5599e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;行標籤&gt;&#39; 無效，因為 &#39;&lt;行標籤&gt;&#39; 位於不包含此陳述式的 &#39;Using&#39; 陳述式內
在 `Using` 建構之外的 `GoTo` 陳述式嘗試分叉到建構內的行標籤。  
  
 從 `Using`...`End Using` 建構之外任意處分叉到建構內任意處是無效的。  
  
 **錯誤 ID︰**BC36009  
  
### 更正這個錯誤  
  
-   請將 `GoTo` 陳述式內的行標籤，變更為不在任何 `For`...`Next`、`For Each`...`Next`、`SyncLock`...`End SyncLock`、`Try`...`Catch`...`Finally`、`With`...`End With`或 `Using`...`End Using` 建構內的標籤。  
  
     \-或\-  
  
-   請完全移除 `GoTo` 陳述式。 您可以進入 `Using`...`End Using` 建構的唯一方式，是允許控制權傳遞給 `Using` 陳述式本身。  
  
## 請參閱  
 [GoTo Statement](../Topic/GoTo%20Statement.md)   
 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)