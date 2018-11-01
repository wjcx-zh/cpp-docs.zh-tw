---
title: 框架視窗類別 (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 93df9ce745fc907425f1a840ffb7d16a696831fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514331"
---
# <a name="frame-window-classes-windows"></a>框架視窗類別 (Windows)

框架視窗是視窗的主要應用程式或應用程式的一部分。 框架視窗通常會包含其他視窗，例如檢視、 工具列和狀態列。 若是`CMDIFrameWnd`，它們可能包含`CMDIChildWnd`間接物件。

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
SDI 應用程式的主框架視窗的基底類別。 也其他框架視窗類別的基底類別。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
MDI 應用程式的主框架視窗的基底類別。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
MDI 應用程式的文件框架視窗的基底類別。

[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)<br/>
通常在浮動工具列周圍出現的半高度框架視窗。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
當就地編輯伺服器文件時，則您可以提供檢視框架視窗。

## <a name="related-class"></a>相關的類別

類別`CMenu`提供用來存取您的應用程式功能表所透過的介面。 它可用於在執行階段; 動態管理功能表例如，當新增或刪除根據內容功能表項目。 雖然功能表通常可搭配框架視窗，也與對話方塊和其他藉視窗使用它們。

[CMenu](../mfc/reference/cmenu-class.md)<br/>
封裝`HMENU`應用程式的功能表列和快顯功能表的控制代碼。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

