---
title: "非衍生自 CFrameWnd 之視窗中的工具提示 | Microsoft Docs"
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
  - "控制項 [MFC], 工具提示"
  - "啟用工具提示"
  - "處理函式, 工具提示"
  - "說明, 控制項的工具提示"
  - "TOOLTIPTEXT 結構"
  - "TTN_NEEDTEXT 訊息"
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 非衍生自 CFrameWnd 之視窗中的工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文章系列涵蓋啟用從 [CFrameWnd](../mfc/reference/cframewnd-class.md)不是衍生自的視窗包含的控制項的工具提示。  這篇文章 [工具列工具提示](../mfc/toolbar-tool-tips.md) 做為 `CFrameWnd`中的控制項提供工具提示的資訊。  
  
 本文章系列中包含的主題:  
  
-   [啟用工具提示](../mfc/enabling-tool-tips.md)  
  
-   [工具提示的處理 TTN\_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [TOOLTIPTEXT 結構](../mfc/tooltiptext-structure.md)  
  
 工具提示的按鈕和其他控制項的自動顯示在衍生自 `CFrameWnd`的父視窗。  這是因為， `CFrameWnd` 有 [TTN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269) 通知的預設處理常式，處理從工具提示控制項 **TTN\_NEEDTEXT** 告知與控制項。  
  
 不過，此預設處理常式未呼叫，在 **TTN\_NEEDTEXT** 通知從工具提示控制項傳送與不是 `CFrameWnd`時的視窗的控制項，例如在對話方塊或表單檢視的控制項。  因此，對於 **TTN\_NEEDTEXT** 通知訊息提供處理函式以顯示子控制項的工具提示您是必要的。  
  
 為您的 Windows 提供的預設工具提示由 [CWnd::EnableToolTips](../Topic/CWnd::EnableToolTips.md) 沒有文字相關聯的量值。  在工具提示視窗中顯示之前，要擷取的工具提示文字，可以顯示 **TTN\_NEEDTEXT** 通知傳送給工具提示控制項的父視窗。  如果沒有這個訊息的處理常式可以指定某些值對 **TOOLTIPTEXT** 結構的 **pszText** 成員，將不會為工具提示所顯示的文字。  
  
## 請參閱  
 [工具提示](../mfc/tool-tips.md)