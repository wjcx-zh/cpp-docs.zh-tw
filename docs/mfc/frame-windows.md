---
title: 框架視窗
ms.date: 11/04/2016
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame windows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
ms.openlocfilehash: 09db7bab392778297f17c14f7bb807f91af4d896
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619930"
---
# <a name="frame-windows"></a>框架視窗

當應用程式執行 Windows 時，使用者會與文件框架視窗中顯示的互動。 文件框架視窗會有兩個主要元件： 框架和框架的內容。 文件框架視窗可以是[單一文件介面](../mfc/sdi-and-mdi.md)(SDI) 框架視窗或[多重文件介面](../mfc/sdi-and-mdi.md)(MDI) 子視窗。 Windows 會處理大部分與框架視窗的使用者的互動： 移動和調整視窗大小、 關閉它，並降到最低和最大化其。 您管理的框架內的內容。

## <a name="frame-windows-and-views"></a>框架 Windows 和檢視表

MFC 架構會使用框架視窗包含檢視。 兩個元件 — 框架和內容，都會呈現和管理由 MFC 中的兩個不同類別。 框架視窗類別管理框架，並檢視類別管理內容。 [檢視] 視窗是框架視窗的子系。 繪圖和其他的使用者互動，與文件中進行檢視的工作區中，框架視窗的工作區。 框架視窗會提供檢視完整的標題列和標準的視窗控制項，例如控制項功能表上，最小化及最大化視窗中，按鈕周圍顯示框架，並控制調整大小的視窗。 包含視窗的工作區，完全佔用子視窗的 [內容]，檢視。 下圖顯示在框架視窗和檢視之間的關聯性。

![框架視窗檢視](../mfc/media/vc37fx1.gif "vc37fx1")框架視窗和檢視

## <a name="frame-windows-and-splitter-windows"></a>框架 Windows 和分隔器的 Windows

另一個常見的排列方式為來框住多個檢視，通常使用的框架視窗[分隔器視窗](../mfc/multiple-document-types-views-and-frame-windows.md)。 在分隔器視窗中，框架視窗的工作區佔用的分隔器視窗，其中又包含多個子視窗，呼叫的窗格，也就是檢視。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

**一般框架視窗的主題**

- [視窗物件](../mfc/window-objects.md)

- [框架視窗類別](../mfc/frame-window-classes.md)

- [應用程式精靈所建立的框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [框架視窗樣式](../mfc/frame-window-styles-cpp.md)

- [框架視窗執行什麼功能](../mfc/what-frame-windows-do.md)

**使用框架 Windows 主題**

- [使用框架視窗](../mfc/using-frame-windows.md)

- [建立文件框架視窗](../mfc/creating-document-frame-windows.md)

- [終結框架視窗](../mfc/destroying-frame-windows.md)

- [管理 MDI 子視窗](../mfc/managing-mdi-child-windows.md)

- [管理目前的檢視](../mfc/managing-the-current-view.md)框架視窗包含一個以上的檢視中

- [管理功能表、 控制列和快速鍵 （其他物件共用框架視窗的空間）](../mfc/managing-menus-control-bars-and-accelerators.md)

**特殊的框架視窗功能的相關主題**

- [拖放檔案](../mfc/dragging-and-dropping-files-in-a-frame-window.md)從檔案總管或檔案管理員成框架視窗

- [回應動態資料交換 (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)

- [組織 semimodal 狀態： 即時線上 Windows 說明 （協調其他視窗動作）](../mfc/orchestrating-other-window-actions.md)

- [組織 semimodal 狀態： 列印和預覽列印 （協調其他視窗動作）](../mfc/orchestrating-other-window-actions.md)

**在其他種類的 Windows 上的主題**

- [使用檢視](../mfc/using-views.md)

- [對話方塊](../mfc/dialog-boxes.md)

- [控制項](../mfc/controls-mfc.md)

## <a name="see-also"></a>另請參閱

[Windows](../mfc/windows.md)

