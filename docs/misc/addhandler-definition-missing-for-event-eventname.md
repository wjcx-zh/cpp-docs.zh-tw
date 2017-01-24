---
title: "事件 &#39;&lt;事件名稱&gt;&#39; 遺漏 &#39;AddHandler&#39; 定義 | Microsoft Docs"
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
  - "bc31130"
  - "vbc31130"
helpviewer_keywords: 
  - "BC31130"
ms.assetid: cf6c7fd6-ce2e-4916-b427-2a4a63e7279d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件 &#39;&lt;事件名稱&gt;&#39; 遺漏 &#39;AddHandler&#39; 定義
如果事件宣告為 `Custom`，則必須提供用於加入事件處理常式的程序。  
  
 **錯誤 ID︰**BC31130  
  
### 更正這個錯誤  
  
1.  在 `Custom Event` 陳述式與 `End Event` 陳述式之間加入 `AddHandler` 宣告。  
  
2.  請確認已正確地終止事件宣告內的其他程序。  
  
## 請參閱  
 [AddHandler Statement](../Topic/AddHandler%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)