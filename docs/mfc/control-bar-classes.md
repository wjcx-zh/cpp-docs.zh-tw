---
title: 控制列類別
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: a050c5d2f7396324c2c380a03fc28e01ab992208
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440958"
---
# <a name="control-bar-classes"></a>控制列類別

控制列會附加至框架視窗。 其中包含按鈕、狀態窗格或對話方塊範本。 自由浮動的控制列（也稱為工具調板）是藉由將它們附加至[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)物件來執行。

## <a name="framework-control-bars"></a>架構控制列

這些控制列是 MFC 架構不可或缺的一部分。 它們比較容易使用，而且比 Windows 控制列更強大，因為它們已與架構整合。 大部分的 MFC 應用程式會使用這些控制列，而不是 Windows 控制列。

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
本節列出之 MFC 控制列的基類。 控制列是對齊框架視窗邊緣的視窗。 控制列包含以 `HWND`為基礎的子控制項或不是以 `HWND`為基礎的控制項，例如工具列按鈕。

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
以對話方塊範本為基礎的控制列。

[CReBar](../mfc/reference/crebar-class.md)<br/>
支援可以包含控制項形式之其他子視窗的工具列。

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
包含不是以 `HWND`為基礎之點陣圖命令按鈕的工具列控制項視窗。 大部分的 MFC 應用程式會使用這個類別，而不是 `CToolBarCtrl`。

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
狀態列控制項視窗的基類。 大部分的 MFC 應用程式會使用這個類別，而不是 `CStatusBarCtrl`。

## <a name="windows-control-bars"></a>Windows 控制列

這些控制列是適用于對應之 Windows 控制項的精簡型包裝函式。 因為它們並未與架構整合，所以比先前列出的控制列更難使用它們。 大部分的 MFC 應用程式會使用先前列出的控制列。

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
執行 `CRebar` 物件的內部控制項。

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
水準視窗（通常分成窗格），應用程式可以在其中顯示狀態資訊。

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具列通用控制項的功能。

## <a name="related-classes"></a>相關類別

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
一個小型快顯視窗，會在應用程式中顯示一個描述工具用途的單行文字。

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
處理控制列銜接狀態資料的持續性儲存。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
