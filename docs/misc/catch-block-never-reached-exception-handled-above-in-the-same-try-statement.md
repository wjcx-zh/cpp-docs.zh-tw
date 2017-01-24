---
title: "一律不會執行到 &#39;Catch&#39; 區塊；&lt;例外狀況&gt; 會在相同 &#39;Try&#39; 陳述式的上方處理 | Microsoft Docs"
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
  - "bc42031"
  - "vbc42031"
helpviewer_keywords: 
  - "BC42031"
ms.assetid: 7d15597c-5988-42ea-a853-63cbf78faaf3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 一律不會執行到 &#39;Catch&#39; 區塊；&lt;例外狀況&gt; 會在相同 &#39;Try&#39; 陳述式的上方處理
無法到達程式碼中的 `Catch` 區塊，因為它已在前面的 `Try` 區塊中處理。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42031  
  
### 更正這個錯誤  
  
-   請移除多餘的陳述式。  
  
## 請參閱  
 [如何：在 Visual Basic 中攔截例外狀況](http://msdn.microsoft.com/zh-tw/f3063c89-d2bf-49b1-91b5-b87edfb18b95)   
 [如何：在 Visual Basic 的 Catch 區塊使用 Try... 測試程式碼](http://msdn.microsoft.com/zh-tw/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [如何：在 Visual Basic 中的 Catch 區塊中篩選錯誤](http://msdn.microsoft.com/zh-tw/85964d0a-56e7-4301-a96e-5eaea23b7b9b)   
 [逐步解說：結構化例外狀況處理 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/440da655-4b32-490b-8b16-bfe46f41fa76)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)