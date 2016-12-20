---
title: "陳述式不可出現在事件主體中 | Microsoft Docs"
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
  - "bc31112"
  - "vbc31112"
helpviewer_keywords: 
  - "BC31112"
ms.assetid: fd51fc53-a008-4b79-85fb-2d9fa1fb5a79
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陳述式不可出現在事件主體中
陳述式不可出現在事件主體中。 已假設是事件結尾。  
  
 在事件主體中不正確的陳述式出現在一個事件主體中。  
  
 **錯誤 ID︰**BC31112  
  
### 更正這個錯誤  
  
-   在陳述式之前加入 `End Event`。  
  
## 請參閱  
 [Application Events Sample](http://msdn.microsoft.com/zh-tw/289a787f-b97e-43c8-a304-fe95e45f4a0d)   
 [Event Statement](../Topic/Event%20Statement.md)