---
title: MFC ActiveX 控制項：繪製 ActiveX 控制項
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: a01a66402471b295a6e57af8af265c50685b4a1f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618214"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC ActiveX 控制項：繪製 ActiveX 控制項

本文將描述 ActiveX 控制項繪製程序，以及如何修改繪製程式碼以最佳化這個程序  （如需如何優化繪製的技巧，請參閱[優化控制項繪製](optimizing-control-drawing.md)，而不讓控制項個別還原先前選取的 GDI 物件。 在繪製所有控制項之後，容器就可以自動還原原始物件)。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

本文中的範例來自「MFC ActiveX 控制項精靈」以預設設定建立的控制項。 如需使用 MFC ActiveX 控制項建立基本架構控制項應用程式的詳細資訊，請參閱[MFC Activex 控制項 wizard](reference/mfc-activex-control-wizard.md)一文。

涵蓋下列主題：

- [繪製 ActiveX 控制項精靈所建立可支援繪製之控制項和程式碼的整體程序](#_core_the_painting_process_of_an_activex_control)

- [如何最佳化繪製程序](#_core_optimizing_your_paint_code)

- [如何使用中繼檔繪製控制項](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>ActiveX 控制項的繪製進程

當 ActiveX 控制項最初顯示或重繪時，所採取的繪製程序類似使用 MFC 所開發的其他應用程式，但其中有一項重要的差異：ActiveX 控制項可以處於現用或非現用狀態。

現用控制項在 ActiveX 控制項容器中是以子視窗表示。 就像其他視窗一樣，它會負責在收到 WM_PAINT 訊息時自行繪製。 控制項的基類[COleControl](reference/colecontrol-class.md)會在其函式中處理這個訊息 `OnPaint` 。 這個預設實作會呼叫控制項的 `OnDraw` 函式。

非現用控制項是以不同的方式繪製。 當控制項處於非現用狀態時，它的視窗會是不可見或不存在，因此無法接收繪製訊息。 控制項容器會改為直接呼叫控制項的 `OnDraw` 函式。 這種方式與現用控制項的繪製程序不同的地方在於，絕不會呼叫 `OnPaint` 成員函式。

如前段中所討論，ActiveX 控制項的更新方式取決於控制項的狀態。 不過，由於架構在兩種情況下都會呼叫 `OnDraw` 成員函式，因此您會將大部分的繪製程式碼加入這個成員函式中。

`OnDraw` 成員函式會處理控制項繪製。 當控制項處於非現用狀態時，控制項容器就會呼叫 `OnDraw`，以傳遞控制項容器的裝置內容和控制項佔據的矩形區域座標。

架構傳遞至 `OnDraw` 成員函式的矩形包含控制項佔據的區域。 如果控制項處於現用狀態，則左上角為 (0, 0)，而且傳遞的裝置內容會是包含控制項的子視窗。 如果控制項處於非現用狀態，則左上角座標不一定是 (0, 0)，而且傳遞的裝置內容會是包含控制項的控制項容器。

> [!NOTE]
> 您對的修改 `OnDraw` 不需依賴矩形的左上角（0，0），而且只會在傳遞至的矩形內繪製，這點很重要 `OnDraw` 。 如果您在矩形區域之外繪製，則可能發生非預期的結果。

「MFC ActiveX 控制項精靈」在控制項實作檔 (.CPP) 中提供的預設實作 (如下所示) 會用白色筆刷繪製矩形，並且會以目前的背景色彩填滿橢圓形。

[!code-cpp[NVC_MFC_AxUI#1](codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> 繪製控制項時，您不應該對當做*pdc*參數傳遞至函式的裝置內容進行假設 `OnDraw` 。 有時候裝置內容是由容器應用程式提供，而且不一定會初始化為預設狀態。 具體來說，請明確選取您的繪圖程式碼所依據的畫筆、筆刷、色彩、字型和其他資源。

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>優化您的繪製程式碼

控制項成功繪製本身之後，下一步是最佳化 `OnDraw` 函式。

ActiveX 控制項繪製的預設實作會繪製整個控制項範圍。 這對於簡單的控制項而言就已足夠，不過在大部分的情況下，如果只重繪需要更新的部分而不是整個控制項，重繪控制項的速度會比較快。

函 `OnDraw` 式提供簡單的優化方法，其方式是傳遞*rcInvalid*，這是需要重新繪製之控制項的矩形區域。 使用這個區域可加快繪製程序的速度，因為這個區域通常比整個控制項區域小。

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>使用中繼檔繪製控制項

在大部分情況下，函式的*pdc*參數會 `OnDraw` 指向螢幕裝置內容（DC）。 不過，在列印控制項的影像或預覽列印工作階段期間，所收到用於呈現的 DC 會是稱為「中繼檔 DC」的特殊類型。 螢幕 DC 會立即處理收到的要求，中繼檔 DC 則是儲存要求以便之後播放。 在設計模式中，有些容器應用程式也可能會選擇使用中繼檔 DC 呈現控制項影像。

容器可以透過兩個介面函式來進行中繼檔繪製要求： `IViewObject::Draw` （此函式也可針對非中繼檔繪製呼叫）和 `IDataObject::GetData` 。 當中繼檔 DC 當做其中一個參數傳遞時，MFC 架構會呼叫[COleControl：： OnDrawMetafile](reference/colecontrol-class.md#ondrawmetafile)。 由於這是虛擬成員函式，因此請覆寫控制項類別中的這個函式，以便執行任何特殊處理。 預設行為會呼叫 `COleControl::OnDraw`。

為確保控制項能夠同時在螢幕與中繼檔裝置內容中繪製，您只能使用螢幕和中繼檔 DC 都支援的成員函式。 請注意，座標系統可能不會以像素為單位測量。

因為 `OnDrawMetafile` 的預設實作會呼叫控制項的 `OnDraw` 函式，因此，除非您覆寫 `OnDrawMetafile`，否則請使用同時適用於中繼檔和螢幕裝置內容的成員函式。 下面將列出可同時在中繼檔和螢幕裝置內容中使用的 `CDC` 子集。 如需這些函數的詳細資訊，請參閱*MFC 參考*中的[CDC](reference/cdc-class.md)類別。

|Arc|BibBlt|Chord|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

除了 `CDC` 成員函式之外，中繼檔 DC 中還有其他幾個相容的函式。 其中包括[CPalette：： AnimatePalette](reference/cpalette-class.md#animatepalette)、 [CFont：： CreateFontIndirect](reference/cfont-class.md#createfontindirect)和三個成員函式 `CBrush` ： [CreateBrushIndirect](reference/cbrush-class.md#createbrushindirect)、 [CreateDIBPatternBrush](reference/cbrush-class.md#createdibpatternbrush)和[CreatePatternBrush](reference/cbrush-class.md#createpatternbrush)。

未記錄在中繼檔中的函式為： [DrawFocusRect](reference/cdc-class.md#drawfocusrect)、 [DrawIcon](reference/cdc-class.md#drawicon)、 [DrawText](reference/cdc-class.md#drawtext)、 [ExcludeUpdateRgn](reference/cdc-class.md#excludeupdatergn)、 [FillRect](reference/cdc-class.md#fillrect)、 [FrameRect](reference/cdc-class.md#framerect)、 [GrayString](reference/cdc-class.md#graystring)、 [InvertRect](reference/cdc-class.md#invertrect)、 [ScrollDC](reference/cdc-class.md#scrolldc)和[TabbedTextOut](reference/cdc-class.md#tabbedtextout)。 由於中繼檔 DC 實際上並未與裝置相關聯，因此您無法在中繼檔 DC 中使用 SetDIBits、GetDIBits 和 CreateDIBitmap。 您可以在中繼檔 DC 中使用 SetDIBitsToDevice 和 StretchDIBits 做為目的端。 [CreateCompatibleDC](reference/cdc-class.md#createcompatibledc)、 [CreateCompatibleBitmap](reference/cbitmap-class.md#createcompatiblebitmap)和[CreateDiscardableBitmap](reference/cbitmap-class.md#creatediscardablebitmap)對中繼檔 DC 沒有意義。

使用中繼檔 DC 時要考慮的另一點是，座標系統不一定會以像素為單位測量。 基於這個理由，您所有的繪圖程式碼都應該調整，以符合在 `OnDraw` *rcBounds*參數中傳遞至的矩形。 這可防止意外繪製在控制項外部，因為*rcBounds*代表控制項視窗的大小。

在您實作控制項的中繼檔呈現之後，請使用測試容器測試中繼檔。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](testing-properties-and-events-with-test-container.md) 。

#### <a name="to-test-the-controls-metafile-using-test-container"></a>使用測試容器測試控制項的中繼檔

1. 在測試容器的 [**編輯**] 功能表上，按一下 [**插入新控制項**]。

1. 在 [**插入新控制項**] 方塊中選取控制項，然後按一下 **[確定]**。

   控制項將會出現在測試容器中。

1. 在 [**控制**] 功能表上，按一下 [**繪製中繼檔**]。

   另一個顯示中繼檔的視窗隨即出現。 您可以變更這個視窗的大小，查看縮放如何影響控制項的中繼檔。 您可以隨時關閉這個視窗。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
