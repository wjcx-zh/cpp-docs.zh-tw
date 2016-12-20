---
title: "已不再支援 &#39;Get&#39; 陳述式 (Visual Basic) | Microsoft Docs"
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
  - "vbc30767"
  - "bc30767"
helpviewer_keywords: 
  - "BC30767"
ms.assetid: 6aa62dcc-99aa-4051-a81e-3bbb6a8c355f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 已不再支援 &#39;Get&#39; 陳述式 (Visual Basic)
不再支援 `Get` 陳述式。 檔案 I\/O 功能通常是在 `Microsoft.VisualBasic` 命名空間中，但是目標 .NET Compact Framework 版本並不支援它。  
  
 **錯誤 ID：**BC30767  
  
### 更正這個錯誤  
  
-   使用 <xref:System.IO> 命名空間中所定義的函式來執行檔案作業。  
  
## 請參閱  
 <xref:System.IO>   
 [Get Statement](../Topic/Get%20Statement.md)   
 [File Access with Visual Basic](../Topic/File%20Access%20with%20Visual%20Basic.md)