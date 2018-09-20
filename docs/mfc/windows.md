---
title: Windows |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], window
- windows [MFC]
- MFC, windows
- window objects [MFC], MFC Framework
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 664afc2d842a7072ed41d579939e530e01c6e33f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431771"
---
# <a name="windows"></a>Windows

此系列文章說明在 MFC 架構中的視窗物件。 所有的 MFC 視窗是衍生自類別[CWnd](../mfc/reference/cwnd-class.md)，包括框架視窗、 檢視、 對話方塊和控制項。

第一群說明[window 物件](../mfc/window-objects.md)一般。 此群組，如需 c + + 視窗物件，一般資訊，請參閱如何封裝`HWND`，以及您如何使用它們建立您自己的視窗，例如子視窗時。

第二個群說明[框架視窗](../mfc/frame-windows.md)— 放置內容周圍框架的 windows — 尤其。 請參閱此群組，如需有關 MFC 架構如何管理框架視窗與它們框架時，包括控制列和檢視表的內容資訊。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

*視窗物件的一般主題*

- [視窗物件](../mfc/window-objects.md)

- [C + + 之間的關聯性視窗物件和 HWND 處理](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [在衍生的視窗類別](../mfc/derived-window-classes.md)

- [建立視窗物件](../mfc/creating-windows.md)

- [終結視窗物件](../mfc/destroying-window-objects.md)

- [註冊視窗 「 類別 」](../mfc/registering-window-classes.md)

- [使用視窗物件](../mfc/working-with-window-objects.md)

- [裝置內容](../mfc/device-contexts.md)： 讓 Windows 繪製裝置獨立的物件

- [圖形物件](../mfc/graphic-objects.md)： 畫筆、 筆刷、 字型、 點陣圖、 調色盤、 區域

*框架視窗的主題*

- [框架視窗](../mfc/frame-windows.md)： 提供框架的視窗物件

- [框架視窗和檢視表](../mfc/frame-windows.md)

- [框架視窗類別](../mfc/frame-window-classes.md)

- [框架視窗樣式](../mfc/frame-window-styles-cpp.md)

- [變更 MFC 所建立之視窗的樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [框架視窗執行什麼功能](../mfc/what-frame-windows-do.md)

- [使用框架視窗](../mfc/using-frame-windows.md)

- [管理 MD/子視窗 （MDICLIENT 視窗）](../mfc/managing-mdi-child-windows.md)

- [管理功能表、 控制列和快速鍵](../mfc/managing-menus-control-bars-and-accelerators.md)

- [CFrameWnd](../mfc/reference/cframewnd-class.md)

- [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)

- [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)

- [使用檢視](../mfc/using-views.md)

- [多個文件類型、 檢視和框架 Windows （分隔視窗）](../mfc/multiple-document-types-views-and-frame-windows.md)

- [訊息 （對應和處理常式函式）](../mfc/messages.md)

*建立和終結 Windows*

- [一般視窗建立順序](../mfc/general-window-creation-sequence.md)

- [終結視窗物件](../mfc/destroying-window-objects.md)

- [建立文件框架視窗](../mfc/creating-document-frame-windows.md)

- [終結框架視窗](../mfc/destroying-frame-windows.md)

*建立分隔器的 Windows*

- [建立分隔器視窗](../mfc/multiple-document-types-views-and-frame-windows.md)

*管理子 Windows 和目前的檢視*

- [管理 MDI 子視窗](../mfc/managing-mdi-child-windows.md)

- [管理目前檢視](../mfc/managing-the-current-view.md)

- [管理功能表、 控制列和快速鍵](../mfc/managing-menus-control-bars-and-accelerators.md)

*使用裝置內容和視窗樣式*

- [使用 裝置內容中的 畫筆和其他圖形物件](../mfc/graphic-objects.md)

- [變更 MFC 所建立之視窗的樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)<br/>
[對話方塊](../mfc/dialog-boxes.md)<br/>
[工具列](../mfc/toolbars.md)<br/>
[狀態列](../mfc/status-bars.md)<br/>
[對話方塊列](../mfc/dialog-bars.md)

