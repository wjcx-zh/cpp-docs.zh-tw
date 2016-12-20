---
title: "事件 &#39;&lt;事件名稱&gt;&#39; 遺漏 &#39;RaiseEvent&#39; 定義 | Microsoft Docs"
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
  - "vbc31132"
  - "bc31132"
helpviewer_keywords: 
  - "BC31132"
ms.assetid: 8f3442fd-2ed1-4dbc-83a8-f0860ec022ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件 &#39;&lt;事件名稱&gt;&#39; 遺漏 &#39;RaiseEvent&#39; 定義
如果事件宣告為 `Custom`，則必須提供引發事件的程序。  
  
 **錯誤 ID︰**BC31132  
  
### 更正這個錯誤  
  
1.  在 `Custom Event` 陳述式與 `End Event` 陳述式之間加入 `RaiseEvent` 宣告。  
  
2.  請確認已正確地終止事件宣告內的其他程序。  
  
## 請參閱  
 [RaiseEvent Statement](../Topic/RaiseEvent%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)