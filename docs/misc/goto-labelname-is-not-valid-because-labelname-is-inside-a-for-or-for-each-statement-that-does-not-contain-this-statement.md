---
title: "&#39;GoTo &lt;標籤名稱&gt;&#39; 無效，因為 &lt;標籤名稱&gt; 位於不包含這個陳述式的 &#39;For&#39; 或 &#39;For Each&#39; 陳述式內部 | Microsoft Docs"
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
  - "vbc30757"
  - "bc30757"
helpviewer_keywords: 
  - "BC30757"
ms.assetid: be28bec5-1bc4-4da1-ba0c-4e3faac81077
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;標籤名稱&gt;&#39; 無效，因為 &lt;標籤名稱&gt; 位於不包含這個陳述式的 &#39;For&#39; 或 &#39;For Each&#39; 陳述式內部
`GoTo` 陳述式只能在目前的程式碼區塊內跳躍。  
  
 **錯誤 ID︰**BC30757  
  
### 更正這個錯誤  
  
-   請重建您的程式碼，讓 `GoTo` 陳述式和標籤都位在 `For` 區塊內。  
  
## 請參閱  
 [GoTo Statement](../Topic/GoTo%20Statement.md)   
 [For \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/c470a263-9b49-4308-8fd6-8592b84a7980)