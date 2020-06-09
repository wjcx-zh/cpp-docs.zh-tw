---
title: 控制列類別
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: f89770683edb1f4268b4f19adb74e5c08aa5f109
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620519"
---
# <a name="control-bar-classes"></a>控制列類別

控制列會附加至框架視窗。 其中包含按鈕、狀態窗格或對話方塊範本。 自由浮動的控制列（也稱為工具調板）是藉由將它們附加至[CMiniFrameWnd](reference/cminiframewnd-class.md)物件來執行。

## <a name="framework-control-bars"></a>架構控制列

這些控制列是 MFC 架構不可或缺的一部分。 它們比較容易使用，而且比 Windows 控制列更強大，因為它們已與架構整合。 大部分的 MFC 應用程式會使用這些控制列，而不是 Windows 控制列。

[CControlBar](reference/ccontrolbar-class.md)<br/>
本節列出之 MFC 控制列的基類。 控制列是對齊框架視窗邊緣的視窗。 控制列包含以為基礎的 `HWND` 子控制項或不是以為基礎的控制項 `HWND` ，例如工具列按鈕。

[CDialogBar](reference/cdialogbar-class.md)<br/>
以對話方塊範本為基礎的控制列。

[CReBar](reference/crebar-class.md)<br/>
支援可以包含控制項形式之其他子視窗的工具列。

[CToolBar](reference/ctoolbar-class.md)<br/>
包含不是以為基礎之點陣圖命令按鈕的工具列控制項視窗 `HWND` 。 大部分的 MFC 應用程式會使用這個類別，而不是 `CToolBarCtrl` 。

[CStatusBar](reference/cstatusbar-class.md)<br/>
狀態列控制項視窗的基類。 大部分的 MFC 應用程式會使用這個類別，而不是 `CStatusBarCtrl` 。

## <a name="windows-control-bars"></a>Windows 控制列

這些控制列是適用于對應之 Windows 控制項的精簡型包裝函式。 因為它們並未與架構整合，所以比先前列出的控制列更難使用它們。 大部分的 MFC 應用程式會使用先前列出的控制列。

[CRebarCtrl](reference/crebarctrl-class.md)<br/>
執行物件的內部控制項 `CRebar` 。

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
水準視窗（通常分成窗格），應用程式可以在其中顯示狀態資訊。

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具列通用控制項的功能。

## <a name="related-classes"></a>相關類別

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
一個小型快顯視窗，會在應用程式中顯示一個描述工具用途的單行文字。

[CDockState](reference/cdockstate-class.md)<br/>
處理控制列銜接狀態資料的持續性儲存。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
