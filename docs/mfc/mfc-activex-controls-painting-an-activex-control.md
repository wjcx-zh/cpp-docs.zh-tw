---
title: "MFC ActiveX 控制項：繪製 ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控制項, 最佳化"
  - "MFC ActiveX 控制項, 繪圖"
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：繪製 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 ActiveX 控制項繪製製程，以及如何修改繪製程式碼最佳化處理。\(請參閱技術的 [最佳繪製控制項](../mfc/optimizing-control-drawing.md) 如何由會最佳化繪圖控制個別還原先前選取的 GDI 物件。  在所有控制項繪製之後，容器可以自動還原原始物件\)。  
  
 範例本文是擁有預設設定的 MFC ActiveX 控制項精靈所建立的控制項。  如需使用 MFC ActiveX 控制項精靈的基本架構控制應用程式的詳細資訊，請參閱本文件的 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)。  
  
 其中包含下列主題：  
  
-   [繪製的 ActiveX 控制項精靈和程式碼整體程序建立的控制項支援繪製](#_core_the_painting_process_of_an_activex_control)  
  
-   [如何最佳化繪製製程](#_core_optimizing_your_paint_code)  
  
-   [使用中繼檔，如何使用您的控制項](#_core_painting_your_control_using_metafiles)  
  
##  <a name="_core_the_painting_process_of_an_activex_control"></a> ActiveX 控制項的繪製行為  
 當 ActiveX 控制項最初會顯示或重新繪製時，會依照繪製製程類似使用 MFC 所開發的應用程式，其中一個重要差異:ActiveX 控制項可以處於作用中或一個非現用狀態。  
  
 現用控制項在 ActiveX 控制項容器所表示的子視窗。  就像其他視窗，當 `WM_PAINT` 收到訊息時，它會繪製負責。  控制項的基底類別， [COleControl](../mfc/reference/colecontrol-class.md)，控制代碼會在其 `OnPaint` 函式中的這個訊息。  這個預設實作會呼叫控制項的 `OnDraw` 函式。  
  
 非現用控制項不同方式繪製。  當控制項處於非現用狀態時，它的視窗是可見或不存在的，因此無法接收繪製訊息。  相反地，控制項容器直接呼叫控制項的 `OnDraw` 函式。  這與使用中控制項的繪製製程在於 `OnPaint` 成員函式絕不會呼叫。  
  
 如前面所述， ActiveX 控制項如何更新取決於控制項的狀態。  不過，因為架構在兩種情況下呼叫 `OnDraw` 成員函式，將大部分的此成員函式的繪製程式碼。  
  
 `OnDraw` 成員函式來處理控制項的繪製。  當控制項處於非現用狀態時，控制項容器呼叫 `OnDraw`，透過控制項容器的裝置內容和所佔用的矩形區域的座標控制。  
  
 這個架構會將參數所 `OnDraw` 成員函式包含的控制項佔據的區域。  如果控制項正在使用中，左上角為 \(0， 0\)，並傳遞的裝置內容是包含控制項的子視窗。  如果控制項是無作用的，其左上角座標不一定是 \(0， 0\)，並傳遞的裝置內容是包含控制項的容器。  
  
> [!NOTE]
>  請務必對  `OnDraw` 的修改不依賴矩形左上角的位置等於 \(0， 0\)，而您只繪製矩形內傳遞至 `OnDraw`。  如果您在矩形的區域之外，繪製非預期的結果可能發生。  
  
 控制項實作檔 \(.CPP\) MFC ActiveX 控制項精靈提供的預設實作，如下所示，繪製一個白色筆刷矩形並以目前的背景色彩填滿橢圓形。  
  
 [!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/CPP/mfc-activex-controls-painting-an-activex-control_1.cpp)]  
  
> [!NOTE]
>  在繪製控制項時，您不應該對以 *pdc* 參數對 `OnDraw` 函式裝置內容狀態的假設。  有時候容器應用程式提供裝置內容，並不一定初始化為預設狀態。  特別是，明確選取畫筆、筆刷、色彩、字型和您的繪圖程式碼相依的其他資源。  
  
##  <a name="_core_optimizing_your_paint_code"></a> 最佳化繪畫程式碼  
 在控制項已成功自己繪製之後，下一步是最佳化 `OnDraw` 函式。  
  
 繪製繪製的 ActiveX 控制項的預設實作整個控制項範圍。  對於簡單的控制項已經足夠，不過在大部分的情況下重新繪製控制項是快速，如果需要更新重新繪製的部分，而不是整個控制項。  
  
 `OnDraw` 函式會透過 `rcInvalid`提供最佳化簡單方法，需要重新繪製控制項的矩形範圍。  小於整個控制項範圍內使用這個區域，通常快速繪製製程。  
  
##  <a name="_core_painting_your_control_using_metafiles"></a> 繪製您的使用中繼檔的控制項  
 在許多情況 \(如 `OnDraw` 函式中的 `pdc` 參數轉換螢幕裝置內容 \(DC\)。  不過，在列印時，控制項的影像或在預覽列印工作階段期間，會接收的 DC 是稱為中繼檔 DC」的特殊型別。  不同於螢幕 DC，立即處理要求傳送給它，中繼檔 DC 儲存之後使用。  有些容器應用程式也可以選擇將控制項呈現影像使用中繼檔 DC，在設計模式中。  
  
 中繼檔繪製要求可以由容器來兩個介面功能: **IViewObject::Draw** \(這個函式可能為非中繼檔繪圖也稱為\) 和 **IDataObject::GetData**。  在刪除中繼檔 DC 會當成其中一個參數時， MFC 框架呼叫 [COleControl::OnDrawMetafile](../Topic/COleControl::OnDrawMetafile.md)。  由於這是虛擬成員函式，請覆寫控制項類別的這個函式會執行任何特殊處理。  使用預設行為會呼叫 `COleControl::OnDraw`。  
  
 若要判斷控制項在螢幕上繪製，且中繼檔裝置內容，您必須在螢幕和中繼檔 DC 只支援的成員函式。  請注意座標系統以像素不可以測量。  
  
 因為 `OnDrawMetafile` 的預設實作會呼叫控制項的 `OnDraw` 函式，請使用適用於中繼檔和螢幕裝置內容的成員函式，，除非您覆寫 `OnDrawMetafile`。  下列清單 `CDC` 可中繼檔和螢幕裝置內容的成員函式的子集。  如需這些功能的詳細資訊，請參閱《 *MFC 參考》中的*[CDC](../mfc/reference/cdc-class.md) 類別。  
  
|弧形|BibBlt|字串|  
|--------|------------|--------|  
|**橢圓形**|**逸出字元**|`ExcludeClipRect`|  
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|  
|`LineTo`|`MoveTo`|`OffsetClipRgn`|  
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|  
|`Pie`|**Polygon**|`Polyline`|  
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|  
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|  
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|  
|`SelectPalette`|`SetBkColor`|`SetBkMode`|  
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|  
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|  
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|  
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|  
|`StretchBlt`|`TextOut`||  
  
 除了 `CDC` 成員函式之外，還有相容於中繼檔 DC 的許多其他功能。  其中包括 [CPalette::AnimatePalette](../Topic/CPalette::AnimatePalette.md)、 [CFont::CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md)和 `CBrush`的三 \+ 成成員的函式: [CreateBrushIndirect](../Topic/CBrush::CreateBrushIndirect.md)、 [CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md)和 [CreatePatternBrush](../Topic/CBrush::CreatePatternBrush.md)。  
  
 在中繼檔不會錄製的函式是: [DrawFocusRect](../Topic/CDC::DrawFocusRect.md)、 [DrawIcon](../Topic/CDC::DrawIcon.md)、 [DrawText](../Topic/CDC::DrawText.md)、 [ExcludeUpdateRgn](../Topic/CDC::ExcludeUpdateRgn.md)、 [FillRect](../Topic/CDC::FillRect.md)、 [FrameRect](../Topic/CDC::FrameRect.md)、 [GrayString](../Topic/CDC::GrayString.md)、 [InvertRect](../Topic/CDC::InvertRect.md)、 [ScrollDC](../Topic/CDC::ScrollDC.md)和 [TabbedTextOut](../Topic/CDC::TabbedTextOut.md)。  由於中繼檔 DC 實際上並未與裝置，您無法使用 SetDIBits、GetDIBits 和 CreateDIBitmap 與中繼檔 DC。  您可以使用 SetDIBitsToDevice 和 StretchDIBits 與中繼檔 DC 做為目的端。  [CreateCompatibleDC](../Topic/CDC::CreateCompatibleDC.md)、 [CreateCompatibleBitmap](../Topic/CBitmap::CreateCompatibleBitmap.md)和 [CreateDiscardableBitmap](../Topic/CBitmap::CreateDiscardableBitmap.md) 不具任何意義與中繼檔 DC。  
  
 考慮使用中繼檔網域控制站 \(DC\) 時的另一點是座標系統以像素不可以測量。  因此，應該以符合調整所有的繪圖程式碼矩形傳入 `rcBounds` 參數的 `OnDraw` 。  因為 `rcBounds` 代表控制項視窗的大小，這可防止在控制項外部的意外繪製。  
  
 在您實作了控制項後中繼檔轉換，請使用測試容器測試中繼檔。  如需存取測試容器的詳細資訊，請參閱[用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)。  
  
#### 使用測試容器，測試控制項的中繼檔。  
  
1.  在測試容器的 **Edit** 功能表上，按一下 **Insert New Control**。  
  
2.  在 **Insert New Control** 方塊中，選取控制項並按一下 \[**好**\]。  
  
     控制項會出現在測試容器。  
  
3.  在 **Control** 功能表上，按一下 **Draw Metafile**。  
  
     另一個視窗中會出現哪些中繼檔隨即顯示。  您可以變更這個視窗的大小會調整如何影響控制項的中繼檔。  您可以隨時關閉此視窗。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)