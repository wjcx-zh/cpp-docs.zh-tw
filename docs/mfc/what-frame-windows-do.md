---
title: 框架視窗執行什麼功能
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
ms.openlocfilehash: 594700ef1cbe0030bbe452adaa40b29b4a72f4d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405673"
---
# <a name="what-frame-windows-do"></a>框架視窗執行什麼功能

除了框架檢閱以外，框架視窗負責協調框架與其檢閱及與應用程式相關的各種工作。 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)並[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)繼承自[CFrameWnd](../mfc/reference/cframewnd-class.md)，所以他們有`CFrameWnd`功能，以及它們所新增的新功能。 子視窗的範例包括檢視、控制項 (例如按鈕和清單方塊)，以及控制列 (包括工具列、狀態列和對話方塊列)。

框架視窗負責管理其子視窗的配置。 在 MFC 架構中，框架視窗可在其工作區內放置所有控制列、檢視和其他子視窗。

框架視窗也會轉送命令給其檢視，並且可回應來自控制項視窗的通知訊息。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [控制列 （如何調整大小成框架視窗）](../mfc/control-bars.md)

- [管理功能表、 控制列和快速鍵 （如何調整大小成框架視窗）](../mfc/managing-menus-control-bars-and-accelerators.md)

- [命令路由 （從框架視窗至其檢視和其他命令目標）](../mfc/command-routing.md)

- [文件 /View 架構](../mfc/document-view-architecture.md)

- [控制列](../mfc/control-bars.md)

- [控制項](../mfc/controls-mfc.md)

## <a name="see-also"></a>另請參閱

[框架視窗](../mfc/frame-windows.md)
