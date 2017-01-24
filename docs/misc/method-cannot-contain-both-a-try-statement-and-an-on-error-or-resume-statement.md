---
title: "方法不可以同時包含 &#39;Try&#39; 陳述式以及 &#39;On Error&#39; 或 &#39;Resume&#39; 陳述式 | Microsoft Docs"
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
  - "vbc30544"
  - "bc30544"
helpviewer_keywords: 
  - "BC30544"
ms.assetid: 1e75d5fe-9a6b-43c2-9749-1f2d7ce5b10d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法不可以同時包含 &#39;Try&#39; 陳述式以及 &#39;On Error&#39; 或 &#39;Resume&#39; 陳述式
您已搭配 `On Error` 或 `Resume` 使用 `Try` 陳述式。  
  
 **錯誤 ID︰**BC30544  
  
### 更正這個錯誤  
  
1.  移除 `On Error` 或 `Resume`。  
  
## 請參閱  
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)