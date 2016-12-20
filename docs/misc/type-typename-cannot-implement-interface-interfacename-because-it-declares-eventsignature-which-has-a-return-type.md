---
title: "&#39;&lt;類型名稱&gt;&#39; 類型無法實作介面 &#39;&lt;介面名稱&gt;&#39;，因為它宣告具有傳回類型的 &lt;事件簽章&gt; | Microsoft Docs"
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
  - "bc30945"
  - "vbc30945"
helpviewer_keywords: 
  - "BC30945"
ms.assetid: 4f26e71a-949d-4103-b565-35cc8e833d29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型名稱&gt;&#39; 類型無法實作介面 &#39;&lt;介面名稱&gt;&#39;，因為它宣告具有傳回類型的 &lt;事件簽章&gt;
類別或結構嘗試實作的介面，宣告會傳回值的事件。  
  
 Visual Basic 目前不支援宣告會傳回值的事件。  
  
 **錯誤 ID︰**BC30945  
  
### 更正這個錯誤  
  
-   請從類別或結構定義移除 `Implements` 陳述式，或實作不同的介面。  
  
## 請參閱  
 [不在組建中：事件和事件處理常式](http://msdn.microsoft.com/zh-tw/95074a0d-1cbc-4221-a95a-964185c7f962)   
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)