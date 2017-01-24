---
title: "事件 &#39;&lt;事件名稱&gt;&#39; 遺漏 &#39;RemoveHandler&#39; 定義 | Microsoft Docs"
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
  - "bc31131"
  - "vbc31131"
helpviewer_keywords: 
  - "BC31131"
ms.assetid: 0ef68daf-b66e-4ecf-bf2c-dcacabd8aa3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件 &#39;&lt;事件名稱&gt;&#39; 遺漏 &#39;RemoveHandler&#39; 定義
如果事件宣告為 `Custom`，則必須提供用於移除事件處理常式的程序。  
  
 **錯誤 ID︰**BC31131  
  
### 更正這個錯誤  
  
1.  在 `Custom Event` 陳述式與 `End Event` 陳述式之間加入 `RemoveHandler` 宣告。  
  
2.  請確認已正確地終止事件宣告內的其他程序。  
  
## 請參閱  
 [RemoveHandler Statement](../Topic/RemoveHandler%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)