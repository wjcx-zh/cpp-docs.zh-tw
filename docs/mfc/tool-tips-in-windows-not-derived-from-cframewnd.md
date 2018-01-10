---
title: "非衍生自 cframewnd 之視窗中的工具提示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c27126954f72eb4a075d0741b0ec0faec94f381c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>非衍生自 CFrameWnd 之視窗中的工具提示
本文章系列涵蓋啟用工具提示控制項的視窗中，不衍生自包含[CFrameWnd](../mfc/reference/cframewnd-class.md)。 發行項[工具列工具提示](../mfc/toolbar-tool-tips.md)提供中控制項的工具提示資訊`CFrameWnd`。  
  
 此系列的文章中涵蓋的主題包括：  
  
-   [啟用工具提示](../mfc/enabling-tool-tips.md)  
  
-   [處理工具提示的 TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [TOOLTIPTEXT 結構](../mfc/tooltiptext-structure.md)  
  
 工具提示會自動顯示按鈕與父視窗所包含的其他控制項衍生自`CFrameWnd`。 這是因為`CFrameWnd`具有預設處理常式，如[TTN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269)通知，用來處理**TTN_NEEDTEXT**通知從工具提示控制項與控制項相關聯。  
  
 不過，這個預設處理常式時，會不呼叫**TTN_NEEDTEXT**從控制項的視窗中，不是相關聯的工具提示控制項傳送通知`CFrameWnd`，例如控制項在對話方塊或表單檢視。 因此，則需要您提供的處理常式函式**TTN_NEEDTEXT**通知訊息，以顯示子控制項的工具提示。  
  
 為您的 windows 所提供的預設工具提示[CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)沒有與其相關聯的文字。 若要擷取要顯示的工具提示文字**TTN_NEEDTEXT**會顯示工具提示視窗之前，傳送通知給工具提示控制項的父視窗。 如果沒有指派至某些值，這個訊息處理常式**pszText**隸屬**TOOLTIPTEXT**結構，會有任何顯示的工具提示的文字。  
  
## <a name="see-also"></a>請參閱  
 [工具提示](../mfc/tool-tips.md)

