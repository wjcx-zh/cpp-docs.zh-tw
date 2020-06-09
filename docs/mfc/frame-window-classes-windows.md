---
title: 框架視窗類別 (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 1c0a1e1e93433e0fbe07c11eb350216173e74d84
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625845"
---
# <a name="frame-window-classes-windows"></a>框架視窗類別 (Windows)

框架視窗是將應用程式或一部分應用程式框架的視窗。 框架視窗通常包含其他視窗，例如視圖、工具列和狀態列。 在案例中 `CMDIFrameWnd` ，它們可能會 `CMDIChildWnd` 間接包含物件。

[CFrameWnd](reference/cframewnd-class.md)<br/>
SDI 應用程式主框架視窗的基類。 也是所有其他框架視窗類別的基類。

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
MDI 應用程式主框架視窗的基類。

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
MDI 應用程式檔框架視窗的基類。

[CMiniFrameWnd](reference/cminiframewnd-class.md)<br/>
通常會在浮動工具列周圍看到一半高度的框架視窗。

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
當伺服器檔正在進行編輯時，提供視圖的框架視窗。

## <a name="related-class"></a>相關類別

類別 `CMenu` 提供用來存取應用程式功能表的介面。 這適用于在執行時間動態操作功能表;例如，根據內容新增或刪除功能表項目時。 雖然功能表最常用於框架視窗，但也可以搭配對話方塊和其他 nonchild 視窗使用。

[CMenu](reference/cmenu-class.md)<br/>
封裝 `HMENU` 應用程式的功能表列和快顯功能表的控制碼。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
