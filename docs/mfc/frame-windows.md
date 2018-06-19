---
title: 框架視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame widows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 515df19bcc11f7a6706985014fc44bc4ff315f36
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352059"
---
# <a name="frame-windows"></a>框架視窗
當應用程式執行 windows 時，使用者會與文件框架視窗中顯示的互動。 文件框架視窗包含兩個主要元件： 框架和框架的內容。 文件框架視窗可以是[單一文件介面](../mfc/sdi-and-mdi.md)(SDI) 框架視窗或[多重文件介面](../mfc/sdi-and-mdi.md)(MDI) 子視窗。 Windows 會處理大部分與框架視窗的使用者的互動： 移動和調整視窗大小、 關閉，和最小化和最大化它。 您可以管理內部框架的內容。  
  
## <a name="frame-windows-and-views"></a>框架視窗和檢視表  
 MFC 架構會使用框架視窗包含的檢視。 兩個元件 — 框架和內容，會表示，由 MFC 中的兩個不同類別。 框架視窗類別管理框架和檢視類別管理內容。 [檢視] 視窗是框架視窗的子系。 繪圖和文件與其他使用者互動發生在檢視的用戶端區域中，框架視窗的工作區。 框架視窗會提供檢視完整的標題列和標準的視窗控制項，例如控制項功能表上，最小化和最大化視窗中，按鈕周圍顯示框架，並調整視窗大小會控制。 「 內容 」 包含視窗的工作區完全佔用的子視窗，檢視。 下圖顯示在框架視窗和檢視之間的關聯性。  
  
 ![框架視窗檢視](../mfc/media/vc37fx1.gif "vc37fx1")  
框架視窗和檢視  
  
## <a name="frame-windows-and-splitter-windows"></a>框架視窗和分隔視窗  
 另一個常見的排列方式是框架視窗來框住多個檢視，通常使用[分隔視窗](../mfc/multiple-document-types-views-and-frame-windows.md)。 在分隔視窗中，框架視窗的工作區佔用的分隔視窗中，而後者又多子視窗，呼叫的窗格，也就是檢視。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
 **一般框架視窗的主題**  
  
-   [視窗物件](../mfc/window-objects.md)  
  
-   [框架視窗類別](../mfc/frame-window-classes.md)  
  
-   [應用程式精靈所建立的框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架視窗樣式](../mfc/frame-window-styles-cpp.md)  
  
-   [框架視窗的功能](../mfc/what-frame-windows-do.md)  
  
 **使用框架視窗的主題**  
  
-   [使用框架視窗](../mfc/using-frame-windows.md)  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
-   [終結框架視窗](../mfc/destroying-frame-windows.md)  
  
-   [管理 MDI 子視窗](../mfc/managing-mdi-child-windows.md)  
  
-   [管理目前檢視](../mfc/managing-the-current-view.md)中包含多個檢視的框架視窗  
  
-   [管理功能表、 控制列和快速鍵 （其他物件共用框架視窗的空間）](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **特殊的框架視窗功能的相關主題**  
  
-   [拖放檔案](../mfc/dragging-and-dropping-files-in-a-frame-window.md)來自檔案總管或檔案管理員成框架視窗  
  
-   [回應動態資料交換 (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [半強制回應狀態： 即時線上 Windows 說明 （協調其他視窗動作）](../mfc/orchestrating-other-window-actions.md)  
  
-   [半強制回應狀態： 列印和預覽列印 （協調其他視窗動作）](../mfc/orchestrating-other-window-actions.md)  
  
 **在其他種類的 Windows 上的主題**  
  
-   [使用檢視](../mfc/using-views.md)  
  
-   [對話方塊](../mfc/dialog-boxes.md)  
  
-   [控制項](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>另請參閱  
 [Windows](../mfc/windows.md)

