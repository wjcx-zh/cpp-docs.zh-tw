---
title: "&#39;On Error&#39; 陳述式在 &#39;Using&#39; 陳述式內無效。 | Microsoft Docs"
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
  - "vbc36013"
  - "bc36013"
helpviewer_keywords: 
  - "BC36013"
ms.assetid: 5b399bf9-6595-46e0-a808-378f6c28568b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;On Error&#39; 陳述式在 &#39;Using&#39; 陳述式內無效。
`On Error` 陳述式會出現在 `Using` 陳述式內，但在該內容中無效。  
  
 **錯誤識別碼：**BC36013  
  
### 更正這個錯誤  
  
-   在 `On Error` 陳述式的位置使用結構化的錯誤處理，例如 `Try…Catch` 區塊。  
  
## 請參閱  
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)   
 [選擇使用結構化和非結構化例外處理的時機 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/e897d7ca-07e8-45dd-8a6d-a5b2a2fc9b9a)   
 [On Error Statement](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)   
 [如何：在 Visual Basic 的 Catch 區塊使用 Try... 測試程式碼](http://msdn.microsoft.com/zh-tw/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)