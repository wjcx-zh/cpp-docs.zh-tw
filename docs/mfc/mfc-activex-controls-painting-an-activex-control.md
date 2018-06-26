---
title: MFC ActiveX 控制項： 繪製 ActiveX 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de12a21c4b411f3cd1fe25d7d6badd8d26318351
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929808"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC ActiveX 控制項：繪製 ActiveX 控制項
本文將描述 ActiveX 控制項繪製程序，以及如何修改繪製程式碼以最佳化這個程序  (請參閱[最佳化控制項繪圖](../mfc/optimizing-control-drawing.md)的技術如何不讓控制項個別藉此最佳化繪製還原先前選取的 GDI 物件。 在繪製所有控制項之後，容器就可以自動還原原始物件)。  
  
 本文中的範例來自「MFC ActiveX 控制項精靈」以預設設定建立的控制項。 如需有關如何建立基本架構控制項應用程式中使用 MFC ActiveX 控制項精靈的詳細資訊，請參閱文章[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)。  
  
 其中包含下列主題：  
  
-   [繪製的整體程序控制項和程式碼所建立可支援繪製 ActiveX 控制項精靈](#_core_the_painting_process_of_an_activex_control)  
  
-   [如何最佳化繪製程序](#_core_optimizing_your_paint_code)  
  
-   [如何繪製控制項使用中繼檔](#_core_painting_your_control_using_metafiles)  
  
##  <a name="_core_the_painting_process_of_an_activex_control"></a> ActiveX 控制項繪製程序  
 當 ActiveX 控制項最初顯示或重繪時，所採取的繪製程序類似使用 MFC 所開發的其他應用程式，但其中有一項重要的差異：ActiveX 控制項可以處於現用或非現用狀態。  
  
 現用控制項在 ActiveX 控制項容器中是以子視窗表示。 類似其他視窗中，它負責接收 WM_PAINT 訊息時繪製自己本身。 控制項的基底類別， [COleControl](../mfc/reference/colecontrol-class.md)，會處理此訊息在其`OnPaint`函式。 這個預設實作會呼叫控制項的 `OnDraw` 函式。  
  
 非現用控制項是以不同的方式繪製。 當控制項處於非現用狀態時，它的視窗會是不可見或不存在，因此無法接收繪製訊息。 控制項容器會改為直接呼叫控制項的 `OnDraw` 函式。 這種方式與現用控制項的繪製程序不同的地方在於，絕不會呼叫 `OnPaint` 成員函式。  
  
 如前段中所討論，ActiveX 控制項的更新方式取決於控制項的狀態。 不過，由於架構在兩種情況下都會呼叫 `OnDraw` 成員函式，因此您會將大部分的繪製程式碼加入這個成員函式中。  
  
 `OnDraw` 成員函式會處理控制項繪製。 當控制項處於非現用狀態時，控制項容器就會呼叫 `OnDraw`，以傳遞控制項容器的裝置內容和控制項佔據的矩形區域座標。  
  
 架構傳遞至 `OnDraw` 成員函式的矩形包含控制項佔據的區域。 如果控制項處於現用狀態，則左上角為 (0, 0)，而且傳遞的裝置內容會是包含控制項的子視窗。 如果控制項處於非現用狀態，則左上角座標不一定是 (0, 0)，而且傳遞的裝置內容會是包含控制項的控制項容器。  
  
> [!NOTE]
>  很重要，讓修改`OnDraw`不相依於該矩形的左上角位置等於 （0，0），而且您繪製矩形內，只傳遞給`OnDraw`。 如果您在矩形區域之外繪製，則可能發生非預期的結果。  
  
 「MFC ActiveX 控制項精靈」在控制項實作檔 (.CPP) 中提供的預設實作 (如下所示) 會用白色筆刷繪製矩形，並且會以目前的背景色彩填滿橢圓形。  
  
 [!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]  
  
> [!NOTE]
>  當繪製控制項，您應該提出任何假設為會傳遞裝置內容的狀態*pdc*參數`OnDraw`函式。 有時候裝置內容是由容器應用程式提供，而且不一定會初始化為預設狀態。 具體來說，請明確選取您的繪圖程式碼所依據的畫筆、筆刷、色彩、字型和其他資源。  
  
##  <a name="_core_optimizing_your_paint_code"></a> 最佳化繪製程式碼  
 控制項成功繪製本身之後，下一步是最佳化 `OnDraw` 函式。  
  
 ActiveX 控制項繪製的預設實作會繪製整個控制項範圍。 這對於簡單的控制項而言就已足夠，不過在大部分的情況下，如果只重繪需要更新的部分而不是整個控制項，重繪控制項的速度會比較快。  
  
 `OnDraw`函式會提供簡單的最佳化方法，藉由傳遞*rcInvalid*，需要重繪控制項的矩形區域。 使用這個區域可加快繪製程序的速度，因為這個區域通常比整個控制項區域小。  
  
##  <a name="_core_painting_your_control_using_metafiles"></a> 繪製控制項使用中繼檔  
 在大部分情況下*pdc*參數`OnDraw`函式指向螢幕裝置內容 (DC)。 不過，在列印控制項的影像或預覽列印工作階段期間，所收到用於呈現的 DC 會是稱為「中繼檔 DC」的特殊類型。 螢幕 DC 會立即處理收到的要求，中繼檔 DC 則是儲存要求以便之後播放。 在設計模式中，有些容器應用程式也可能會選擇使用中繼檔 DC 呈現控制項影像。  
  
 中繼檔繪製要求可透過兩個介面函式的容器： `IViewObject::Draw` （這個函式也可針對非中繼檔繪製） 和`IDataObject::GetData`。 當中繼檔 DC 當做其中一個參數傳遞時，MFC 架構會呼叫[colecontrol:: Ondrawmetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile)。 由於這是虛擬成員函式，因此請覆寫控制項類別中的這個函式，以便執行任何特殊處理。 預設行為會呼叫 `COleControl::OnDraw`。  
  
 為確保控制項能夠同時在螢幕與中繼檔裝置內容中繪製，您只能使用螢幕和中繼檔 DC 都支援的成員函式。 請注意，座標系統可能不會以像素為單位測量。  
  
 因為 `OnDrawMetafile` 的預設實作會呼叫控制項的 `OnDraw` 函式，因此，除非您覆寫 `OnDrawMetafile`，否則請使用同時適用於中繼檔和螢幕裝置內容的成員函式。 下面將列出可同時在中繼檔和螢幕裝置內容中使用的 `CDC` 子集。 如需這些函式的詳細資訊，請參閱類別[CDC](../mfc/reference/cdc-class.md)中*MFC 參考*。  
  
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
  
 除了 `CDC` 成員函式之外，中繼檔 DC 中還有其他幾個相容的函式。 這些包括[cpalette:: Animatepalette](../mfc/reference/cpalette-class.md#animatepalette)， [cfont:: Createfontindirect](../mfc/reference/cfont-class.md#createfontindirect)，和三個成員函式的`CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect)， [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush)，和[CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush)。  
  
 不會記錄在中繼檔中的函式是： [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect)， [DrawIcon](../mfc/reference/cdc-class.md#drawicon)， [DrawText](../mfc/reference/cdc-class.md#drawtext)， [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn)， [FillRect](../mfc/reference/cdc-class.md#fillrect)， [FrameRect](../mfc/reference/cdc-class.md#framerect)， [GrayString](../mfc/reference/cdc-class.md#graystring)， [InvertRect](../mfc/reference/cdc-class.md#invertrect)， [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)，和[TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout)。 由於中繼檔 DC 實際上並未與裝置相關聯，因此您無法在中繼檔 DC 中使用 SetDIBits、GetDIBits 和 CreateDIBitmap。 您可以在中繼檔 DC 中使用 SetDIBitsToDevice 和 StretchDIBits 做為目的端。 [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc)， [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap)，和[CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap)不具任何意義，在中繼檔 DC。  
  
 使用中繼檔 DC 時要考慮的另一點是，座標系統不一定會以像素為單位測量。 基於這個理由，所有您的繪圖程式碼應該加以調整成的矩形中傳遞至`OnDraw`中*rcbounds 就*參數。 這可避免不小心在控制項之外繪製，因為*rcbounds 就*代表控制項的視窗大小。  
  
 在您實作控制項的中繼檔呈現之後，請使用測試容器測試中繼檔。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。  
  
#### <a name="to-test-the-controls-metafile-using-test-container"></a>使用測試容器測試控制項的中繼檔  
  
1.  測試容器**編輯**功能表上，按一下 **插入新控制項**。  
  
2.  在**插入新控制項**方塊中選取的控制項，然後按一下**確定**。  
  
     控制項將會出現在測試容器中。  
  
3.  在**控制項**功能表上，按一下 **繪製中繼檔**。  
  
     另一個顯示中繼檔的視窗隨即出現。 您可以變更這個視窗的大小，查看縮放如何影響控制項的中繼檔。 您可以隨時關閉這個視窗。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

