---
title: "訊息傳送和接收 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項通知訊息"
  - "訊息 [C++], MFC"
  - "訊息 [C++], 接收"
  - "訊息 [C++], 傳送"
  - "MFC [C++], 訊息"
  - "Windows 訊息 [C++], 在 MFC 中處理"
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 訊息傳送和接收
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

考慮處理序所傳送的部分，這個框架如何反應。  
  
 大部分的訊息是由與程式的使用者互動。  命令會以在功能表項目或工具列按鈕的按一下滑鼠或由快速鍵按鍵。  使用者也會產生 Windows 訊息，例如，移動或調整視窗大小。  其他視窗訊息傳送事件時，例如程式啟動或結束時，會發生，當視窗取得或失去焦點時，依此類推。  控制項通知訊息由滑鼠點選或其他使用者互動產生與控制項，例如按鈕或清單方塊控制對話方塊。  
  
 類別的 `CWinApp` **Run** 成員函式來擷取訊息並將事件分派到適當的視窗。  大部分的命令訊息傳送到應用程式的主框架視窗。  由類別庫的 `WindowProc` 預先定義收到訊息並以不同的方式傳送它們，接收訊息的類別。  
  
 現在請考慮流程的接收的部分。  
  
 訊息的初始接收者必須是視窗物件。  Windows 訊息直接由該視窗物件通常處理。  命令訊息，通常來自應用程式的主框架視窗，會路由到 [命令路由](../mfc/command-routing.md)中所描述的命令目標鏈結。  
  
 每個物件可以接收訊息或命令的一組訊息或命令與其處理常式名稱的訊息對應。  
  
 當命令目標物件接收訊息或命令時，它會搜尋其訊息對應的符合項目。  如果它找到訊息的處理常式，它會呼叫處理常式。  如需訊息對應方式的詳細資訊搜尋，請參閱 [.NET Framework 搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)。  請參考這個的 [在 Framework 的命令](../mfc/user-interface-objects-and-command-ids.md)。  
  
## 請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)