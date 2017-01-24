---
title: "OnCmdMsg 處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnCmdMsg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令傳送, OnCmdMsg 處理常式"
  - "處理常式"
  - "處理常式, OnCmdMessage"
  - "訊息, 傳送"
  - "OnCmdMessage 方法"
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OnCmdMsg 處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要完成命令路由，每個命令目標呼叫下命令目標的 `OnCmdMsg` 成員函式在序列中。  命令目標使用 `OnCmdMsg` 判斷它們是否可以處理命令和傳送至另一個命令目標，則無法處理它。  
  
 每個命令目標類別可能會覆寫 `OnCmdMsg` 成員函式。  覆寫讓每個類別傳送命令到特定的目標。  如 [標準命令路由](../mfc/command-routing.md)表所示，框架視窗，例如，永遠路由命令對其目前子視窗或檢視，。  
  
 `OnCmdMsg` 的預設 `CCmdTarget` 實作的每個命令訊息使用命令目標類別的訊息對應搜尋標準訊息被搜尋的收到—的處理函式相同。  如果找到符合的項目，便會呼叫處理常式。  訊息對應搜尋在 [.NET Framework 搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)中說明。  
  
## 請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)