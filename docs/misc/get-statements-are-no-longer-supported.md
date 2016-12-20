---
title: "不再支援 &#39;Get&#39; 陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30829"
  - "bc30829"
helpviewer_keywords: 
  - "BC30829"
ms.assetid: 8d798357-7efb-4423-9808-8b20777b97ba
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不再支援 &#39;Get&#39; 陳述式
不再支援 `Get` 陳述式。 檔案 I\/O 功能可以在 `Microsoft.VisualBasic` 命名空間中使用。  
  
 `Get` 不受檔案作業的支援，只能用於屬性程序語法。  
  
 **錯誤 ID︰**BC30829  
  
### 更正這個錯誤  
  
1.  使用 `System.IO`、`FileSystemObject` 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 執行階段函式的成員來執行檔案作業。  
  
## 請參閱  
 [Processing Drives, Directories, and Files](../Topic/Processing%20Drives,%20Directories,%20and%20Files%20\(Visual%20Basic\).md)   
 [Get Statement](../Topic/Get%20Statement.md)   
 [File Access with Visual Basic](../Topic/File%20Access%20with%20Visual%20Basic.md)