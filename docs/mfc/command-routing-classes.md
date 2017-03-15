---
title: "命令路由類別 | Microsoft Docs"
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
  - "vc.classes.command"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令傳送, 類別"
  - "MFC, 命令傳送"
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 命令路由類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者與應用程式互動來選取功能表或控制列按鈕具有滑鼠的，應用程式會將資訊從受影響的使用者介面物件加入至適當的命令目標物件。  從 `CCmdTarget` 取得的命令目標類別包括 [CWinApp](../mfc/reference/cwinapp-class.md)、 [CWnd](../mfc/reference/cwnd-class.md)、 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)、 [CDocument](../mfc/reference/cdocument-class.md)、 [CView](../mfc/reference/cview-class.md)和從其衍生的類別。  架構支援自動命令路由命令，以便可以由最適當的物件處理目前作用中的應用程式。  
  
 類別 `CCmdUI` 物件傳遞給命令目標的更新命令 UI \([ON\_UPDATE\_COMMAND\_UI](../Topic/ON_UPDATE_COMMAND_UI.md)\) 處理常式可讓您更新使用者介面的狀態特定命令 \(例如，從功能表項目核取或移除檢查\)。  您呼叫 `CCmdUI` 物件的成員函式來更新 UI 物件的狀態。  這個程序是相同的 UI 物件與特定命令是功能表項目或按鈕 \(或兩者\)。  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 做為類別的基底類別 \(Base Class\) 可以接收和回應訊息物件的所有類別。  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 為更新使用者介面物件的程式設計介面 \(例如功能表項目或控制列按鈕。  命令目標物件啟用，停用，檢查，及\/或清除與這個物件的使用者介面物件。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)