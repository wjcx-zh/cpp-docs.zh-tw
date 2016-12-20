---
title: "已不再支援 &#39;Line&#39; 陳述式 (智慧型裝置/Visual Basic 編譯器錯誤) | Microsoft Docs"
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
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 已不再支援 &#39;Line&#39; 陳述式 (智慧型裝置/Visual Basic 編譯器錯誤)
不再支援 `Line` 陳述式。 檔案 I\/O 功能通常提供為 <xref:Microsoft.VisualBasic.FileSystem.LineInput%2A?displayProperty=fullName>，但是 .NET Compact Framework 目標版本並不支援它。  
  
 **錯誤 ID︰**BC30768  
  
### 更正這個錯誤  
  
-   如果執行檔案存取，請使用 <xref:System.IO> 命名空間中定義的函式。  
  
-   如果執行圖形，請使用 <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>。  
  
## 請參閱  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [File Access with Visual Basic](../Topic/File%20Access%20with%20Visual%20Basic.md)