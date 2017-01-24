---
title: "呼叫更新處理常式的時機 | Microsoft Docs"
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
  - "命令傳送, 更新命令"
  - "命令傳送, 更新處理常式"
  - "停用功能表項目"
  - "停用工具列按鈕"
  - "功能表項目, 啟用"
  - "功能表 [C++], 初始化"
  - "功能表 [C++], 更新為內容變更"
  - "工具列按鈕 [C++], 啟用"
  - "工具列控制項 [MFC], OnIdle 方法期間更新的"
  - "工具列 [C++], 更新"
  - "更新處理常式"
  - "更新處理常式, 呼叫"
  - "更新使用者介面物件"
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 呼叫更新處理常式的時機
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

假設使用者按一下檔案功能表上方時，產生 `WM_INITMENUPOPUP` 訊息。  框架的更新機制共同更新檔案功能表上的所有項目，在功能表下拉前，因此使用者可以看到它。  
  
 若要這樣做，框架路由更新所有功能表項目的命令在沿標準命令路由的快顯功能表。  在路由的命令目標有機會可以比更新命令以適當的訊息對應項目 \(格式為 `ON_UPDATE_COMMAND_UI`\) 和呼叫「更新處理常式」函式更新所有功能表項目。  因此，為有六個功能表項目的功能表，六更新命令已送出。  如果更新處理常式為功能表項目的命令識別碼存在，則會進行更新。  否則，架構會檢查處理常式的存在該命令 ID 的並啟用或停用功能表項目屬性。  
  
 在命令路由期間，如果此框架沒找到一個 `ON_UPDATE_COMMAND_UI` 項目，它會自動啟用使用者介面物件是否有 `ON_COMMAND` 輸入某個相同的命令 ID.  否則，它會停用使用者介面物件。  因此，確保使用者介面物件時，請提供命令的處理常式物件產生或提供其新處理常式。  請參閱本主題稍後 [使用者介面物件和命令 ID。](../mfc/user-interface-objects-and-command-ids.md)的圖表。  
  
 停用使用者介面物件預設不是可能的。  如需詳細資訊，請參閱*MFC 參考* 中`CFrameWnd`類別的 [m\_bAutoMenuEnable](../Topic/CFrameWnd::m_bAutoMenuEnable.md) 成員函式。  
  
 當應用程式發生收到 `WM_INITMENUPOPUP` 訊息時，功能表使用為自動在架構中。  在閒置迴圈期間，架構搜尋命令傳送按鈕更新處理常式，以與它為功能表類似的方式進行。  
  
## 請參閱  
 [如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)