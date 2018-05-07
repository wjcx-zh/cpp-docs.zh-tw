---
title: 控制列類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.control
dev_langs:
- C++
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4974b7ba3b71e60b8edf2a73ea5f06fab64ddfb7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="control-bar-classes"></a>控制列類別
控制列會附加至框架視窗。 它們包含按鈕、 狀態窗格或對話方塊範本。 自由浮動控制列，也稱為工具板由附加至這些[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)物件。  
  
## <a name="framework-control-bars"></a>架構控制列  
 這些控制列是 MFC 架構中不可或缺的一部分。 它們是容易使用且更強大，比 Windows 控制列，因為它們會整合的架構。 大部分的 MFC 應用程式使用這些控制列，而不是 Windows 控制列。  
  
 [CControlBar](../mfc/reference/ccontrolbar-class.md)  
 本章節所列的 MFC 控制列基底類別。 控制列是對齊框架視窗邊緣的視窗。 控制列包含`HWND`-根據子控制項或控制項不根據`HWND`，例如工具列按鈕。  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 控制列對話方塊範本為基礎。  
  
 [CReBar](../mfc/reference/crebar-class.md)  
 支援可包含控制項的表單中的其他子視窗的工具列。  
  
 [CToolBar](../mfc/reference/ctoolbar-class.md)  
 工具列控制項不包含點陣圖命令按鈕的 windows `HWND`。 大部分的 MFC 應用程式使用這個類別而非`CToolBarCtrl`。  
  
 [CStatusBar](../mfc/reference/cstatusbar-class.md)  
 狀態列控制項 windows 基底類別。 大部分的 MFC 應用程式使用這個類別而非`CStatusBarCtrl`。  
  
## <a name="windows-control-bars"></a>Windows 控制列  
 這些控制項長條是對應的 Windows 控制項的精簡型包裝函式。 是，因為它們不會整合的架構，很難使用與先前所列的控制列。 大部分的 MFC 應用程式會使用先前所列的控制列。  
  
 [CRebarCtrl](../mfc/reference/crebarctrl-class.md)  
 實作的內部控制`CRebar`物件。  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 水平視窗中，通常會分成的窗格，在其中應用程式可以顯示狀態資訊。  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具列通用控制項的功能。  
  
## <a name="related-classes"></a>相關的類別  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 小型快顯視窗顯示單行說明應用程式中工具用途的文字。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 處理永續性儲存體的停駐控制列的狀態資料。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../mfc/class-library-overview.md)

