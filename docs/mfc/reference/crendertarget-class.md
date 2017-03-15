---
title: "CRenderTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRenderTarget
- afxrendertarget/CRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CRenderTarget class
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6f77d482e7ee3bf0798ad488067893b3712aac62
ms.lasthandoff: 02/24/2017

---
# <a name="crendertarget-class"></a>CRenderTarget 類別
ID2D1RenderTarget 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CRenderTarget : public CObject;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRenderTarget::CRenderTarget](#crendertarget)|建構 CRenderTarget 物件。|  
|[CRenderTarget:: ~ CRenderTarget](#crendertarget__~crendertarget)|解構函式。 呈現目標物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRenderTarget::Attach](#attach)|會附加至現有的呈現目標物件的介面|  
|[CRenderTarget::BeginDraw](#begindraw)|在此呈現目標上繪製的初始化。|  
|[CRenderTarget::Clear](#clear)|清除指定的色彩來繪製的區域。|  
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|將 GDI 色彩和 alpha 值轉換成 D2D1_COLOR_F 物件。|  
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|建立新的點陣圖呈現目標使用期間中繼螢幕的繪圖與目前的呈現目標。|  
|[CRenderTarget::Destroy](#destroy)|刪除一個或多個資源|  
|[CRenderTarget::Detach](#detach)|中斷連結物件中的呈現目標介面|  
|[CRenderTarget::DrawBitmap](#drawbitmap)|繪製格式化指定的 IDWriteTextLayout 物件所描述的文字。|  
|[CRenderTarget::DrawEllipse](#drawellipse)|繪製指定的橢圓形使用指定的筆劃樣式的外框。|  
|[CRenderTarget::DrawGeometry](#drawgeometry)|繪製指定的幾何，使用指定的筆劃樣式的外框。|  
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|繪製指定的圖像 （glyph）。|  
|[CRenderTarget::DrawLine](#drawline)|使用指定的筆劃樣式指定的點之間繪製一條線。|  
|[CRenderTarget::DrawRectangle](#drawrectangle)|繪製筆劃樣式與指定的維度的矩形外的框。|  
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|繪製指定的圓角矩形，使用指定的筆劃樣式的外框。|  
|[CRenderTarget::DrawText](#drawtext)|繪製指定的文字使用 IDWriteTextFormat 物件所提供的格式資訊。|  
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|繪製格式化指定的 IDWriteTextLayout 物件所描述的文字。|  
|[CRenderTarget::EndDraw](#enddraw)|結束繪製作業的呈現目標，並指出目前的錯誤狀態及相關聯的標記。|  
|[CRenderTarget::FillEllipse](#fillellipse)|繪製指定的橢圓形內部。|  
|[CRenderTarget::FillGeometry](#fillgeometry)|繪製指定的幾何的內部。|  
|[CRenderTarget::FillMesh](#fillmesh)|繪製指定之網狀結構的內部。|  
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|適用於所指定的點陣圖為筆刷不透明遮罩，並使用該筆刷繪製區域的呈現目標。|  
|[CRenderTarget::FillRectangle](#fillrectangle)|繪製指定矩形內部。|  
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|繪製指定之圓角矩形內部。|  
|[CRenderTarget::Flush](#flush)|執行所有暫止的繪製命令。|  
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|擷取非文字繪圖作業的目前反鋸齒功能模式。|  
|[CRenderTarget::GetDpi](#getdpi)|傳回呈現目標的每英吋點數 (DPI)|  
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|取得大小上限，以支援呈現目標的任何一個點陣圖維度的裝置相關單位 （像素）|  
|[CRenderTarget::GetPixelFormat](#getpixelformat)|擷取呈現目標的像素格式和 alpha 模式|  
|[CRenderTarget::GetPixelSize](#getpixelsize)|傳回以裝置像素為單位的呈現目標的大小|  
|[CRenderTarget::GetRenderTarget](#getrendertarget)|傳回 ID2D1RenderTarget 介面|  
|[CRenderTarget::GetSize](#getsize)|傳回與裝置無關的像素為單位的呈現目標大小|  
|[CRenderTarget::GetTags](#gettags)|取得後續繪圖作業的標籤。|  
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|取得目前的反鋸齒功能模式的文字和繪製作業的圖像 （glyph）。|  
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|擷取目前的文字轉譯選項呈現目標。|  
|[CRenderTarget::GetTransform](#gettransform)|將指定的轉換套用至呈現目標，取代現有的轉換。 所有後續的繪圖作業發生在轉換後的空間。|  
|[CRenderTarget::IsSupported](#issupported)|指出呈現目標是否支援指定的屬性|  
|[CRenderTarget::IsValid](#isvalid)|檢查資源的有效性|  
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|移除呈現目標的軸對齊的最後一個剪輯。 會呼叫這個方法之後，多媒體項目不會再套用至後續繪製作業。|  
|[CRenderTarget::PopLayer](#poplayer)|停止將繪圖作業重新導向至指定的最後一個 PushLayer 層呼叫。|  
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|移除呈現目標的軸對齊的最後一個剪輯。 會呼叫這個方法之後，多媒體項目不會再套用至後續繪製作業。|  
|[CRenderTarget::PushLayer](#pushlayer)|將指定的圖層加入至呈現目標，讓呼叫 PopLayer 之前接收到所有後續的繪圖作業。|  
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|將呈現目標的繪圖狀態設定所指定的 ID2D1DrawingStateBlock。|  
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|將繪圖的目前狀態儲存至指定的 ID2D1DrawingStateBlock。|  
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|設定呈現目標的反鋸齒功能模式。 反鋸齒功能模式適用於所有後續繪製作業，不包括文字和繪製作業的圖像 （glyph）。|  
|[CRenderTarget::SetDpi](#setdpi)|設定每英吋點數 (DPI) 呈現目標。|  
|[CRenderTarget::SetTags](#settags)|指定後續繪圖作業的標籤。|  
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|指定要用於後續文字和圖像繪製作業的反鋸齒功能模式。|  
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|指定要套用至所有後續文字和繪製作業的圖像的文字呈現選項。|  
|[CRenderTarget::SetTransform](#settransform)|多載。 將指定的轉換套用至呈現目標，取代現有的轉換。 所有後續的繪圖作業發生在轉換後的空間。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](#verifyresource)|確認 CD2DResource 物件的有效性。如果它不存在，則建立的物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|傳回 ID2D1RenderTarget 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CRenderTarget::m_lstResources](#m_lstresources)|一份 CD2DResource 物件的指標。|  
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|ID2D1RenderTarget 物件的指標。|  
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|包含預設文字格式的 CD2DTextFormat 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="a-namedtorcrendertargeta--crendertargetcrendertarget"></a><a name="_dtorcrendertarget"></a>CRenderTarget:: ~ CRenderTarget  
 解構函式。 呈現目標物件終結時呼叫。  
  
```  
virtual ~CRenderTarget();
```  
  
##  <a name="a-nameattacha--crendertargetattach"></a><a name="attach"></a>CRenderTarget::Attach  
 會附加至現有的呈現目標物件的介面  
  
```  
void Attach(ID2D1RenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 現有的呈現目標介面。 不能是 NULL  
  
##  <a name="a-namebegindrawa--crendertargetbegindraw"></a><a name="begindraw"></a>CRenderTarget::BeginDraw  
 在此呈現目標上繪製的初始化。  
  
```  
void BeginDraw();
```  
  
##  <a name="a-namecleara--crendertargetclear"></a><a name="clear"></a>CRenderTarget::Clear  
 清除指定的色彩來繪製的區域。  
  
```  
void Clear(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>參數  
 `color`  
 套繪圖區域的色彩。  
  
##  <a name="a-namecolorreftod2dcolora--crendertargetcolorreftod2dcolor"></a><a name="colorref_to_d2dcolor"></a>CRenderTarget::COLORREF_TO_D2DCOLOR  
 將 GDI 色彩和 alpha 值轉換成 D2D1_COLOR_F 物件。  
  
```  
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,  
    int nAlpha = 255);
```  
  
### <a name="parameters"></a>參數  
 `color`  
 RGB 值。  
  
 `nAlpha`  
  
### <a name="return-value"></a>傳回值  
 D2D1_COLOR_F 值。  
  
##  <a name="a-namecreatecompatiblerendertargeta--crendertargetcreatecompatiblerendertarget"></a><a name="createcompatiblerendertarget"></a>CRenderTarget::CreateCompatibleRenderTarget  
 建立新的點陣圖呈現目標使用期間中繼螢幕的繪圖與目前的呈現目標。  
  
```  
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,  
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.), 
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0), 
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,  
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>參數  
 `bitmapTarget`  
 此方法傳回時，包含新的點陣圖呈現目標的指標位址。 這個參數會以未初始化的狀態傳遞。  
  
 `sizeDesired`  
 新的呈現目標，如果應該不同於原始的與裝置無關像素為單位的所需的大小呈現目標，或為 NULL。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `sizePixelDesired`  
 新的呈現目標，如果應該不同於原始的像素為單位的所需的大小呈現目標，或為 NULL。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `desiredFormat`  
 新 alpha 模式與所要的像素格式呈現目標，或為 NULL。 如果像素格式設定為 DXGI_FORMAT_UNKNOWN 或這個參數為 null，新的呈現目標做為原始呈現目標，就會使用相同的像素格式。 如果 alpha 模式是 D2D1_ALPHA_MODE_UNKNOWN 或這個參數是 NULL，新的呈現目標的 alpha 模式會預設為 D2D1_ALPHA_MODE_PREMULTIPLIED。 如需支援的像素格式的資訊，請參閱支援的像素格式和 Alpha 模式。  
  
 `options`  
 指定新的呈現目標是否必須使用 GDI 相容的值。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="a-namecrendertargeta--crendertargetcrendertarget"></a><a name="crendertarget"></a>CRenderTarget::CRenderTarget  
 建構 CRenderTarget 物件。  
  
```  
CRenderTarget();
```  
  
##  <a name="a-namedestroya--crendertargetdestroy"></a><a name="destroy"></a>CRenderTarget::Destroy  
 刪除一個或多個資源  
  
```  
BOOL Destroy(BOOL bDeleteResources = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bDeleteResources`  
 如果 bDeleteResources 為 TRUE 時，會自動終結 m_lstResources 中的所有資源。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE  
  
##  <a name="a-namedetacha--crendertargetdetach"></a><a name="detach"></a>CRenderTarget::Detach  
 中斷連結物件中的呈現目標介面  
  
```  
ID2D1RenderTarget* Detach ();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的指標會呈現目標的介面。  
  
##  <a name="a-namedrawbitmapa--crendertargetdrawbitmap"></a><a name="drawbitmap"></a>CRenderTarget::DrawBitmap  
 繪製格式化指定的 IDWriteTextLayout 物件所描述的文字。  
  
```  
void DrawBitmap(
    CD2DBitmap* pBitmap,  
    const CD2DRectF& rectDest,  
    float fOpacity = 1.0,  
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,  
    const CD2DRectF* pRectSrc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pBitmap`  
 要轉譯的點陣圖。  
  
 `rectDest`  
 大小和位置，在呈現目標的座標空間中的區域繪製了點陣圖即與裝置無關像素為單位。 如果不是井然有序的矩形，不繪製任何內容，但是呈現目標不能進入錯誤狀態。  
  
 `fOpacity`  
 介於 0.0 和 1.0 f，含之間的值，指定要套用至點陣圖; 的不透明度值此值乘的 alpha 值的點陣圖的內容。  
  
 `interpolationMode`  
 如果點陣圖是縮放或旋轉繪製作業，請使用插補法模式。  
  
 `pRectSrc`  
 大小和位置、 與裝置無關點陣圖的座標空間，以繪製點陣圖內的區域中的像素為單位。  
  
##  <a name="a-namedrawellipsea--crendertargetdrawellipse"></a><a name="drawellipse"></a>CRenderTarget::DrawEllipse  
 繪製指定的橢圓形使用指定的筆劃樣式的外框。  
  
```  
void DrawEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `ellipse`  
 位置與裝置無關的像素繪製橢圓形的半徑。  
  
 `pBrush`  
 用來繪製橢圓形的外框的筆刷。  
  
 `fStrokeWidth`  
 橢圓形的筆觸粗細。 筆觸被中心橢圓形的外框。  
  
 `strokeStyle`  
 要套用至橢圓形的外框，則為 NULL 來繪製實心筆劃筆劃的樣式。  
  
##  <a name="a-namedrawgeometrya--crendertargetdrawgeometry"></a><a name="drawgeometry"></a>CRenderTarget::DrawGeometry  
 繪製指定的幾何，使用指定的筆劃樣式的外框。  
  
```  
void DrawGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pGeometry`  
 要繪製的幾何。  
  
 `pBrush`  
 用來繪製幾何筆劃的筆刷。  
  
 `fStrokeWidth`  
 幾何筆劃粗細。 筆觸被中心幾何外框。  
  
 `strokeStyle`  
 要套用至幾何外框，則為 NULL 來繪製實心筆劃筆劃的樣式。  
  
##  <a name="a-namedrawglyphruna--crendertargetdrawglyphrun"></a><a name="drawglyphrun"></a>CRenderTarget::DrawGlyphRun  
 繪製指定的圖像 （glyph）。  
  
```  
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,  
    const DWRITE_GLYPH_RUN& glyphRun,  
    CD2DBrush* pForegroundBrush,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>參數  
 `ptBaseLineOrigin`  
 在與裝置無關的像素，圖像 （glyph） 的基準的來源。  
  
 `glyphRun`  
 要呈現的圖像。  
  
 `pForegroundBrush`  
 用來繪製指定的圖像 （glyph） 的筆刷。  
  
 `measuringMode`  
 值，指出如何使用圖像 （glyph） 度量資訊來進行格式化時，測量的文字。 預設值是 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="a-namedrawlinea--crendertargetdrawline"></a><a name="drawline"></a>CRenderTarget::DrawLine  
 使用指定的筆劃樣式指定的點之間繪製一條線。  
  
```  
void DrawLine(
    const CD2DPointF& ptFrom,  
    const CD2DPointF& ptTo,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `ptFrom`  
 與裝置無關的像素為單位指定線條的起始點。  
  
 `ptTo`  
 與裝置無關的像素為單位指定線條的終點。  
  
 `pBrush`  
 用來繪製線條的筆劃的筆刷。  
  
 `fStrokeWidth`  
 值大於或等於 0.0 f 指定筆劃的寬度。 如果未指定此參數，它會預設為 1.0 f。 筆觸是列上置中。  
  
 `strokeStyle`  
 小畫家，或 NULL 來繪製一條實線筆劃的樣式。  
  
##  <a name="a-namedrawrectanglea--crendertargetdrawrectangle"></a><a name="drawrectangle"></a>CRenderTarget::DrawRectangle  
 繪製筆劃樣式與指定的維度的矩形外的框。  
  
```  
void DrawRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 若要繪製，在與裝置無關的像素矩形的維度  
  
 `pBrush`  
 用來繪製的矩形筆劃的筆刷  
  
 `fStrokeWidth`  
 值大於或等於 0.0 f 的指定矩形的筆劃的寬度。 筆觸會集中在矩形外框。  
  
 `strokeStyle`  
 小畫家，或 NULL 來繪製實心筆劃筆劃的樣式。  
  
##  <a name="a-namedrawroundedrectanglea--crendertargetdrawroundedrectangle"></a><a name="drawroundedrectangle"></a>CRenderTarget::DrawRoundedRectangle  
 繪製指定的圓角矩形，使用指定的筆劃樣式的外框。  
  
```  
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `rectRounded`  
 若要繪製，以與裝置無關的像素為單位的圓角矩形維度。  
  
 `pBrush`  
 用來繪製圓角的矩形外框的筆刷。  
  
 `fStrokeWidth`  
 圓角的矩形筆劃的寬度。 筆觸被中心圓角的矩形外框。 預設值為 1.0 f。  
  
 `strokeStyle`  
 圓角的矩形筆劃，則為 NULL 來繪製實心筆劃的樣式。 預設值是 NULL。  
  
##  <a name="a-namedrawtexta--crendertargetdrawtext"></a><a name="drawtext"></a>CRenderTarget::DrawText  
 繪製指定的文字使用 IDWriteTextFormat 物件所提供的格式資訊。  
  
```  
void DrawText(
    const CString& strText,  
    const CD2DRectF& rect,  
    CD2DBrush* pForegroundBrush,  
    CD2DTextFormat* textFormat = NULL,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>參數  
 `strText`  
 要繪製的 Unicode 字元陣列指標。  
  
 `rect`  
 在其中繪製文字的區域位置及大小。  
  
 `pForegroundBrush`  
 用來繪製文字的筆刷。  
  
 `textFormat`  
 物件，描述要繪製的文字，例如字型、 字型大小及文字方向的詳細資料的格式。  
  
 `options`  
 值，指出是否應該像素界限對齊文字，以及是否應該修剪文字以配置矩形。 預設值是 D2D1_DRAW_TEXT_OPTIONS_NONE，表示文字應該像素界限對齊，則應該不會遭到裁剪以配置矩形。  
  
 `measuringMode`  
 值，指出如何使用圖像 （glyph） 度量資訊來進行格式化時，測量的文字。 預設值是 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="a-namedrawtextlayouta--crendertargetdrawtextlayout"></a><a name="drawtextlayout"></a>CRenderTarget::DrawTextLayout  
 繪製格式化指定的 IDWriteTextLayout 物件所描述的文字。  
  
```  
void DrawTextLayout(
    const CD2DPointF& ptOrigin,  
    CD2DTextLayout* textLayout,  
    CD2DBrush* pBrushForeground,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>參數  
 `ptOrigin`  
 說明與裝置無關的像素，繪製 textLayout 所描述的文字的左上角的點。  
  
 `textLayout`  
 繪製格式化的文字。 不是繼承自 ID2D1Resource 任何繪製效果都會被忽略。 如果繪製效果繼承自 ID2D1Resource 沒有筆刷，這個方法會失敗，並且呈現目標會放在錯誤狀態。  
  
 `pBrushForeground`  
 用來繪製還沒有筆刷繪製效果 （IDWriteTextLayout::SetDrawingEffect 方法所指定） 與它相關的 textLayout 中的任何文字的筆刷。  
  
 `options`  
 值，指出是否應該像素界限對齊文字，以及是否應該修剪文字以配置矩形。 預設值是 D2D1_DRAW_TEXT_OPTIONS_NONE，表示文字應該像素界限對齊，則應該不會遭到裁剪以配置矩形。  
  
##  <a name="a-nameenddrawa--crendertargetenddraw"></a><a name="enddraw"></a>CRenderTarget::EndDraw  
 結束繪製作業的呈現目標，並指出目前的錯誤狀態及相關聯的標記。  
  
```  
HRESULT EndDraw();
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="a-namefillellipsea--crendertargetfillellipse"></a><a name="fillellipse"></a>CRenderTarget::FillEllipse  
 繪製指定的橢圓形內部。  
  
```  
void FillEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `ellipse`  
 位置，並且以與裝置無關的像素，來繪製橢圓形的半徑。  
  
 `pBrush`  
 筆刷，用來繪製橢圓形內部。  
  
##  <a name="a-namefillgeometrya--crendertargetfillgeometry"></a><a name="fillgeometry"></a>CRenderTarget::FillGeometry  
 繪製指定的幾何的內部。  
  
```  
void FillGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    CD2DBrush* pOpacityBrush = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pGeometry`  
 要繪製的幾何。  
  
 `pBrush`  
 用來繪製幾何的筆刷的內部。  
  
 `pOpacityBrush`  
 若要套用至幾何; 不透明度遮罩沒有不透明度遮罩是 NULL。 如果指定為不透明遮罩 （opacityBrush 參數），則筆刷必須是有其 x 和 y 延伸模式 」 設為 D2D1_EXTEND_MODE_CLAMP ID2D1BitmapBrush。 如需詳細資訊，請參閱＜備註＞一節。  
  
##  <a name="a-namefillmesha--crendertargetfillmesh"></a><a name="fillmesh"></a>CRenderTarget::FillMesh  
 繪製指定之網狀結構的內部。  
  
```  
void FillMesh(
    CD2DMesh* pMesh,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `pMesh`  
 若要繪製網狀結構。  
  
 `pBrush`  
 用來繪製網狀結構的筆刷。  
  
##  <a name="a-namefillopacitymaska--crendertargetfillopacitymask"></a><a name="fillopacitymask"></a>CRenderTarget::FillOpacityMask  
 適用於所指定的點陣圖為筆刷不透明遮罩，並使用該筆刷繪製區域的呈現目標。  
  
```  
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,  
    CD2DBrush* pBrush,  
    D2D1_OPACITY_MASK_CONTENT content,  
    const CD2DRectF& rectDest,  
    const CD2DRectF& rectSrc);
```  
  
### <a name="parameters"></a>參數  
 `pOpacityMask`  
 位置，並且以與裝置無關的像素，來繪製橢圓形的半徑。  
  
 `pBrush`  
 用來繪製的區域的呈現目標 destinationRectangle 所指定的筆刷。  
  
 `content`  
 不是透明遮罩包含的內容類型。 值用於判斷不透明遮罩會以混合的色彩空間。  
  
 `rectDest`  
 若要繪製，以與裝置無關的像素為單位的呈現目標的區域。  
  
 `rectSrc`  
 要做為與裝置無關的像素為單位的不透明度遮罩點陣圖的區域。  
  
##  <a name="a-namefillrectanglea--crendertargetfillrectangle"></a><a name="fillrectangle"></a>CRenderTarget::FillRectangle  
 繪製指定矩形內部。  
  
```  
void FillRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 要繪製，以與裝置無關的像素為單位的矩形的維度。  
  
 `pBrush`  
 用來繪製矩形的筆刷的內部。  
  
##  <a name="a-namefillroundedrectanglea--crendertargetfillroundedrectangle"></a><a name="fillroundedrectangle"></a>CRenderTarget::FillRoundedRectangle  
 繪製指定之圓角矩形內部。  
  
```  
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `rectRounded`  
 要繪製，請在與裝置無關的像素的圓角矩形的維度。  
  
 `pBrush`  
 用來繪製圓角矩形內部的筆刷。  
  
##  <a name="a-nameflusha--crendertargetflush"></a><a name="flush"></a>CRenderTarget::Flush  
 執行所有暫止的繪製命令。  
  
```  
void Flush(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL);
```  
  
### <a name="parameters"></a>參數  
 `tag1`  
 包含繪製作業中造成錯誤或 0，如果沒有任何錯誤的標記。 這個參數會以未初始化的狀態傳遞。  
  
 `tag2`  
 包含繪製作業中造成錯誤或 0，如果沒有任何錯誤的標記。 這個參數會以未初始化的狀態傳遞。  
  
##  <a name="a-namegetantialiasmodea--crendertargetgetantialiasmode"></a><a name="getantialiasmode"></a>CRenderTarget::GetAntialiasMode  
 擷取非文字繪圖作業的目前反鋸齒功能模式。  
  
```  
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前繪製作業的非文字的消除鋸齒模式。  
  
##  <a name="a-namegetdpia--crendertargetgetdpi"></a><a name="getdpi"></a>CRenderTarget::GetDpi  
 傳回呈現目標的每英吋點數 (DPI)  
  
```  
CD2DSizeF GetDpi() const;  
```  
  
### <a name="return-value"></a>傳回值  
 呈現目標的每英吋點數 (DPI)。  
  
##  <a name="a-namegetmaximumbitmapsizea--crendertargetgetmaximumbitmapsize"></a><a name="getmaximumbitmapsize"></a>CRenderTarget::GetMaximumBitmapSize  
 取得大小上限，以支援呈現目標的任何一個點陣圖維度的裝置相關單位 （像素）  
  
```  
UINT32 GetMaximumBitmapSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 大小上限，單位為像素的呈現目標支援任何一個點陣圖維度  
  
##  <a name="a-namegetpixelformata--crendertargetgetpixelformat"></a><a name="getpixelformat"></a>CRenderTarget::GetPixelFormat  
 擷取呈現目標的像素格式和 alpha 模式  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>傳回值  
 呈現目標的像素格式和 alpha 模式  
  
##  <a name="a-namegetpixelsizea--crendertargetgetpixelsize"></a><a name="getpixelsize"></a>CRenderTarget::GetPixelSize  
 傳回以裝置像素為單位的呈現目標的大小  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 呈現目標裝置像素為單位的大小  
  
##  <a name="a-namegetrendertargeta--crendertargetgetrendertarget"></a><a name="getrendertarget"></a>CRenderTarget::GetRenderTarget  
 傳回 ID2D1RenderTarget 介面  
  
```  
ID2D1RenderTarget* GetRenderTarget();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1RenderTarget 介面的指標。  
  
##  <a name="a-namegetsizea--crendertargetgetsize"></a><a name="getsize"></a>CRenderTarget::GetSize  
 傳回與裝置無關的像素為單位的呈現目標大小  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 與裝置無關的像素為單位的呈現目標的目前大小  
  
##  <a name="a-namegettagsa--crendertargetgettags"></a><a name="gettags"></a>CRenderTarget::GetTags  
 取得後續繪圖作業的標籤。  
  
```  
void GetTags(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `tag1`  
 包含後續繪圖作業的第一個標籤。 這個參數會以未初始化的狀態傳遞。 如果指定 NULL，則會擷取此參數沒有值。  
  
 `tag2`  
 包含後續繪圖作業的第二個標籤。 這個參數會以未初始化的狀態傳遞。 如果指定 NULL，則會擷取此參數沒有值。  
  
##  <a name="a-namegettextantialiasmodea--crendertargetgettextantialiasmode"></a><a name="gettextantialiasmode"></a>CRenderTarget::GetTextAntialiasMode  
 取得目前的反鋸齒功能模式的文字和繪製作業的圖像 （glyph）。  
  
```  
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前消除鋸齒的文字及圖像繪製作業的模式。  
  
##  <a name="a-namegettextrenderingparamsa--crendertargetgettextrenderingparams"></a><a name="gettextrenderingparams"></a>CRenderTarget::GetTextRenderingParams  
 擷取目前的文字轉譯選項呈現目標。  
  
```  
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```  
  
### <a name="parameters"></a>參數  
 `textRenderingParams`  
 此方法傳回時，textRenderingParamscontains 呈現目標的指標位址的目前文字轉譯選項。  
  
##  <a name="a-namegettransforma--crendertargetgettransform"></a><a name="gettransform"></a>CRenderTarget::GetTransform  
 將指定的轉換套用至呈現目標，取代現有的轉換。 所有後續的繪圖作業發生在轉換後的空間。  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>參數  
 `transform`  
 要套用至呈現目標的轉換。  
  
##  <a name="a-nameissupporteda--crendertargetissupported"></a><a name="issupported"></a>CRenderTarget::IsSupported  
 指出呈現目標是否支援指定的屬性  
  
```  
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;  
```  
  
### <a name="parameters"></a>參數  
 `renderTargetProperties`  
 要測試的呈現目標屬性  
  
### <a name="return-value"></a>傳回值  
 指定的呈現目標屬性會受到此呈現目標; 如果為 TRUE否則為 FALSE  
  
##  <a name="a-nameisvalida--crendertargetisvalid"></a><a name="isvalid"></a>CRenderTarget::IsValid  
 檢查資源的有效性  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源無效，則為 TRUE否則為 FALSE。  
  
##  <a name="a-namemlstresourcesa--crendertargetmlstresources"></a><a name="m_lstresources"></a>CRenderTarget::m_lstResources  
 一份 CD2DResource 物件的指標。  
  
```  
CObList m_lstResources;  
```  
  
##  <a name="a-namemprendertargeta--crendertargetmprendertarget"></a><a name="m_prendertarget"></a>CRenderTarget::m_pRenderTarget  
 ID2D1RenderTarget 物件的指標。  
  
```  
ID2D1RenderTarget* m_pRenderTarget;  
```  
  
##  <a name="a-namemptextformatdefaulta--crendertargetmptextformatdefault"></a><a name="m_ptextformatdefault"></a>CRenderTarget::m_pTextFormatDefault  
 包含預設文字格式的 CD2DTextFormat 物件的指標。  
  
```  
CD2DTextFormat* m_pTextFormatDefault;  
```  
  
##  <a name="a-nameoperatorid2d1rendertargetstara--crendertargetoperator-id2d1rendertarget"></a><a name="operator_id2d1rendertarget_star"></a>CRenderTarget::operator ID2D1RenderTarget *  
 傳回 ID2D1RenderTarget 介面  
  
```  
operator ID2D1RenderTarget*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1RenderTarget 介面的指標。  
  
##  <a name="a-namepopaxisalignedclipa--crendertargetpopaxisalignedclip"></a><a name="popaxisalignedclip"></a>CRenderTarget::PopAxisAlignedClip  
 移除呈現目標的軸對齊的最後一個剪輯。 會呼叫這個方法之後，多媒體項目不會再套用至後續繪製作業。  
  
```  
void PopAxisAlignedClip();
```  
  
##  <a name="a-namepoplayera--crendertargetpoplayer"></a><a name="poplayer"></a>CRenderTarget::PopLayer  
 停止將繪圖作業重新導向至指定的最後一個 PushLayer 層呼叫。  
  
```  
void PopLayer();
```  
  
##  <a name="a-namepushaxisalignedclipa--crendertargetpushaxisalignedclip"></a><a name="pushaxisalignedclip"></a>CRenderTarget::PushAxisAlignedClip  
 移除呈現目標的軸對齊的最後一個剪輯。 會呼叫這個方法之後，多媒體項目不會再套用至後續繪製作業。  
  
```  
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,  
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```  
  
### <a name="parameters"></a>參數  
 `rectClip`  
 大小和位置的裁剪區域中，以與裝置無關的像素為單位。  
  
 `mode`  
 可繪製具有子像素界限的剪輯 rects 邊緣以及 blend 場景內容剪輯反鋸齒功能模式。 混合，其會執行之後當 PopAxisAlignedClip 方法會呼叫，而不會套用至圖層內的每個基本型別。  
  
##  <a name="a-namepushlayera--crendertargetpushlayer"></a><a name="pushlayer"></a>CRenderTarget::PushLayer  
 將指定的圖層加入至呈現目標，讓呼叫 PopLayer 之前接收到所有後續的繪圖作業。  
  
```  
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,  
    CD2DLayer& layer);
```  
  
### <a name="parameters"></a>參數  
 `layerParameters`  
 內容界限、 幾何遮罩、 不透明度、 不透明度遮罩和圖層的反鋸齒功能選項。  
  
 `layer`  
 接收後續的繪圖作業的圖層。  
  
##  <a name="a-namerestoredrawingstatea--crendertargetrestoredrawingstate"></a><a name="restoredrawingstate"></a>CRenderTarget::RestoreDrawingState  
 將呈現目標的繪圖狀態設定所指定的 ID2D1DrawingStateBlock。  
  
```  
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```  
  
### <a name="parameters"></a>參數  
 `drawingStateBlock`  
 呈現目標的新繪圖的狀態。  
  
##  <a name="a-namesavedrawingstatea--crendertargetsavedrawingstate"></a><a name="savedrawingstate"></a>CRenderTarget::SaveDrawingState  
 將繪圖的目前狀態儲存至指定的 ID2D1DrawingStateBlock。  
  
```  
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;  
```  
  
### <a name="parameters"></a>參數  
 `drawingStateBlock`  
 此方法傳回時，包含目前繪圖呈現目標的狀態。 這個參數必須先初始化之前將它傳遞給方法。  
  
##  <a name="a-namesetantialiasmodea--crendertargetsetantialiasmode"></a><a name="setantialiasmode"></a>CRenderTarget::SetAntialiasMode  
 設定呈現目標的反鋸齒功能模式。 反鋸齒功能模式適用於所有後續繪製作業，不包括文字和繪製作業的圖像 （glyph）。  
  
```  
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```  
  
### <a name="parameters"></a>參數  
 `antialiasMode`  
 未來的繪圖作業的反鋸齒功能模式。  
  
##  <a name="a-namesetdpia--crendertargetsetdpi"></a><a name="setdpi"></a>CRenderTarget::SetDpi  
 設定每英吋點數 (DPI) 呈現目標。  
  
```  
void SetDpi(const CD2DSizeF& sizeDPI);
```  
  
### <a name="parameters"></a>參數  
 `sizeDPI`  
 大於或等於零的值會指定呈現目標水平/verticalDPI。  
  
##  <a name="a-namesettagsa--crendertargetsettags"></a><a name="settags"></a>CRenderTarget::SetTags  
 指定後續繪圖作業的標籤。  
  
```  
void SetTags(
    D2D1_TAG tag1,  
    D2D1_TAG tag2);
```  
  
### <a name="parameters"></a>參數  
 `tag1`  
 要套用至後續繪圖作業的標籤。  
  
 `tag2`  
 要套用至後續繪圖作業的標籤。  
  
##  <a name="a-namesettextantialiasmodea--crendertargetsettextantialiasmode"></a><a name="settextantialiasmode"></a>CRenderTarget::SetTextAntialiasMode  
 指定要用於後續文字和圖像繪製作業的反鋸齒功能模式。  
  
```  
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```  
  
### <a name="parameters"></a>參數  
 `textAntialiasMode`  
 要用於後續文字和繪製作業的圖像 （glyph） 的反鋸齒功能模式。  
  
##  <a name="a-namesettextrenderingparamsa--crendertargetsettextrenderingparams"></a><a name="settextrenderingparams"></a>CRenderTarget::SetTextRenderingParams  
 指定要套用至所有後續文字和繪製作業的圖像的文字呈現選項。  
  
```  
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```  
  
### <a name="parameters"></a>參數  
 `textRenderingParams`  
 文字轉譯選項套用到所有後續文字和圖像繪製作業。若要清除目前文字轉譯選項為 NULL。  
  
##  <a name="a-namesettransforma--crendertargetsettransform"></a><a name="settransform"></a>CRenderTarget::SetTransform  
 將指定的轉換套用至呈現目標，取代現有的轉換。 所有後續的繪圖作業發生在轉換後的空間。  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);  
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```  
  
### <a name="parameters"></a>參數  
 `transform`  
 要套用至呈現目標的轉換。  
  
##  <a name="a-nameverifyresourcea--crendertargetverifyresource"></a><a name="verifyresource"></a>CRenderTarget::VerifyResource  
 確認 CD2DResource 物件的有效性。如果它不存在，則建立的物件。  
  
```  
BOOL VerifyResource(CD2DResource* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 CD2DResource 物件指標。  
  
### <a name="return-value"></a>傳回值  
 是物件，如果有效，則為 TRUE否則為 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

