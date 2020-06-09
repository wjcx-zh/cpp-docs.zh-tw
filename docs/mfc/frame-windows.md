---
title: 框架視窗
ms.date: 11/19/2018
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
ms.openlocfilehash: 39c0b4b866fa123d8bcae639342c925570d96e1b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625828"
---
# <a name="frame-windows"></a>框架視窗

當應用程式在 Windows 下執行時，使用者會與框架視窗中顯示的檔互動。 檔框架視窗有兩個主要元件：框架和框架的內容。 檔框架視窗可以是[單一檔介面](sdi-and-mdi.md)（SDI）框架視窗或[多重文件介面](sdi-and-mdi.md)（MDI）子視窗。 Windows 會管理大部分使用者與框架視窗的互動：移動視窗並調整其大小、將其關閉，並將其最小化並最大化。 您可以管理框架內的內容。

## <a name="frame-windows-and-views"></a>框架視窗和 Views

MFC 架構會使用框架視窗來包含 views。 兩個元件（框架和內容）會由 MFC 中的兩個不同類別來表示和管理。 框架視窗類別會管理框架，而 view 類別則會管理內容。 [View] 視窗是框架視窗的子系。 繪圖和其他使用者與檔的互動會在視圖的工作區中進行，而不是框架視窗的工作區。 框架視窗會在視圖周圍提供可見的框架，並以標題列和標準視窗控制項（例如 [控制項] 功能表）、將視窗最小化並最大化的按鈕，以及用來調整視窗大小的控制項來完成。 「內容」是由視窗的工作區所組成，它完全由子視窗（view）所佔據。 下圖顯示框架視窗和視圖之間的關聯性。

![框架視窗視圖](../mfc/media/vc37fx1.gif "框架視窗檢視") <br/>
框架視窗和視圖

## <a name="frame-windows-and-splitter-windows"></a>框架視窗和分隔視窗

另一個常見的相片順序是讓框架視窗建立多個視圖的框架，通常是使用[分隔視窗](multiple-document-types-views-and-frame-windows.md)。 在分隔視窗中，框架視窗的工作區是由分隔視窗所佔用，而它又有多個子視窗，稱為窗格，也就是 views。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

**一般框架視窗主題**

- [視窗物件](window-objects.md)

- [框架視窗類別](frame-window-classes.md)

- [應用程式精靈所建立的框架視窗類別](frame-window-classes-created-by-the-application-wizard.md)

- [框架視窗樣式](frame-window-styles-cpp.md)

- [框架視窗的作用](what-frame-windows-do.md)

**使用框架視窗的主題**

- [使用框架視窗](using-frame-windows.md)

- [建立檔框架視窗](creating-document-frame-windows.md)

- [終結框架視窗](destroying-frame-windows.md)

- [管理 MDI 子視窗](managing-mdi-child-windows.md)

- 在包含一個以上視圖的框架視窗中[管理目前的視圖](managing-the-current-view.md)

- [管理功能表、控制列和快速鍵（其他共用框架視窗空間的物件）](managing-menus-control-bars-and-accelerators.md)

**特殊框架視窗功能的主題**

- 將檔案從 [檔案瀏覽器] 或 [檔案管理員][拖放](dragging-and-dropping-files-in-a-frame-window.md)到框架視窗

- [回應動態資料交換（DDE）](responding-to-dynamic-data-exchange-dde.md)

- [Semimodal 狀態：上下文相關的 Windows 說明（協調其他視窗動作）](orchestrating-other-window-actions.md)

- [Semimodal 狀態：列印和預覽列印（協調其他視窗動作）](orchestrating-other-window-actions.md)

**其他類型 Windows 的主題**

- [使用檢視](using-views.md)

- [對話方塊](dialog-boxes.md)

- [控制項](controls-mfc.md)

## <a name="see-also"></a>另請參閱

[Windows](windows.md)
