---
title: 框架視窗類別 (架構)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: 483112d197b7c7211989ecda8b774deb9f30d49e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624600"
---
# <a name="frame-window-classes-architecture"></a>框架視窗類別 (架構)

在檔/視圖架構中，框架視窗是包含 [view] 視窗的視窗。 它們也支援連接控制列。

在多重文件介面（MDI）應用程式中，主視窗衍生自 `CMDIFrameWnd` 。 它間接包含檔的框架，也就是 `CMDIChildWnd` 物件。 `CMDIChildWnd`接著，物件會包含檔的 views。

在單一檔介面（SDI）應用程式中，主視窗（衍生自 `CFrameWnd` ）包含目前檔的視圖。

[CFrameWnd](reference/cframewnd-class.md)<br/>
SDI 應用程式主框架視窗的基類。 也是所有其他框架視窗類別的基類。

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
MDI 應用程式主框架視窗的基類。

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
MDI 應用程式檔框架視窗的基類。

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
當伺服器檔正在進行編輯時，提供視圖的框架視窗。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
