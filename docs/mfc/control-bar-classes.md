---
title: 控制列類別 |Microsoft Docs
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
ms.openlocfilehash: 13fe4cd9cc483bccde6a342ef224dfbafab36eca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378551"
---
# <a name="control-bar-classes"></a>控制列類別

控制列會附加至框架視窗。 它們包含按鈕、 狀態窗格或對話方塊範本。 自由浮動的控制列，也稱為工具板由附加至這些[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)物件。

## <a name="framework-control-bars"></a>架構控制列

這些控制列是 MFC 架構中不可或缺的一部分。 它們是容易使用且更強大，比 Windows 控制列，因為它們與 framework 整合。 大部分的 MFC 應用程式會使用這些控制列，而不是 Windows 控制列。

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
在本節中所列的 MFC 控制列基底類別。 一種控制列是對齊框架視窗邊緣的視窗。 控制列包含`HWND`-根據子控制項或控制項不根據`HWND`，例如工具列按鈕。

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
控制列以對話方塊範本為基礎。

[CReBar](../mfc/reference/crebar-class.md)<br/>
支援可包含控制項的表單中的其他子視窗的工具列。

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
不包含點陣圖命令按鈕的工具列控制項視窗根據`HWND`。 大部分的 MFC 應用程式使用這個類別而非`CToolBarCtrl`。

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
狀態列控制項 windows 基底類別。 大部分的 MFC 應用程式使用這個類別而非`CStatusBarCtrl`。

## <a name="windows-control-bars"></a>Windows 控制列

這些控制列是精簡型包裝函式對應的 Windows 控制項。 因為它們不與 framework 整合，則它們很難是比先前所列的控制列。 大部分的 MFC 應用程式會使用先前所列的控制列。

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
實作的內部控制`CRebar`物件。

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
水平的視窗中，通常會分成的窗格中，應用程式可以在其中顯示狀態資訊。

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具列通用控制項的功能。

## <a name="related-classes"></a>相關的類別

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
小型快顯視窗會顯示一行文字，描述應用程式中工具用途。

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
處理停駐控制列的狀態資料的永續性儲存的體。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

