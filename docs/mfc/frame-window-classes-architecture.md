---
title: 框架視窗類別 (架構)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: e3ae432c1adc881a5c67d6a6c292dc1f6a583ab3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441261"
---
# <a name="frame-window-classes-architecture"></a>框架視窗類別 (架構)

在檔/視圖架構中，框架視窗是包含 [view] 視窗的視窗。 它們也支援連接控制列。

在多重文件介面（MDI）應用程式中，主視窗衍生自 `CMDIFrameWnd`。 它間接包含檔的框架，也就是 `CMDIChildWnd` 物件。 `CMDIChildWnd` 物件又會包含檔的 views。

在單一檔介面（SDI）應用程式中，從 `CFrameWnd`衍生的主視窗包含目前檔的視圖。

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
SDI 應用程式主框架視窗的基類。 也是所有其他框架視窗類別的基類。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
MDI 應用程式主框架視窗的基類。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
MDI 應用程式檔框架視窗的基類。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
當伺服器檔正在進行編輯時，提供視圖的框架視窗。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
