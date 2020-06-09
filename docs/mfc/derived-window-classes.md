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
ms.openlocfilehash: c84284b765e740fa0a13972e9902e7737e15bbab
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623179"
---
# <a name="derived-window-classes"></a>衍生的視窗類別

您可以直接從[CWnd](reference/cwnd-class.md)建立 windows，或從衍生新的視窗類別 `CWnd` 。 這是您通常建立自己的自訂視窗的方式。 不過，在 framework 程式中使用的大部分視窗，會改為從 MFC 所提供的其中一個 `CWnd` 衍生的框架視窗類別建立。

## <a name="frame-window-classes"></a>框架視窗類別

[CFrameWnd](reference/cframewnd-class.md)<br/>
用於建立單一檔和其觀看畫面的 SDI 框架視窗。 框架視窗是應用程式的主框架視窗，以及目前檔的框架視窗。

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
當做 MDI 應用程式的主框架視窗使用。 主框架視窗是所有 MDI 文件視窗的容器，並與之共用其功能表列。 MDI 框架視窗是出現在桌面上的最上層視窗。

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
用於在 MDI 主框架視窗中開啟的個別檔。 每份檔及其視圖都會以 MDI 主框架視窗所包含的 MDI 子框架視窗來框住。 MDI 子視窗看起來很像一般框架視窗，而是包含在 MDI 框架視窗中，而不是放在桌面上。 不過，MDI 子視窗缺少其本身的功能表列，而且必須共用包含它的 MDI 框架視窗的功能表列。

如需詳細資訊，請參閱[框架視窗](frame-windows.md)。

## <a name="other-window-classes-derived-from-cwnd"></a>衍生自 CWnd 的其他視窗類別

除了框架視窗之外，還有其他幾個主要的 windows 類別是衍生自 `CWnd` ：

*檢視*<br/>
Views 是使用 `CWnd` 衍生類別[CView](reference/cview-class.md) （或它的其中一個衍生類別）所建立。 「視圖」會附加至檔，並作為檔和使用者之間的媒介。 「視圖」是子視窗（非 MDI 子系），通常會填滿 SDI 框架視窗或 MDI 子框架視窗的工作區（或工具列和/或狀態列未涵蓋的工作區部分）。

*對話方塊*<br/>
對話方塊是使用 `CWnd` 衍生類別[CDialog](reference/cdialog-class.md)來建立。

*表單*<br/>
以對話方塊範本資源（例如對話方塊）為基礎的表單檢視，是使用類別[CFormView](reference/cformview-class.md)、 [CRecordView](reference/crecordview-class.md)或[CDaoRecordView](reference/cdaorecordview-class.md)所建立。

*控制項*<br/>
控制項（例如按鈕、清單方塊和下拉式方塊）是使用其他衍生自的類別來建立 `CWnd` 。 請參閱[控制主題](controls-mfc.md)。

*控制列*<br/>
包含控制項的子視窗。 範例包括工具列和狀態列。 請參閱[控制](control-bars.md)列。

## <a name="window-class-hierarchy"></a>視窗類別階層

請參閱*Mfc 參考*中的 mfc 階層架構[圖表](hierarchy-chart.md)。 視圖會在[檔/視圖架構](document-view-architecture.md)中說明。 對話方塊中會說明對話方塊[。](dialog-boxes.md)

## <a name="creating-your-own-special-purpose-window-classes"></a>建立您自己的特殊用途視窗類別

除了類別庫所提供的視窗類別以外，您可能還需要特殊用途的子視窗。 若要建立這種視窗，請建立您自己的[CWnd](reference/cwnd-class.md)衍生類別，並將它設為框架或視圖的子視窗。 請記住，架構會管理檔框架視窗的工作區範圍。 大部分的工作區都是由視圖管理，但是其他視窗（例如控制列或您自己的自訂視窗）可能會與此視圖共用空間。 您可能需要與類別[CView](reference/cview-class.md)和[CControlBar](reference/ccontrolbar-class.md)中的機制互動，以便在框架視窗的工作區中定位子視窗。

[建立 Windows](creating-windows.md)討論視窗物件及其管理的視窗的建立。

## <a name="see-also"></a>另請參閱

[視窗物件](window-objects.md)
