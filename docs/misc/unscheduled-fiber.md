---
title: "未排程的 Fiber | Microsoft Docs"
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
  - "bc30948"
  - "vbc30948"
helpviewer_keywords: 
  - "BC30948"
ms.assetid: 982bf6d2-ce62-4451-8a23-82dacf8ee100
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未排程的 Fiber
無法評估偵錯工具，因為它所在的邏輯 Fiber 在實際執行緒上未排程。 如果在使用 Fiber 的 SQL Server 上執行處理序，即可能會發生此情況。  
  
 Fiber 包含堆疊和暫存器內容，因此它可以在任何執行緒上執行。 Fiber 可以切出某個執行緒，並在稍後重新啟動不同的執行緒。  
  
 **錯誤 ID：**BC30948  
  
### 更正這個錯誤  
  
-   請確定 Fiber 有在實體執行緒上排程。  
  
## 請參閱  
 [Debugging SQL](http://msdn.microsoft.com/zh-tw/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Visual Studio 偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)