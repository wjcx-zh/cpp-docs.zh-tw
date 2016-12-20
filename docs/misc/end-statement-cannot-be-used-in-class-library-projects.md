---
title: "不可以在類別庫專案中使用 &#39;End&#39; 陳述式 | Microsoft Docs"
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
  - "bc30615"
  - "vbc30615"
helpviewer_keywords: 
  - "BC30615"
ms.assetid: c8606b17-b50b-4014-b76e-b748d57e9389
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不可以在類別庫專案中使用 &#39;End&#39; 陳述式
用來建立 DLL 的類別庫專案不允許使用 `End` 關鍵字來停止執行程序中的程式碼。  
  
 **錯誤 ID：**BC30615  
  
### 更正這個錯誤  
  
-   使用控制結構 \(例如 `While` 和 `For`\) 來控制程式執行流程。  
  
## 請參閱  
 [Control Flow](../Topic/Control%20Flow%20in%20Visual%20Basic.md)