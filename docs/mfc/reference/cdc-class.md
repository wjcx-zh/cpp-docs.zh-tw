---
title: "CDC 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDC 類別"
  - "coordinates in Windows 95/98 [C++]"
  - "device contexts [C++], CDC 類別"
  - "screen coordinates in device contexts"
  - "Windows [C++], device contexts"
  - "Windows 95 [C++], 螢幕座標"
  - "Windows 98 [C++], 螢幕座標"
ms.assetid: 715b3334-cb2b-4c9c-8067-02eb7c66c8b2
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDC 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義裝置內容物件類別。  
  
## 語法  
  
```  
class CDC : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDC::CDC](../Topic/CDC::CDC.md)|建構 `CDC` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDC::AbortDoc](../Topic/CDC::AbortDoc.md)|結束目前的列印工作，則清除應用程式提供裝置撰寫，因為 `StartDoc` 成員函式的最後一個呼叫中的所有項目。|  
|[CDC::AbortPath](../Topic/CDC::AbortPath.md)|在裝置內容區塊並捨棄所有路徑。|  
|[CDC::AddMetaFileComment](../Topic/CDC::AddMetaFileComment.md)|複製到緩衝區的註解將指定的加強型格式中繼檔。|  
|[CDC::AlphaBlend](../Topic/CDC::AlphaBlend.md)|顯示具有透明或半透明的像素的點陣圖。|  
|[CDC::AngleArc](../Topic/CDC::AngleArc.md)|繪製線段和弧形，並且移動目前位置移至弧形結束點。|  
|[CDC::Arc](../Topic/CDC::Arc.md)|繪製橢圓弧形。|  
|[CDC::ArcTo](../Topic/CDC::ArcTo.md)|繪製橢圓弧形。  這個函式類似，但是有一點例外，就是 `Arc`目前位置更新。|  
|[CDC::Attach](../Topic/CDC::Attach.md)|將視窗裝置內容至 `CDC` 物件。|  
|[CDC::BeginPath](../Topic/CDC::BeginPath.md)|在裝置內容開啟路徑括弧。|  
|[CDC::BitBlt](../Topic/CDC::BitBlt.md)|將項目從複製到指定的裝置內容的點陣圖。|  
|[CDC::Chord](../Topic/CDC::Chord.md)|繪製套索 \(橢圓形和線段交集所界限的封閉圖形\)。|  
|[CDC::CloseFigure](../Topic/CDC::CloseFigure.md)|關閉路徑中的一個開放的圖形。|  
|[CDC::CreateCompatibleDC](../Topic/CDC::CreateCompatibleDC.md)|建立與另一個裝置內容相容的記憶體裝置內容。  您可以使用已準備好在記憶體中的影像。|  
|[CDC::CreateDC](../Topic/CDC::CreateDC.md)|建立特定裝置的裝置內容。|  
|[CDC::CreateIC](../Topic/CDC::CreateIC.md)|建立特定裝置的資訊內容。  這提供快速的方法來取得關於裝置的資訊，而不必建立裝置內容。|  
|[CDC::DeleteDC](../Topic/CDC::DeleteDC.md)|刪除 Windows 裝置內容與這個 `CDC` 物件。|  
|[CDC::DeleteTempMap](../Topic/CDC::DeleteTempMap.md)|呼叫 `CWinApp` 閒置時間管理員刪除 `FromHandle`建立的任何 `CDC` 暫存物件。  同時中斷連接裝置內容。|  
|[CDC::Detach](../Topic/CDC::Detach.md)|中斷與這個物件的 `CDC` 視窗裝置內容。|  
|[CDC::DPtoHIMETRIC](../Topic/CDC::DPtoHIMETRIC.md)|轉換成裝置單位 **HIMETRIC** 單位。|  
|[CDC::DPtoLP](../Topic/CDC::DPtoLP.md)|轉換成裝置單位為邏輯單位。|  
|[CDC::Draw3dRect](../Topic/CDC::Draw3dRect.md)|繪製 3D 矩形。|  
|[CDC::DrawDragRect](../Topic/CDC::DrawDragRect.md)|其會在拖曳時，清除及重新繪製矩形。|  
|[CDC::DrawEdge](../Topic/CDC::DrawEdge.md)|繪製矩形邊緣。|  
|[CDC::DrawEscape](../Topic/CDC::DrawEscape.md)|透過存取圖形裝置介面 \(GDI\) 無法直接在的視訊監視器的繪圖功能。|  
|[CDC::DrawFocusRect](../Topic/CDC::DrawFocusRect.md)|繪製這個樣式的矩形表示焦點。|  
|[CDC::DrawFrameControl](../Topic/CDC::DrawFrameControl.md)|繪製框架控制項。|  
|[CDC::DrawIcon](../Topic/CDC::DrawIcon.md)|繪製圖示。|  
|[CDC::DrawState](../Topic/CDC::DrawState.md)|顯示影像並套用視覺效果指示的狀態。|  
|[CDC::DrawText](../Topic/CDC::DrawText.md)|繪製格式化的在指定矩形的文字。|  
|[CDC::DrawTextEx](../Topic/CDC::DrawTextEx.md)|使用不同的格式， Draws 格式化在指定矩形的文字。|  
|[CDC::Ellipse](../Topic/CDC::Ellipse.md)|繪製橢圓形。|  
|[CDC::EndDoc](../Topic/CDC::EndDoc.md)|結束 `StartDoc` 成員函式啟動的列印工作。|  
|[CDC::EndPage](../Topic/CDC::EndPage.md)|告知裝置驅動程式頁。|  
|[CDC::EndPath](../Topic/CDC::EndPath.md)|關閉路徑括號並選取括弧定義路徑到裝置內容中。|  
|[CDC::EnumObjects](../Topic/CDC::EnumObjects.md)|列舉型別 \(Enumeration\) 畫筆和筆刷可用的裝置內容。|  
|[CDC::Escape](../Topic/CDC::Escape.md)|允許應用程式存取從特定裝置本身不是可以透過 GDI 的安裝。  同時也允許存取 Windows 逸出函式的存取。  應用程式會呼叫的逸出字元翻譯並傳送至裝置驅動程式。|  
|[CDC::ExcludeClipRect](../Topic/CDC::ExcludeClipRect.md)|建立包含可指定矩形的現有裁剪區域的新裁剪區域。|  
|[CDC::ExcludeUpdateRgn](../Topic/CDC::ExcludeUpdateRgn.md)|防止繪製視窗的無效區域內透過排除視窗的更新區域從裁剪區域。|  
|[CDC::ExtFloodFill](../Topic/CDC::ExtFloodFill.md)|會用目前筆刷填滿區域。  要 [CDC::FloodFill](../Topic/CDC::FloodFill.md) 成員函式提供更多的彈性。|  
|[CDC::ExtTextOut](../Topic/CDC::ExtTextOut.md)|使用目前選取的字型，以矩形區域中的字串。|  
|[CDC::FillPath](../Topic/CDC::FillPath.md)|使用目前的筆刷和多邊形填滿模式，在目前路徑關閉任何開啟的圖表和填滿路徑的內部。|  
|[CDC::FillRect](../Topic/CDC::FillRect.md)|使用特定筆刷，填滿指定的矩形。|  
|[CDC::FillRgn](../Topic/CDC::FillRgn.md)|使用這個筆刷來填滿指定的特定區域。|  
|[CDC::FillSolidRect](../Topic/CDC::FillSolidRect.md)|使用純色填滿矩形。|  
|[CDC::FlattenPath](../Topic/CDC::FlattenPath.md)|轉換任何曲線所選取路徑構成目前裝置內容，並將每條曲線轉換為直線序列。|  
|[CDC::FloodFill](../Topic/CDC::FloodFill.md)|會用目前筆刷填滿區域。|  
|[CDC::FrameRect](../Topic/CDC::FrameRect.md)|在矩形周圍繪製框線。|  
|[CDC::FrameRgn](../Topic/CDC::FrameRgn.md)|使用筆刷，在特定區域周圍繪製框線。|  
|[CDC::FromHandle](../Topic/CDC::FromHandle.md)|傳回指向 `CDC` 物件，當指定控制代碼的裝置內容。  如果有 `CDC` 物件與任何控制代碼，暫存 `CDC` 物件建立和附加。|  
|[CDC::GetArcDirection](../Topic/CDC::GetArcDirection.md)|傳回裝置內容中目前弧形方向。|  
|[CDC::GetAspectRatioFilter](../Topic/CDC::GetAspectRatioFilter.md)|擷取目前的外觀比例篩選條件的設定。|  
|[CDC::GetBkColor](../Topic/CDC::GetBkColor.md)|擷取目前的背景色彩。|  
|[CDC::GetBkMode](../Topic/CDC::GetBkMode.md)|擷取背景方式。|  
|[CDC::GetBoundsRect](../Topic/CDC::GetBoundsRect.md)|傳回指定之裝置內容中目前的累積週框 \(Bounding Rectangle\)。|  
|[CDC::GetBrushOrg](../Topic/CDC::GetBrushOrg.md)|擷取這個目前的筆刷的原點。|  
|[CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)|從目前的擷取字型寬度，以邏輯單位，在特定範圍的連續字元。|  
|[CDC::GetCharABCWidthsI](../Topic/CDC::GetCharABCWidthsI.md)|從目前的 TrueType 字型擷取寬度，以邏輯單位，在指定的範圍的連續圖像索引。|  
|[CDC::GetCharacterPlacement](../Topic/CDC::GetCharacterPlacement.md)|擷取資訊的各種型別有關的字串。|  
|[CDC::GetCharWidth](../Topic/CDC::GetCharWidth.md)|從目前的字型擷取連續字元的分數寬度在特定範圍中。|  
|[CDC::GetCharWidthI](../Topic/CDC::GetCharWidthI.md)|從目前的擷取字型寬度，以邏輯座標，在指定的範圍的連續圖像索引。|  
|[CDC::GetClipBox](../Topic/CDC::GetClipBox.md)|在目前的裁剪界限四周擷取最嚴格的週框 \(Bounding Rectangle\) 的大小。|  
|[CDC::GetColorAdjustment](../Topic/CDC::GetColorAdjustment.md)|擷取裝置內容的色彩調整值。|  
|[CDC::GetCurrentBitmap](../Topic/CDC::GetCurrentBitmap.md)|傳回指向目前選取的 `CBitmap` 物件。|  
|[CDC::GetCurrentBrush](../Topic/CDC::GetCurrentBrush.md)|傳回指向目前選取的 `CBrush` 物件。|  
|[CDC::GetCurrentFont](../Topic/CDC::GetCurrentFont.md)|傳回指向目前選取的 `CFont` 物件。|  
|[CDC::GetCurrentPalette](../Topic/CDC::GetCurrentPalette.md)|傳回指向目前選取的 `CPalette` 物件。|  
|[CDC::GetCurrentPen](../Topic/CDC::GetCurrentPen.md)|傳回指向目前選取的 `CPen` 物件。|  
|[CDC::GetCurrentPosition](../Topic/CDC::GetCurrentPosition.md)|擷取畫筆的目前位置 \(以邏輯座標\)。|  
|[CDC::GetDCBrushColor](../Topic/CDC::GetDCBrushColor.md)|擷取目前筆刷的色彩。|  
|[CDC::GetDCPenColor](../Topic/CDC::GetDCPenColor.md)|擷取目前畫筆色彩。|  
|[CDC::GetDeviceCaps](../Topic/CDC::GetDeviceCaps.md)|擷取指定的一種有關特定顯示裝置功能的裝置特定資訊。|  
|[CDC::GetFontData](../Topic/CDC::GetFontData.md)|從可調整的字型檔案擷取字型度量資訊。  擷取的資訊由指定的位移字型檔位置和訊息長度傳回所識別。|  
|[CDC::GetFontLanguageInfo](../Topic/CDC::GetFontLanguageInfo.md)|傳回目前選取的字型資訊的指定顯示內容的。|  
|[CDC::GetGlyphOutline](../Topic/CDC::GetGlyphOutline.md)|擷取外框曲線或點陣圖中字元的以目前的字型。|  
|[CDC::GetGraphicsMode](../Topic/CDC::GetGraphicsMode.md)|擷取指定之裝置內容中目前圖形模式。|  
|[CDC::GetHalftoneBrush](../Topic/CDC::GetHalftoneBrush.md)|擷取半色調的筆刷。|  
|[CDC::GetKerningPairs](../Topic/CDC::GetKerningPairs.md)|擷取針對指定之裝置內容中目前選取的字型的字元字元間距調整為。|  
|[CDC::GetLayout](../Topic/CDC::GetLayout.md)|擷取裝置內容 \(DC\) 的配置。  設定可以為由左至右 \(預設值\) 或由右至左 \(反映\)。|  
|[CDC::GetMapMode](../Topic/CDC::GetMapMode.md)|擷取目前對應模式。|  
|[CDC::GetMiterLimit](../Topic/CDC::GetMiterLimit.md)|傳回裝置內容的斜接限制。|  
|[CDC::GetNearestColor](../Topic/CDC::GetNearestColor.md)|擷取最接近的邏輯色彩為特定裝置可以表示的指定邏輯色彩。|  
|[CDC::GetOutlineTextMetrics](../Topic/CDC::GetOutlineTextMetrics.md)|擷取 TrueType 字型的字型度量資訊。|  
|[CDC::GetOutputCharWidth](../Topic/CDC::GetOutputCharWidth.md)|從使用輸出裝置內容目前的字型在字元的連續群組中擷取個別字元的寬度。|  
|[CDC::GetOutputTabbedTextExtent](../Topic/CDC::GetOutputTabbedTextExtent.md)|計算一個字串的寬度和高度會以輸出裝置內容的。|  
|[CDC::GetOutputTextExtent](../Topic/CDC::GetOutputTextExtent.md)|計算文字行的寬度和高度會以輸出裝置內容的使用目前字型決定維度。|  
|[CDC::GetOutputTextMetrics](../Topic/CDC::GetOutputTextMetrics.md)|從輸出裝置內容中擷取目前的字型度量資訊。|  
|[CDC::GetPath](../Topic/CDC::GetPath.md)|擷取定義線條的端點的座標，曲線並按下控制項中選取到裝置內容中的路徑中找到。|  
|[CDC::GetPixel](../Topic/CDC::GetPixel.md)|擷取像素的 RGB 色彩值在指定的點。|  
|[CDC::GetPolyFillMode](../Topic/CDC::GetPolyFillMode.md)|擷取目前多邊形填滿模式。|  
|[CDC::GetROP2](../Topic/CDC::GetROP2.md)|擷取目前的繪圖模式。|  
|[CDC::GetSafeHdc](../Topic/CDC::GetSafeHdc.md)|傳回 [CDC::m\_hDC](../Topic/CDC::m_hDC.md)，輸出裝置內容。|  
|[CDC::GetStretchBltMode](../Topic/CDC::GetStretchBltMode.md)|擷取目前的點陣圖縮放模式。|  
|[CDC::GetTabbedTextExtent](../Topic/CDC::GetTabbedTextExtent.md)|計算一個字串的寬度和高度會以屬性的裝置內容。|  
|[CDC::GetTextAlign](../Topic/CDC::GetTextAlign.md)|擷取文字對齊旗標。|  
|[CDC::GetTextCharacterExtra](../Topic/CDC::GetTextCharacterExtra.md)|擷取數量的目前設定 intercharacter 延伸。|  
|[CDC::GetTextColor](../Topic/CDC::GetTextColor.md)|擷取目前的文字色彩。|  
|[CDC::GetTextExtent](../Topic/CDC::GetTextExtent.md)|計算文字行的寬度和高度會以屬性的裝置內容的使用目前字型決定維度。|  
|[CDC::GetTextExtentExPointI](../Topic/CDC::GetTextExtentExPointI.md)|擷取字元數在指定之空間內適當之指定的字串和使用這些字元為每一個文字範圍填入陣列。|  
|[CDC::GetTextExtentPointI](../Topic/CDC::GetTextExtentPointI.md)|擷取指定之陣列的寬度和高度圖像索引。|  
|[CDC::GetTextFace](../Topic/CDC::GetTextFace.md)|複製目前字型的字樣名稱輸入緩衝區，以 null 結尾的字串。|  
|[CDC::GetTextMetrics](../Topic/CDC::GetTextMetrics.md)|從屬性的裝置內容中擷取目前的字型度量資訊。|  
|[CDC::GetViewportExt](../Topic/CDC::GetViewportExt.md)|擷取檢視區的 x 和 y 程度。|  
|[CDC::GetViewportOrg](../Topic/CDC::GetViewportOrg.md)|擷取檢視區還原點的 X 座標和 Y 座標。|  
|[CDC::GetWindow](../Topic/CDC::GetWindow.md)|傳回視窗與顯示裝置內容。|  
|[CDC::GetWindowExt](../Topic/CDC::GetWindowExt.md)|對關聯之視窗的 x 和 y 程度。|  
|[CDC::GetWindowOrg](../Topic/CDC::GetWindowOrg.md)|擷取 x 和 y 座標關聯之視窗的原點。|  
|[CDC::GetWorldTransform](../Topic/CDC::GetWorldTransform.md)|擷取目前全局空間網頁空間轉換。|  
|[CDC::GradientFill](../Topic/CDC::GradientFill.md)|填滿矩形和具有 gradating 三角形的色彩的結構。|  
|[CDC::GrayString](../Topic/CDC::GrayString.md)|在指定位置繪製呈現暗灰色 \(灰色\) 文字。|  
|[CDC::HIMETRICtoDP](../Topic/CDC::HIMETRICtoDP.md)|轉換 **HIMETRIC** 單位為單位\)。|  
|[CDC::HIMETRICtoLP](../Topic/CDC::HIMETRICtoLP.md)|轉換 **HIMETRIC** 單元套用到邏輯單位中。|  
|[CDC::IntersectClipRect](../Topic/CDC::IntersectClipRect.md)|藉由建立目前區域和矩形的交集來建立新的裁剪區域。|  
|[CDC::InvertRect](../Topic/CDC::InvertRect.md)|反轉矩形的內容。|  
|[CDC::InvertRgn](../Topic/CDC::InvertRgn.md)|在區域反轉色彩。|  
|[CDC::IsPrinting](../Topic/CDC::IsPrinting.md)|判斷裝置內容是否用於列印。|  
|[CDC::LineTo](../Topic/CDC::LineTo.md)|從目前位置繪製線條，，但不包括，按。|  
|[CDC::LPtoDP](../Topic/CDC::LPtoDP.md)|呈現邏輯單位的單位。|  
|[CDC::LPtoHIMETRIC](../Topic/CDC::LPtoHIMETRIC.md)|呈現邏輯單位的 **HIMETRIC** 單位。|  
|[CDC::MaskBlt](../Topic/CDC::MaskBlt.md)|使用指定的遮罩和光柵作業 \(Raster，合併色彩資料來源和目的點陣圖。|  
|[CDC::ModifyWorldTransform](../Topic/CDC::ModifyWorldTransform.md)|使用指定的方式，變更裝置內容的全局轉換。|  
|[CDC::MoveTo](../Topic/CDC::MoveTo.md)|會將目前的位置。|  
|[CDC::OffsetClipRgn](../Topic/CDC::OffsetClipRgn.md)|移動指定裝置的裁剪區域。|  
|[CDC::OffsetViewportOrg](../Topic/CDC::OffsetViewportOrg.md)|修改檢視區還原點相對於目前檢視區還原點的座標。|  
|[CDC::OffsetWindowOrg](../Topic/CDC::OffsetWindowOrg.md)|修改視窗原點座標相對於目前視窗的原點。|  
|[CDC::PaintRgn](../Topic/CDC::PaintRgn.md)|使用這個選項的筆刷來填滿區域。|  
|[CDC::PatBlt](../Topic/CDC::PatBlt.md)|建立一個位元組合。|  
|[CDC::Pie](../Topic/CDC::Pie.md)|繪製派形。|  
|[CDC::PlayMetaFile](../Topic/CDC::PlayMetaFile.md)|播放指定中繼檔的內容在特定裝置上。  `PlayMetaFile` 增強版本顯示在特定加強型格式中繼檔中的圖片。  此中繼資料可以播放任意次數。|  
|[CDC::PlgBlt](../Topic/CDC::PlgBlt.md)|在來源裝置內容執行位元的位元區塊傳輸色彩資料從指定之矩形加入至指定的平行四邊形中指定的裝置內容。|  
|[CDC::PolyBezier](../Topic/CDC::PolyBezier.md)|繪製一個或多個 Bzier 曲線。  不使用目前位置也不會更新。|  
|[CDC::PolyBezierTo](../Topic/CDC::PolyBezierTo.md)|繪製一個或多個 Bzier 曲線，並將目前位置移至最後一 Bzier 曲線的結束點。|  
|[CDC::PolyDraw](../Topic/CDC::PolyDraw.md)|繪製一組線段和 Bzier 曲線。  這個函式會更新目前位置。|  
|[CDC::Polygon](../Topic/CDC::Polygon.md)|繪製由兩個以上的點 \(頂點\) 的多邊形連接由線條。|  
|[CDC::Polyline](../Topic/CDC::Polyline.md)|繪製一組連結指定的點的直線線段。|  
|[CDC::PolylineTo](../Topic/CDC::PolylineTo.md)|繪製一個或多個直線和移動目前位置移至最後一行的結束點。|  
|[CDC::PolyPolygon](../Topic/CDC::PolyPolygon.md)|建立使用目前多邊形填滿模式，填滿的兩個以上的多邊形。  多邊形可能是斷續或它們可能會重疊。|  
|[CDC::PolyPolyline](../Topic/CDC::PolyPolyline.md)|繪製連接的直線線段多個數列。  這個函式不會使用目前位置也不會更新。|  
|[CDC::PtVisible](../Topic/CDC::PtVisible.md)|指定所指定的點是否在裁剪區域中。|  
|[CDC::RealizePalette](../Topic/CDC::RealizePalette.md)|將目前的邏輯調色盤的調色盤項目至系統調色盤。|  
|[CDC::Rectangle](../Topic/CDC::Rectangle.md)|使用目前的筆刷，繪製矩形使用畫筆的目前筆和填滿它。|  
|[CDC::RectVisible](../Topic/CDC::RectVisible.md)|判斷指定的矩形的任何部分是否在裁剪區域之間。|  
|[CDC::ReleaseAttribDC](../Topic/CDC::ReleaseAttribDC.md)|釋放 `m_hAttribDC`，屬性的裝置內容。|  
|[CDC::ReleaseOutputDC](../Topic/CDC::ReleaseOutputDC.md)|釋放 `m_hDC`，輸出裝置內容。|  
|[CDC::ResetDC](../Topic/CDC::ResetDC.md)|更新 `m_hAttribDC` 裝置內容。|  
|[CDC::RestoreDC](../Topic/CDC::RestoreDC.md)|還原裝置內容至先前的狀態儲存 `SaveDC`。|  
|[CDC::RoundRect](../Topic/CDC::RoundRect.md)|繪製圓角矩形使用畫筆的目前筆和填滿使用目前的筆刷。|  
|[CDC::SaveDC](../Topic/CDC::SaveDC.md)|儲存裝置內容的目前狀態。|  
|[CDC::ScaleViewportExt](../Topic/CDC::ScaleViewportExt.md)|修改檢視區範圍相對於目前值。|  
|[CDC::ScaleWindowExt](../Topic/CDC::ScaleWindowExt.md)|修改視窗 \(相對於目前值。|  
|[CDC::ScrollDC](../Topic/CDC::ScrollDC.md)|垂直和水平捲動的矩形。|  
|[CDC::SelectClipPath](../Topic/CDC::SelectClipPath.md)|選取目前路徑當做裁剪區域為裝置內容，將新的區域與任何現有的裁剪區域是使用指定的模式。|  
|[CDC::SelectClipRgn](../Topic/CDC::SelectClipRgn.md)|使用指定的模式，合併特定區域和目前裁剪區域。|  
|[CDC::SelectObject](../Topic/CDC::SelectObject.md)|選取要繪製的物件 \(例如畫筆的 GDI。|  
|[CDC::SelectPalette](../Topic/CDC::SelectPalette.md)|選取邏輯調色盤。|  
|[CDC::SelectStockObject](../Topic/CDC::SelectStockObject.md)|選取視窗中的其中一個預先定義的內建 \(Stock\) 字型、筆刷、畫筆。|  
|[CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)|設定視窗呼叫的另一個由程式設計人員提供的回呼函式，如果必須中止列印工作。|  
|[CDC::SetArcDirection](../Topic/CDC::SetArcDirection.md)|設定為也會使用的繪製方向，而矩形運作。|  
|[CDC::SetAttribDC](../Topic/CDC::SetAttribDC.md)|設定 `m_hAttribDC`，屬性的裝置內容。|  
|[CDC::SetBkColor](../Topic/CDC::SetBkColor.md)|設定目前的背景色彩。|  
|[CDC::SetBkMode](../Topic/CDC::SetBkMode.md)|設定背景方式。|  
|[CDC::SetBoundsRect](../Topic/CDC::SetBoundsRect.md)|控制項的週框矩形資訊的累積指定的裝置內容。|  
|[CDC::SetBrushOrg](../Topic/CDC::SetBrushOrg.md)|在下一個筆刷指定源自選取到裝置內容中。|  
|[CDC::SetColorAdjustment](../Topic/CDC::SetColorAdjustment.md)|使用指定值，設定裝置內容的色彩調整值。|  
|[CDC::SetDCBrushColor](../Topic/CDC::SetDCBrushColor.md)|設定目前筆刷的色彩。|  
|[CDC::SetDCPenColor](../Topic/CDC::SetDCPenColor.md)|設定目前畫筆色彩。|  
|[CDC::SetGraphicsMode](../Topic/CDC::SetGraphicsMode.md)|設定指定之裝置內容中目前圖形模式。|  
|[CDC::SetLayout](../Topic/CDC::SetLayout.md)|變更裝置內容 \(DC\) 的配置。|  
|[CDC::SetMapMode](../Topic/CDC::SetMapMode.md)|設定目前對應模式。|  
|[CDC::SetMapperFlags](../Topic/CDC::SetMapperFlags.md)|修改字型對應器所使用的演算法，會將邏輯字型給實體字型時。|  
|[CDC::SetMiterLimit](../Topic/CDC::SetMiterLimit.md)|設定斜接長度的限制為裝置內容聯結。|  
|[CDC::SetOutputDC](../Topic/CDC::SetOutputDC.md)|設定 `m_hDC`，輸出裝置內容。|  
|[CDC::SetPixel](../Topic/CDC::SetPixel.md)|設定為在指定的點為指定色彩的近似值。|  
|[CDC::SetPixelV](../Topic/CDC::SetPixelV.md)|設定為在指定的座標轉換為指定的色彩的近似值。  因為它不需要傳回實際繪製，點的色彩值`SetPixelV` 比 `SetPixel` 快速。|  
|[CDC::SetPolyFillMode](../Topic/CDC::SetPolyFillMode.md)|將多邊形填滿模式。|  
|[CDC::SetROP2](../Topic/CDC::SetROP2.md)|設定目前的繪圖模式。|  
|[CDC::SetStretchBltMode](../Topic/CDC::SetStretchBltMode.md)|設定這個點陣圖會自動縮放的方式。|  
|[CDC::SetTextAlign](../Topic/CDC::SetTextAlign.md)|將文字對齊設定旗標。|  
|[CDC::SetTextCharacterExtra](../Topic/CDC::SetTextCharacterExtra.md)|設定數量 intercharacter 延伸。|  
|[CDC::SetTextColor](../Topic/CDC::SetTextColor.md)|設定文字色彩。|  
|[CDC::SetTextJustification](../Topic/CDC::SetTextJustification.md)|將命名空間加入至字串的分行符號字元。|  
|[CDC::SetViewportExt](../Topic/CDC::SetViewportExt.md)|設定檢視區的 x 和 y 程度。|  
|[CDC::SetViewportOrg](../Topic/CDC::SetViewportOrg.md)|設定檢視區還原點。|  
|[CDC::SetWindowExt](../Topic/CDC::SetWindowExt.md)|設定關聯之視窗的 x 和 y 程度。|  
|[CDC::SetWindowOrg](../Topic/CDC::SetWindowOrg.md)|設定裝置內容的 Windows 原點。|  
|[CDC::SetWorldTransform](../Topic/CDC::SetWorldTransform.md)|設定目前全局空間網頁空間轉換。|  
|[CDC::StartDoc](../Topic/CDC::StartDoc.md)|告知裝置驅動程式新列印工作開始。|  
|[CDC::StartPage](../Topic/CDC::StartPage.md)|告知裝置驅動程式新網頁開始。|  
|[CDC::StretchBlt](../Topic/CDC::StretchBlt.md)|從來源矩形將點陣圖和裝置目的矩形，必要時，自動縮放或壓縮點陣圖至適合目的矩形的維度。|  
|[CDC::StrokeAndFillPath](../Topic/CDC::StrokeAndFillPath.md)|使用畫筆的目前筆，藉由使用目前的筆刷，關閉路徑中有任何開放圖形，加刪除線路徑的外框，並填入其內部。|  
|[CDC::StrokePath](../Topic/CDC::StrokePath.md)|使用畫筆的目前筆，呈現指定的路徑。|  
|[CDC::TabbedTextOut](../Topic/CDC::TabbedTextOut.md)|在指定位置將一個字串，再展開  索引標籤將這個值指定定位停駐點 \(Tab Stop\) 位置。|  
|[CDC::TextOut](../Topic/CDC::TextOut.md)|使用目前選取的字型，在指定的位置會將一個字串。|  
|[CDC::TransparentBlt](../Topic/CDC::TransparentBlt.md)|從指定的來源裝置內容傳輸的色彩資料位元區塊插入目的裝置內容，並以指定的色彩透明傳輸。|  
|[CDC::UpdateColors](../Topic/CDC::UpdateColors.md)|也可以比對工作區的目前色彩更新裝置內容的工作區域為根據像素 x 像素為基礎的系統調色盤。|  
|[CDC::WidenPath](../Topic/CDC::WidenPath.md)|重新定義目前路徑設定為要繪製的區域，如果路徑描邊的畫筆使用目前選取到裝置內容中。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CDC::operator HDC](../Topic/CDC::operator%20HDC.md)|擷取裝置內容的控制代碼。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDC::m\_hAttribDC](../Topic/CDC::m_hAttribDC.md)|這 `CDC` 使用物件的屬性的裝置內容。|  
|[CDC::m\_hDC](../Topic/CDC::m_hDC.md)|這 `CDC` 物件使用的輸出裝置內容。|  
  
## 備註  
 `CDC` 物件提供成員函式的裝置內容 \(例如，顯示或印表機，以及成員的工作以顯示內容與視窗的工作區。  
  
 藉由 `CDC` 物件的成員函式進行繪製。  類別會提供裝置內容作業提供成員函式，使用繪圖工具、型別安全圖形裝置介面 \(GDI\) 物件選取及使用色彩和調色盤。  它會取得也提供成員函式和裝置的屬性，對應，與檢視區 \(Viewport\) 的工作，包括視窗程度的工作，轉換座標，使用或處理地區、裁剪、繪製線條和繪製簡單圖案、橢圓形和多邊形。  成員函式使用繪製文字也提供工作，字型，使用印表機逸出，捲動和播放中繼檔。  
  
 若要使用 `CDC` 物件，請建構它，然後呼叫其成員函式同時使用裝置內容的 Windows 函式。  
  
> [!NOTE]
>  在 Windows 95 \/98 下，所有螢幕座標是限制為 16 位元。  因此， `int` 傳遞至 `CDC` 成員函式會 32768 到 32767 範圍必須在。  
  
 針對特定使用， MFC 程式庫提供從 `CDC` 衍生的數個類別。  `CPaintDC` 封裝會呼叫 `BeginPaint` 和 `EndPaint`。  `CClientDC` 處理顯示內容與視窗的工作區。  `CWindowDC` 處理顯示內容與整個視窗，包括其架構和控制項。  `CMetaFileDC` 使裝置內容和中繼檔。  
  
 `CDC` 為反轉裝置內容之配置的兩個成員函式， [GetLayout](../Topic/CDC::GetLayout.md) 和 [SetLayout](../Topic/CDC::SetLayout.md)，，不繼承自視窗的配置。  這類由右至左的方向為文化特性撰寫的應用程式是必要的，例如阿拉伯文或希伯來文，其中字元配置不是西歐標準。  
  
 `CDC` 包含兩個裝置內容， [m\_hDC](../Topic/CDC::m_hDC.md) ，並 [m\_hAttribDC](../Topic/CDC::m_hAttribDC.md)，在這種情況下， `CDC` 建立物件，參考相同的裝置。  `CDC` 導向所有輸出 GDI 對 `m_hDC` 和大部分屬性 GDI 對 `m_hAttribDC`。  \(屬性呼叫的範例是 `GetTextColor`，反之， `SetTextColor` 是輸出呼叫\)。  
  
 例如，架構會使用這兩個裝置內容實作會將輸出傳送至中繼檔的 `CMetaFileDC` 物件，當讀取實體裝置時的屬性。  預覽列印在架構的方式來實作。  您也可以透過類似的方式也可以使用兩個裝置內容以您應用程式特定的程式碼。  
  
 在中，您可能需要從 `m_hDC` 和 `m_hAttribDC` 裝置內容時，文字度量資訊使用。  下列函式提供這項功能:  
  
|使用 m\_hAttribDC|使用 m\_hDC|  
|---------------------|---------------|  
|[GetTextExtent](../Topic/CDC::GetTextExtent.md)|[GetOutputTextExtent](../Topic/CDC::GetOutputTextExtent.md)|  
|[GetTabbedTextExtent](../Topic/CDC::GetTabbedTextExtent.md)|[GetOutputTabbedTextExtent](../Topic/CDC::GetOutputTabbedTextExtent.md)|  
|[GetTextMetrics](../Topic/CDC::GetTextMetrics.md)|[GetOutputTextMetrics](../Topic/CDC::GetOutputTextMetrics.md)|  
|[GetCharWidth](../Topic/CDC::GetCharWidth.md)|[GetOutputCharWidth](../Topic/CDC::GetOutputCharWidth.md)|  
  
 如需 `CDC`的資訊，請參閱 [裝置內容。](../../mfc/device-contexts.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDC`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPaintDC Class](../../mfc/reference/cpaintdc-class.md)   
 [CWindowDC Class](../../mfc/reference/cwindowdc-class.md)   
 [CClientDC Class](../../mfc/reference/cclientdc-class.md)   
 [CMetaFileDC Class](../../mfc/reference/cmetafiledc-class.md)