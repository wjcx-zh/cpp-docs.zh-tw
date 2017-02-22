---
title: "Run 成員函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinApp 類別, Run"
  - "CWinApp::Run 中的訊息幫浦"
  - "訊息, 迴圈"
  - "Run 方法, 訊息和閒置處理"
  - "WinMain 方法"
  - "WinMain 方法, 呼叫 CWinApp::Run"
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Run 成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

架構應用程式花費大部分的在 [CWinApp](../mfc/reference/cwinapp-class.md)類別的 [Run](../Topic/CWinApp::Run.md) 成員函式的時間。  在初始化之後，呼叫 `WinMain` **Run** 處理訊息迴圈。  
  
 **Run** 循環訊息迴圈，檢查訊息佇列中可用的訊息。  如果訊息是可用的， **Run** 分派它。  如果訊息都無法使用，通常是 true， **Run** 呼叫要做任何閒置時間的 `OnIdle` 管理或可能需要進行的架構。  如果沒有想要的訊息和無閒置處理，應用程式會等待，直到事情發生。  當應用程式結束時，呼叫 **Run** `ExitInstance`。  在 [OnIdle 成員函式](../mfc/onidle-member-function.md) 的圖表在訊息迴圈顯示順序。  
  
 訊息分派取決於某種特定訊息。  如需有關 詳細資訊，請參閱 [訊息和在 Framework 中的指令](../mfc/messages-and-commands-in-the-framework.md)。  
  
## 請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)