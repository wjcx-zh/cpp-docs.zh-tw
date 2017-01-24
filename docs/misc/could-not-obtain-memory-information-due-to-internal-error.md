---
title: "由於內部錯誤，無法取得記憶體資訊 | Microsoft Docs"
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
  - "vbrDiagnosticInfo_Memory"
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 由於內部錯誤，無法取得記憶體資訊
呼叫 `My.Computer.Info` 物件的其中一個記憶體資訊屬性失敗。  
  
### 更正這個錯誤  
  
-   在 `My.Computer.Info` 物件之記憶體資訊屬性的呼叫周圍加入 `Try...Catch` 區塊。  
  
## 請參閱  
 [My.Computer.Info Object](../Topic/My.Computer.Info%20Object.md)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)