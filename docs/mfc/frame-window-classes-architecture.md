---
title: 框架視窗類別 (架構)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: d1022d9a49e12585a6588e7b3202155f533e4706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431703"
---
# <a name="frame-window-classes-architecture"></a>框架視窗類別 (架構)

在文件/檢視架構中，框架視窗會是包含 [檢視] 視窗的視窗。 它們也支援讓控制列附加到它們。

在多個文件介面 (MDI) 應用程式主視窗衍生自`CMDIFrameWnd`。 它間接包含文件的框架，也就是`CMDIChildWnd`物件。 `CMDIChildWnd`物件，依序包含文件的檢視。

在單一文件介面 (SDI) 應用程式，主要視窗中，衍生自`CFrameWnd`，包含目前的文件的檢視。

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
SDI 應用程式的主框架視窗的基底類別。 也其他框架視窗類別的基底類別。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
MDI 應用程式的主框架視窗的基底類別。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
MDI 應用程式的文件框架視窗的基底類別。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
當就地編輯伺服器文件時，則您可以提供檢視框架視窗。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

