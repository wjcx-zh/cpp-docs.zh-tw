---
title: "&#39;&lt;事件名稱&gt;&#39; 隱含定義 &#39;&lt;成員名稱&gt;&#39;，其與 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中隱含宣告的成員互相衝突 | Microsoft Docs"
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
  - "bc31059"
  - "vbc31059"
helpviewer_keywords: 
  - "BC31059"
ms.assetid: 60ddb2f4-a204-41eb-b13b-b2bb13ddb69c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;事件名稱&gt;&#39; 隱含定義 &#39;&lt;成員名稱&gt;&#39;，其與 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中隱含宣告的成員互相衝突
類型成員名稱與為事件隱含建立的成員名稱相衝突。 事件會隱含建立數個變數。 例如，宣告 `Event X` 會隱含宣告名稱 `XEventHandler`、`XEvent`、`add_X` 和 `remove_X`。  
  
 **錯誤 ID︰**BC31059  
  
### 更正這個錯誤  
  
-   請重新命名明確宣告的成員，以移除命名衝突。  
  
## 請參閱  
 [NotInBuild：Visual Basic 中的 Declaration 陳述式](http://msdn.microsoft.com/zh-tw/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)