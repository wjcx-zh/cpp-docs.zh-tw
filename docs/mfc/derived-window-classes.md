---
title: 衍生的視窗類別
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: bf0d8e82f1a1793f4e5561e24ed9ca173511d07c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462110"
---
# <a name="derived-window-classes"></a>衍生的視窗類別

您可以建立直接從 windows [CWnd](../mfc/reference/cwnd-class.md)，或衍生新的視窗類別，從`CWnd`。 這是通常是建立您自己自訂的 windows。 不過，大部分的 windows 架構程式中使用改為建立其中一個`CWnd`-衍生的 MFC 所提供的框架視窗類別。

## <a name="frame-window-classes"></a>框架視窗類別

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
用於框架單一文件和其檢視的 SDI 框架視窗。 應用程式的主框架視窗和框架視窗目前文件框架視窗。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
當做 MDI 應用程式的主框架視窗。 主框架視窗會是所有的 MDI 文件視窗的容器，並與它們共用其功能表列。 MDI 框架視窗是桌面上會顯示最上層視窗。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
用於個別的文件在 MDI 主框架視窗中開啟。 每份文件和其檢視是由框住，MDI 主框架視窗所包含之 MDI 子框架視窗。 MDI 子視窗很像一般的框架視窗，但包含在 MDI 框架視窗而不是坐在桌面上。 不過，MDI 子視窗沒有自己的功能表列，而且必須共用包含它，MDI 框架視窗的功能表列。

如需詳細資訊，請參閱 <<c0> [ 框架 Windows](../mfc/frame-windows.md)。

## <a name="other-window-classes-derived-from-cwnd"></a>其他衍生自 CWnd 的視窗類別

除了框架視窗的 windows 的其他數種主要類別衍生自`CWnd`:

*檢視*<br/>
使用建立檢視`CWnd`-衍生的類別[CView](../mfc/reference/cview-class.md) （或其衍生的類別）。 檢視附加至文件，並做為文件與使用者之間的媒介。 檢視是通常會填滿工作區的 SDI 框架視窗或 MDI 子框架視窗 （或未涵蓋的工具列和/或狀態列的工作區的部分） 子視窗 （而不 MDI 子系）。

*對話方塊*<br/>
使用建立對話方塊`CWnd`-衍生的類別[CDialog](../mfc/reference/cdialog-class.md)。

*表單*<br/>
使用類別建立根據對話方塊範本資源，例如對話方塊、 表單檢視[CFormView](../mfc/reference/cformview-class.md)， [CRecordView](../mfc/reference/crecordview-class.md)，或[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)。

*控制項*<br/>
使用衍生自其他類別建立控制項，例如按鈕、 清單方塊和下拉式方塊`CWnd`。 請參閱[控制主題](../mfc/controls-mfc.md)。

*控制列*<br/>
包含控制項的子視窗。 範例包括工具列和狀態列。 請參閱[控制列](../mfc/control-bars.md)。

## <a name="window-class-hierarchy"></a>視窗類別階層

請參閱[MFC 階層架構圖表](../mfc/hierarchy-chart.md)中*MFC 參考 》*。 檢視表所述[文件/檢視架構](../mfc/document-view-architecture.md)。 對話方塊會說明[Dialog Boxes](../mfc/dialog-boxes.md)。

## <a name="creating-your-own-special-purpose-window-classes"></a>建立您自己的特殊用途的視窗類別

除了類別程式庫所提供的視窗類別，您可能需要特殊用途的子視窗。 若要建立這種視窗，建立您自己[CWnd](../mfc/reference/cwnd-class.md)-衍生的類別，並使它成為子視窗的框架或檢視表。 請記住，架構會處理文件框架視窗的工作區的範圍。 大部分的工作區管理 檢視中，但其他視窗，例如控制項列或您自己自訂的 windows，可能會與共用空間檢視。 您可能需要在類別中的機制與互動[CView](../mfc/reference/cview-class.md)並[CControlBar](../mfc/reference/ccontrolbar-class.md)來定位在框架視窗的工作區中的子視窗。

[建立 Windows](../mfc/creating-windows.md)討論建立視窗物件和所管理的 windows。

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)

