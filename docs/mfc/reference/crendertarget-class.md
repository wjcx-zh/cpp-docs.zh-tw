---
title: CRenderTarget 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRenderTarget
- AFXRENDERTARGET/CRenderTarget
- AFXRENDERTARGET/CRenderTarget::CRenderTarget
- AFXRENDERTARGET/CRenderTarget::Attach
- AFXRENDERTARGET/CRenderTarget::BeginDraw
- AFXRENDERTARGET/CRenderTarget::Clear
- AFXRENDERTARGET/CRenderTarget::COLORREF_TO_D2DCOLOR
- AFXRENDERTARGET/CRenderTarget::CreateCompatibleRenderTarget
- AFXRENDERTARGET/CRenderTarget::Destroy
- AFXRENDERTARGET/CRenderTarget::Detach
- AFXRENDERTARGET/CRenderTarget::DrawBitmap
- AFXRENDERTARGET/CRenderTarget::DrawEllipse
- AFXRENDERTARGET/CRenderTarget::DrawGeometry
- AFXRENDERTARGET/CRenderTarget::DrawGlyphRun
- AFXRENDERTARGET/CRenderTarget::DrawLine
- AFXRENDERTARGET/CRenderTarget::DrawRectangle
- AFXRENDERTARGET/CRenderTarget::DrawRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::DrawText
- AFXRENDERTARGET/CRenderTarget::DrawTextLayout
- AFXRENDERTARGET/CRenderTarget::EndDraw
- AFXRENDERTARGET/CRenderTarget::FillEllipse
- AFXRENDERTARGET/CRenderTarget::FillGeometry
- AFXRENDERTARGET/CRenderTarget::FillMesh
- AFXRENDERTARGET/CRenderTarget::FillOpacityMask
- AFXRENDERTARGET/CRenderTarget::FillRectangle
- AFXRENDERTARGET/CRenderTarget::FillRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::Flush
- AFXRENDERTARGET/CRenderTarget::GetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetDpi
- AFXRENDERTARGET/CRenderTarget::GetMaximumBitmapSize
- AFXRENDERTARGET/CRenderTarget::GetPixelFormat
- AFXRENDERTARGET/CRenderTarget::GetPixelSize
- AFXRENDERTARGET/CRenderTarget::GetRenderTarget
- AFXRENDERTARGET/CRenderTarget::GetSize
- AFXRENDERTARGET/CRenderTarget::GetTags
- AFXRENDERTARGET/CRenderTarget::GetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::GetTransform
- AFXRENDERTARGET/CRenderTarget::IsSupported
- AFXRENDERTARGET/CRenderTarget::IsValid
- AFXRENDERTARGET/CRenderTarget::PopAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PopLayer
- AFXRENDERTARGET/CRenderTarget::PushAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PushLayer
- AFXRENDERTARGET/CRenderTarget::RestoreDrawingState
- AFXRENDERTARGET/CRenderTarget::SaveDrawingState
- AFXRENDERTARGET/CRenderTarget::SetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetDpi
- AFXRENDERTARGET/CRenderTarget::SetTags
- AFXRENDERTARGET/CRenderTarget::SetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::SetTransform
- AFXRENDERTARGET/CRenderTarget::VerifyResource
- AFXRENDERTARGET/CRenderTarget::m_lstResources
- AFXRENDERTARGET/CRenderTarget::m_pRenderTarget
- AFXRENDERTARGET/CRenderTarget::m_pTextFormatDefault
dev_langs:
- C++
helpviewer_keywords:
- CRenderTarget [MFC], CRenderTarget
- CRenderTarget [MFC], Attach
- CRenderTarget [MFC], BeginDraw
- CRenderTarget [MFC], Clear
- CRenderTarget [MFC], COLORREF_TO_D2DCOLOR
- CRenderTarget [MFC], CreateCompatibleRenderTarget
- CRenderTarget [MFC], Destroy
- CRenderTarget [MFC], Detach
- CRenderTarget [MFC], DrawBitmap
- CRenderTarget [MFC], DrawEllipse
- CRenderTarget [MFC], DrawGeometry
- CRenderTarget [MFC], DrawGlyphRun
- CRenderTarget [MFC], DrawLine
- CRenderTarget [MFC], DrawRectangle
- CRenderTarget [MFC], DrawRoundedRectangle
- CRenderTarget [MFC], DrawText
- CRenderTarget [MFC], DrawTextLayout
- CRenderTarget [MFC], EndDraw
- CRenderTarget [MFC], FillEllipse
- CRenderTarget [MFC], FillGeometry
- CRenderTarget [MFC], FillMesh
- CRenderTarget [MFC], FillOpacityMask
- CRenderTarget [MFC], FillRectangle
- CRenderTarget [MFC], FillRoundedRectangle
- CRenderTarget [MFC], Flush
- CRenderTarget [MFC], GetAntialiasMode
- CRenderTarget [MFC], GetDpi
- CRenderTarget [MFC], GetMaximumBitmapSize
- CRenderTarget [MFC], GetPixelFormat
- CRenderTarget [MFC], GetPixelSize
- CRenderTarget [MFC], GetRenderTarget
- CRenderTarget [MFC], GetSize
- CRenderTarget [MFC], GetTags
- CRenderTarget [MFC], GetTextAntialiasMode
- CRenderTarget [MFC], GetTextRenderingParams
- CRenderTarget [MFC], GetTransform
- CRenderTarget [MFC], IsSupported
- CRenderTarget [MFC], IsValid
- CRenderTarget [MFC], PopAxisAlignedClip
- CRenderTarget [MFC], PopLayer
- CRenderTarget [MFC], PushAxisAlignedClip
- CRenderTarget [MFC], PushLayer
- CRenderTarget [MFC], RestoreDrawingState
- CRenderTarget [MFC], SaveDrawingState
- CRenderTarget [MFC], SetAntialiasMode
- CRenderTarget [MFC], SetDpi
- CRenderTarget [MFC], SetTags
- CRenderTarget [MFC], SetTextAntialiasMode
- CRenderTarget [MFC], SetTextRenderingParams
- CRenderTarget [MFC], SetTransform
- CRenderTarget [MFC], VerifyResource
- CRenderTarget [MFC], m_lstResources
- CRenderTarget [MFC], m_pRenderTarget
- CRenderTarget [MFC], m_pTextFormatDefault
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7550e3e3d8bf7e49f9f93ea6e9a931d6567ef0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crendertarget-class"></a>CRenderTarget 類別
ID2D1RenderTarget 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CRenderTarget : public CObject;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CRenderTarget::CRenderTarget](#crendertarget)|建構 CRenderTarget 物件。|  
|[CRenderTarget:: ~ CRenderTarget](#crendertarget__~crendertarget)|解構函式。 呈現目標物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRenderTarget::Attach](#attach)|將現有的轉譯目標物件的介面|  
|[CRenderTarget::BeginDraw](#begindraw)|初始化這個呈現目標上繪製。|  
|[CRenderTarget::Clear](#clear)|清除指定的色彩來繪製的區域。|  
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|將 GDI 色彩和 alpha 值轉換成 D2D1_COLOR_F 物件。|  
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|與目前的轉譯目標相容的中繼幕後繪製期間建立新的點陣圖轉譯目標使用。|  
|[CRenderTarget::Destroy](#destroy)|刪除一個或多個資源|  
|[CRenderTarget::Detach](#detach)|中斷連結物件中的呈現目標介面|  
|[CRenderTarget::DrawBitmap](#drawbitmap)|繪製格式化指定 IDWriteTextLayout 物件所描述的文字。|  
|[CRenderTarget::DrawEllipse](#drawellipse)|繪製指定的橢圓形使用指定的筆劃樣式的外框。|  
|[CRenderTarget::DrawGeometry](#drawgeometry)|繪製外框的指定使用指定的筆劃樣式的幾何。|  
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|繪製指定的圖像 （glyph）。|  
|[CRenderTarget::DrawLine](#drawline)|使用指定的筆劃樣式指定的點之間繪製一條線。|  
|[CRenderTarget::DrawRectangle](#drawrectangle)|繪製外框的矩形具有指定的維度和筆劃樣式。|  
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|繪製外框的指定之圓角矩形使用指定的筆劃樣式。|  
|[CRenderTarget::DrawText](#drawtext)|繪製指定的文字使用 IDWriteTextFormat 物件所提供的格式資訊。|  
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|繪製格式化指定 IDWriteTextLayout 物件所描述的文字。|  
|[CRenderTarget::EndDraw](#enddraw)|結束對轉譯目標的繪製作業，並指出目前的錯誤狀態及相關聯的標記。|  
|[CRenderTarget::FillEllipse](#fillellipse)|繪製指定的橢圓形內部。|  
|[CRenderTarget::FillGeometry](#fillgeometry)|繪製指定的幾何的內部。|  
|[CRenderTarget::FillMesh](#fillmesh)|繪製指定的 mesh 的內部。|  
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|適用於所指定的點陣圖為筆刷的不透明度遮罩，並使用該筆刷繪製的呈現目標區域中。|  
|[CRenderTarget::FillRectangle](#fillrectangle)|繪製指定矩形的內部。|  
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|繪製指定之圓角矩形內部。|  
|[CRenderTarget::Flush](#flush)|執行所有暫止的繪圖命令。|  
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|擷取目前的消除鋸齒非文字繪圖作業模式。|  
|[CRenderTarget::GetDpi](#getdpi)|傳回轉譯目標的每英吋點數 (DPI)|  
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|取得大小上限，單位裝置而異 （像素） 的支援轉譯目標的任何一個點陣圖維度|  
|[CRenderTarget::GetPixelFormat](#getpixelformat)|擷取轉譯目標像素格式和 alpha 模式|  
|[CRenderTarget::GetPixelSize](#getpixelsize)|傳回以裝置像素為單位的呈現目標的大小|  
|[CRenderTarget::GetRenderTarget](#getrendertarget)|傳回 ID2D1RenderTarget 介面|  
|[CRenderTarget::GetSize](#getsize)|傳回與裝置無關的像素為單位轉譯目標大小|  
|[CRenderTarget::GetTags](#gettags)|取得後續繪圖作業的標籤。|  
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|取得目前的消除鋸齒模式文字和繪製作業的圖像。|  
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|擷取呈現目標的目前文字呈現選項。|  
|[CRenderTarget::GetTransform](#gettransform)|將指定的轉換套用至呈現目標，取代現有的轉換。 後續的所有繪圖作業發生在轉換後的空間。|  
|[CRenderTarget::IsSupported](#issupported)|指出轉譯目標是否支援指定的屬性|  
|[CRenderTarget::IsValid](#isvalid)|檢查資源的有效性|  
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|從轉譯目標中移除的座標軸對齊的最後一個剪輯。 呼叫這個方法之後，後續的繪圖作業將不再套用剪輯。|  
|[CRenderTarget::PopLayer](#poplayer)|停止重新導向至最後一個 PushLayer 所指定的圖層的繪圖作業呼叫。|  
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|從轉譯目標中移除的座標軸對齊的最後一個剪輯。 呼叫這個方法之後，後續的繪圖作業將不再套用剪輯。|  
|[CRenderTarget::PushLayer](#pushlayer)|將指定的圖層加入至呈現目標，讓呼叫 PopLayer 之前收到後續的所有繪圖作業。|  
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|呈現目標的繪圖狀態設定為指定 ID2D1DrawingStateBlock 的。|  
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|將目前的繪圖狀態儲存至指定 ID2D1DrawingStateBlock。|  
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|設定呈現目標的消除鋸齒模式。 消除鋸齒模式適用於後續的所有繪圖作業，但不包括文字和繪製作業的圖像。|  
|[CRenderTarget::SetDpi](#setdpi)|設定每英吋點數 (DPI) 呈現目標。|  
|[CRenderTarget::SetTags](#settags)|指定針對後續的繪圖作業的標籤。|  
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|指定要用於後續文字和圖像繪圖作業的消除鋸齒模式。|  
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|指定要套用到所有後續文字和繪製作業的圖像的文字呈現選項。|  
|[CRenderTarget::SetTransform](#settransform)|多載。 將指定的轉換套用至呈現目標，取代現有的轉換。 後續的所有繪圖作業發生在轉換後的空間。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](#verifyresource)|驗證 CD2DResource 物件的有效性。如果它已不存在，請建立的物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|傳回 ID2D1RenderTarget 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CRenderTarget::m_lstResources](#m_lstresources)|CD2DResource 物件指標的清單。|  
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|ID2D1RenderTarget 物件的指標。|  
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|包含預設文字格式的 CD2DTextFormat 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="_dtorcrendertarget"></a>  CRenderTarget:: ~ CRenderTarget  
 解構函式。 呈現目標物件終結時呼叫。  
  
```  
virtual ~CRenderTarget();
```  
  
##  <a name="attach"></a>  CRenderTarget::Attach  
 將現有的轉譯目標物件的介面  
  
```  
void Attach(ID2D1RenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 現有的轉譯目標介面。 不能是 NULL  
  
##  <a name="begindraw"></a>  CRenderTarget::BeginDraw  
 初始化這個呈現目標上繪製。  
  
```  
void BeginDraw();
```  
  
##  <a name="clear"></a>  CRenderTarget::Clear  
 清除指定的色彩來繪製的區域。  
  
```  
void Clear(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>參數  
 `color`  
 清除在繪圖區域的色彩。  
  
##  <a name="colorref_to_d2dcolor"></a>  CRenderTarget::COLORREF_TO_D2DCOLOR  
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
  
##  <a name="createcompatiblerendertarget"></a>  CRenderTarget::CreateCompatibleRenderTarget  
 與目前的轉譯目標相容的中繼幕後繪製期間建立新的點陣圖轉譯目標使用。  
  
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
 新的呈現目標，是否應與原始版本不同的裝置獨立像素為單位的所需的大小呈現目標，或為 NULL。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `sizePixelDesired`  
 新的轉譯目標像素為單位，是否應與原始版本不同的所需的大小呈現目標，或為 NULL。 如需詳細資訊，請參閱＜備註＞一節。  
  
 `desiredFormat`  
 所需的像素格式和新的 alpha 模式呈現目標，或為 NULL。 如果的像素格式設定為 DXGI_FORMAT_UNKNOWN 或這個參數是 null，新的呈現目標做為原始呈現目標，就會使用相同的像素格式。 如果 alpha 模式 D2D1_ALPHA_MODE_UNKNOWN 或這個參數是 NULL，新的呈現目標的 alpha 模式會預設為 D2D1_ALPHA_MODE_PREMULTIPLIED。 如需受支援像素格式的資訊，請參閱支援的像素格式和 Alpha 模式。  
  
 `options`  
 指定新的呈現目標是否必須使用 GDI 相容的值。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="crendertarget"></a>  CRenderTarget::CRenderTarget  
 建構 CRenderTarget 物件。  
  
```  
CRenderTarget();
```  
  
##  <a name="destroy"></a>  CRenderTarget::Destroy  
 刪除一個或多個資源  
  
```  
BOOL Destroy(BOOL bDeleteResources = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bDeleteResources`  
 如果 bDeleteResources 為 TRUE，將會自動終結位於 m_lstResources 中的所有資源。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE  
  
##  <a name="detach"></a>  CRenderTarget::Detach  
 中斷連結物件中的呈現目標介面  
  
```  
ID2D1RenderTarget* Detach ();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的指標會呈現目標的介面。  
  
##  <a name="drawbitmap"></a>  CRenderTarget::DrawBitmap  
 繪製格式化指定 IDWriteTextLayout 物件所描述的文字。  
  
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
 要呈現的點陣圖。  
  
 `rectDest`  
 大小和位置，轉譯目標的座標空間，繪製了點陣圖即的區域中與裝置無關像素為單位。 如果不是井然有序矩形，不繪製任何內容，但轉譯目標不進入錯誤狀態。  
  
 `fOpacity`  
 介於 0.0 f 到 1.0 f，含的值，指定要套用至點陣圖; 的不透明度值此值已乘以內容的點陣圖的 alpha 值。  
  
 `interpolationMode`  
 點陣圖縮放或旋轉繪圖作業時所要使用插補模式。  
  
 `pRectSrc`  
 大小和位置，以與裝置無關的像素點陣圖的座標空間，以繪製點陣圖內的區域中。  
  
##  <a name="drawellipse"></a>  CRenderTarget::DrawEllipse  
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
 橢圓形的筆劃粗細。 筆觸被中心橢圓形的外框。  
  
 `strokeStyle`  
 要套用至橢圓形的外框或 NULL 來繪製實心筆觸筆觸的樣式。  
  
##  <a name="drawgeometry"></a>  CRenderTarget::DrawGeometry  
 繪製外框的指定使用指定的筆劃樣式的幾何。  
  
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
 幾何的筆劃粗細。 筆觸是幾何的外框上置中對齊。  
  
 `strokeStyle`  
 要套用至幾何的外框或 NULL 來繪製實心筆觸筆觸的樣式。  
  
##  <a name="drawglyphrun"></a>  CRenderTarget::DrawGlyphRun  
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
 在與裝置無關的像素，圖像 （glyph） 的比較基準的來源。  
  
 `glyphRun`  
 要呈現的圖像。  
  
 `pForegroundBrush`  
 用來繪製指定的字符的筆刷。  
  
 `measuringMode`  
 值，指出如何使用字符度量來進行格式化時，量值的文字。 預設值是 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="drawline"></a>  CRenderTarget::DrawLine  
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
 線條，以與裝置無關的像素為單位的結束點。  
  
 `pBrush`  
 用來繪製線條的筆劃的筆刷。  
  
 `fStrokeWidth`  
 值大於或等於 0.0 f，指定筆劃的寬度。 如果未指定這個參數，它會預設為 1.0 f。 筆劃內置該行。  
  
 `strokeStyle`  
 小畫家，或 NULL 來繪製一條實線筆劃的端點樣式。  
  
##  <a name="drawrectangle"></a>  CRenderTarget::DrawRectangle  
 繪製外框的矩形具有指定的維度和筆劃樣式。  
  
```  
void DrawRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 若要繪製，以與裝置無關的像素為單位矩形的維度  
  
 `pBrush`  
 用來繪製的矩形筆劃的筆刷  
  
 `fStrokeWidth`  
 值大於或等於 0.0 f，指定矩形的筆劃的寬度。 筆觸被置於矩形外框。  
  
 `strokeStyle`  
 小畫家，或 NULL 來繪製實心筆觸筆觸的樣式。  
  
##  <a name="drawroundedrectangle"></a>  CRenderTarget::DrawRoundedRectangle  
 繪製外框的指定之圓角矩形使用指定的筆劃樣式。  
  
```  
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `rectRounded`  
 若要繪製，以與裝置無關的像素為單位圓角矩形的維度。  
  
 `pBrush`  
 用來繪製圓角的矩形外框的筆刷。  
  
 `fStrokeWidth`  
 圓角的矩形的筆劃的寬度。 筆觸被中心圓角的矩形外框。 預設值為 1.0 f。  
  
 `strokeStyle`  
 圓角的矩形的筆觸，則為 NULL 來繪製實心筆劃樣式。 預設值是 NULL。  
  
##  <a name="drawtext"></a>  CRenderTarget::DrawText  
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
 要繪製的 Unicode 字元陣列的指標。  
  
 `rect`  
 用來繪製文字的區域位置及大小。  
  
 `pForegroundBrush`  
 用來繪製文字的筆刷。  
  
 `textFormat`  
 描述要繪製的文字，例如字型、 字型大小及文字方向的詳細資料的格式物件。  
  
 `options`  
 值，指出是否應該像素界限對齊文字，以及是否文字應該依附配置矩形。 預設值是 D2D1_DRAW_TEXT_OPTIONS_NONE，表示文字應該對齊像素界限，而且不應該依附配置矩形中。  
  
 `measuringMode`  
 值，指出如何使用字符度量來進行格式化時，量值的文字。 預設值是 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="drawtextlayout"></a>  CRenderTarget::DrawTextLayout  
 繪製格式化指定 IDWriteTextLayout 物件所描述的文字。  
  
```  
void DrawTextLayout(
    const CD2DPointF& ptOrigin,  
    CD2DTextLayout* textLayout,  
    CD2DBrush* pBrushForeground,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>參數  
 `ptOrigin`  
 點，以與裝置無關像素，在其中繪製 textLayout 所描述的文字的左上角中所述。  
  
 `textLayout`  
 要繪製的格式化的文字。 不會繼承自 ID2D1Resource 任何繪製效果都會被忽略。 如果繪製效果是繼承自 ID2D1Resource 不筆刷，這個方法會失敗，並且轉譯目標會放在錯誤狀態。  
  
 `pBrushForeground`  
 用來繪製中還沒有為繪製效果 （IDWriteTextLayout::SetDrawingEffect 方法所指定） 與它相關聯的筆刷的 textLayout 的任何文字的筆刷。  
  
 `options`  
 值，指出是否應該像素界限對齊文字，以及是否文字應該依附配置矩形。 預設值是 D2D1_DRAW_TEXT_OPTIONS_NONE，表示文字應該對齊像素界限，而且不應該依附配置矩形中。  
  
##  <a name="enddraw"></a>  CRenderTarget::EndDraw  
 結束對轉譯目標的繪製作業，並指出目前的錯誤狀態及相關聯的標記。  
  
```  
HRESULT EndDraw();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="fillellipse"></a>  CRenderTarget::FillEllipse  
 繪製指定的橢圓形內部。  
  
```  
void FillEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `ellipse`  
 位置和中與裝置無關的像素，來繪製橢圓形的半徑。  
  
 `pBrush`  
 用來繪製橢圓形內部的筆刷。  
  
##  <a name="fillgeometry"></a>  CRenderTarget::FillGeometry  
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
 內部的筆刷用來繪製幾何。  
  
 `pOpacityBrush`  
 要套用至幾何; 不透明度遮罩沒有不透明度遮罩是 NULL。 如果指定的不透明度遮罩 （opacityBrush 參數），則筆刷必須有設為 D2D1_EXTEND_MODE_CLAMP 其 x 和 y 擴充模式 ID2D1BitmapBrush。 如需詳細資訊，請參閱＜備註＞一節。  
  
##  <a name="fillmesh"></a>  CRenderTarget::FillMesh  
 繪製指定的 mesh 的內部。  
  
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
  
##  <a name="fillopacitymask"></a>  CRenderTarget::FillOpacityMask  
 適用於所指定的點陣圖為筆刷的不透明度遮罩，並使用該筆刷繪製的呈現目標區域中。  
  
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
 位置和中與裝置無關的像素，來繪製橢圓形的半徑。  
  
 `pBrush`  
 用來繪製的區域 destinationRectangle 所指定的轉譯目標的筆刷。  
  
 `content`  
 不是透明度遮罩包含的內容類型。 值用來判斷不透明度遮罩會以混合的色彩空間。  
  
 `rectDest`  
 若要繪製，以與裝置無關的像素為單位轉譯目標的區域。  
  
 `rectSrc`  
 要做為與裝置無關的像素為單位的不透明度遮罩點陣圖的區域。  
  
##  <a name="fillrectangle"></a>  CRenderTarget::FillRectangle  
 繪製指定矩形的內部。  
  
```  
void FillRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 要繪製，以與裝置無關的像素為單位的矩形的維度。  
  
 `pBrush`  
 內部的筆刷用來繪製的矩形。  
  
##  <a name="fillroundedrectangle"></a>  CRenderTarget::FillRoundedRectangle  
 繪製指定之圓角矩形內部。  
  
```  
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>參數  
 `rectRounded`  
 要繪製，以與裝置無關的像素的圓角矩形的維度。  
  
 `pBrush`  
 用來繪製圓角矩形內部的筆刷。  
  
##  <a name="flush"></a>  CRenderTarget::Flush  
 執行所有暫止的繪圖命令。  
  
```  
void Flush(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL);
```  
  
### <a name="parameters"></a>參數  
 `tag1`  
 包含繪製作業造成錯誤或 0，如果沒有錯誤的標記。 這個參數會以未初始化的狀態傳遞。  
  
 `tag2`  
 包含繪製作業造成錯誤或 0，如果沒有錯誤的標記。 這個參數會以未初始化的狀態傳遞。  
  
##  <a name="getantialiasmode"></a>  CRenderTarget::GetAntialiasMode  
 擷取目前的消除鋸齒非文字繪圖作業模式。  
  
```  
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非文字繪圖作業的目前反鋸齒功能模式。  
  
##  <a name="getdpi"></a>  CRenderTarget::GetDpi  
 傳回轉譯目標的每英吋點數 (DPI)  
  
```  
CD2DSizeF GetDpi() const;  
```  
  
### <a name="return-value"></a>傳回值  
 呈現目標的每英吋點數 (DPI)。  
  
##  <a name="getmaximumbitmapsize"></a>  CRenderTarget::GetMaximumBitmapSize  
 取得大小上限，單位裝置而異 （像素） 的支援轉譯目標的任何一個點陣圖維度  
  
```  
UINT32 GetMaximumBitmapSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 大小上限，單位為像素的呈現目標所支援的任何一個點陣圖維度  
  
##  <a name="getpixelformat"></a>  CRenderTarget::GetPixelFormat  
 擷取轉譯目標像素格式和 alpha 模式  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>傳回值  
 轉譯目標像素格式和 alpha 模式  
  
##  <a name="getpixelsize"></a>  CRenderTarget::GetPixelSize  
 傳回以裝置像素為單位的呈現目標的大小  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 呈現目標，裝置像素為單位的大小  
  
##  <a name="getrendertarget"></a>  CRenderTarget::GetRenderTarget  
 傳回 ID2D1RenderTarget 介面  
  
```  
ID2D1RenderTarget* GetRenderTarget();
```  
  
### <a name="return-value"></a>傳回值  
 ID2D1RenderTarget 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="getsize"></a>  CRenderTarget::GetSize  
 傳回與裝置無關的像素為單位轉譯目標大小  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 與裝置無關的像素為單位轉譯目標的目前大小  
  
##  <a name="gettags"></a>  CRenderTarget::GetTags  
 取得後續繪圖作業的標籤。  
  
```  
void GetTags(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `tag1`  
 包含針對後續的繪圖作業的第一個標籤。 這個參數會以未初始化的狀態傳遞。 如果指定 NULL，則會擷取此參數沒有值。  
  
 `tag2`  
 包含針對後續的繪圖作業的第二個標籤。 這個參數會以未初始化的狀態傳遞。 如果指定 NULL，則會擷取此參數沒有值。  
  
##  <a name="gettextantialiasmode"></a>  CRenderTarget::GetTextAntialiasMode  
 取得目前的消除鋸齒模式文字和繪製作業的圖像。  
  
```  
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前反鋸齒文字和繪製作業的字符的模式。  
  
##  <a name="gettextrenderingparams"></a>  CRenderTarget::GetTextRenderingParams  
 擷取呈現目標的目前文字呈現選項。  
  
```  
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```  
  
### <a name="parameters"></a>參數  
 `textRenderingParams`  
 此方法傳回時，textRenderingParamscontains 呈現目標的指標位址的目前文字呈現選項。  
  
##  <a name="gettransform"></a>  CRenderTarget::GetTransform  
 將指定的轉換套用至呈現目標，取代現有的轉換。 後續的所有繪圖作業發生在轉換後的空間。  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>參數  
 `transform`  
 要套用到轉譯目標的轉換。  
  
##  <a name="issupported"></a>  CRenderTarget::IsSupported  
 指出轉譯目標是否支援指定的屬性  
  
```  
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;  
```  
  
### <a name="parameters"></a>參數  
 `renderTargetProperties`  
 要測試的呈現目標屬性  
  
### <a name="return-value"></a>傳回值  
 如果此呈現目標; 的支援指定的呈現目標屬性，則為 TRUE。否則為 FALSE  
  
##  <a name="isvalid"></a>  CRenderTarget::IsValid  
 檢查資源的有效性  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源有效，則為 TRUE否則為 FALSE。  
  
##  <a name="m_lstresources"></a>  CRenderTarget::m_lstResources  
 CD2DResource 物件指標的清單。  
  
```  
CObList m_lstResources;  
```  
  
##  <a name="m_prendertarget"></a>  CRenderTarget::m_pRenderTarget  
 ID2D1RenderTarget 物件的指標。  
  
```  
ID2D1RenderTarget* m_pRenderTarget;  
```  
  
##  <a name="m_ptextformatdefault"></a>  CRenderTarget::m_pTextFormatDefault  
 包含預設文字格式的 CD2DTextFormat 物件的指標。  
  
```  
CD2DTextFormat* m_pTextFormatDefault;  
```  
  
##  <a name="operator_id2d1rendertarget_star"></a>  CRenderTarget::operator ID2D1RenderTarget *  
 傳回 ID2D1RenderTarget 介面  
  
```  
operator ID2D1RenderTarget*();
```   
  
### <a name="return-value"></a>傳回值  
 ID2D1RenderTarget 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="popaxisalignedclip"></a>  CRenderTarget::PopAxisAlignedClip  
 從轉譯目標中移除的座標軸對齊的最後一個剪輯。 呼叫這個方法之後，後續的繪圖作業將不再套用剪輯。  
  
```  
void PopAxisAlignedClip();
```  
  
##  <a name="poplayer"></a>  CRenderTarget::PopLayer  
 停止重新導向至最後一個 PushLayer 所指定的圖層的繪圖作業呼叫。  
  
```  
void PopLayer();
```  
  
##  <a name="pushaxisalignedclip"></a>  CRenderTarget::PushAxisAlignedClip  
 從轉譯目標中移除的座標軸對齊的最後一個剪輯。 呼叫這個方法之後，後續的繪圖作業將不再套用剪輯。  
  
```  
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,  
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```  
  
### <a name="parameters"></a>參數  
 `rectClip`  
 大小和位置的裁剪區域中，以與裝置無關的像素為單位。  
  
 `mode`  
 用於繪製的邊緣具有子像素界限的剪輯 rects，以及混合的剪輯的場景內容進行反鋸齒處理模式。 混合，其會執行一旦 PopAxisAlignedClip 方法時呼叫，並不適用於每個圖層中的基本型別。  
  
##  <a name="pushlayer"></a>  CRenderTarget::PushLayer  
 將指定的圖層加入至呈現目標，讓呼叫 PopLayer 之前收到後續的所有繪圖作業。  
  
```  
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,  
    CD2DLayer& layer);
```  
  
### <a name="parameters"></a>參數  
 `layerParameters`  
 內容的界限、 幾何的遮罩、 不透明度、 不透明度遮罩和圖層的反鋸齒功能選項。  
  
 `layer`  
 接收後續的繪圖作業的圖層。  
  
##  <a name="restoredrawingstate"></a>  CRenderTarget::RestoreDrawingState  
 呈現目標的繪圖狀態設定為指定 ID2D1DrawingStateBlock 的。  
  
```  
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```  
  
### <a name="parameters"></a>參數  
 `drawingStateBlock`  
 呈現目標的繪製新狀態。  
  
##  <a name="savedrawingstate"></a>  CRenderTarget::SaveDrawingState  
 將目前的繪圖狀態儲存至指定 ID2D1DrawingStateBlock。  
  
```  
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;  
```  
  
### <a name="parameters"></a>參數  
 `drawingStateBlock`  
 此方法傳回時，包含目前繪圖呈現目標的狀態。 這個參數必須先初始化，再將其傳遞至方法。  
  
##  <a name="setantialiasmode"></a>  CRenderTarget::SetAntialiasMode  
 設定呈現目標的消除鋸齒模式。 消除鋸齒模式適用於後續的所有繪圖作業，但不包括文字和繪製作業的圖像。  
  
```  
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```  
  
### <a name="parameters"></a>參數  
 `antialiasMode`  
 未來的繪圖作業的消除鋸齒模式。  
  
##  <a name="setdpi"></a>  CRenderTarget::SetDpi  
 設定每英吋點數 (DPI) 呈現目標。  
  
```  
void SetDpi(const CD2DSizeF& sizeDPI);
```  
  
### <a name="parameters"></a>參數  
 `sizeDPI`  
 大於或等於零的值會指定水平/verticalDPI 呈現目標。  
  
##  <a name="settags"></a>  CRenderTarget::SetTags  
 指定針對後續的繪圖作業的標籤。  
  
```  
void SetTags(
    D2D1_TAG tag1,  
    D2D1_TAG tag2);
```  
  
### <a name="parameters"></a>參數  
 `tag1`  
 標籤以套用到後續的繪圖作業。  
  
 `tag2`  
 標籤以套用到後續的繪圖作業。  
  
##  <a name="settextantialiasmode"></a>  CRenderTarget::SetTextAntialiasMode  
 指定要用於後續文字和圖像繪圖作業的消除鋸齒模式。  
  
```  
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```  
  
### <a name="parameters"></a>參數  
 `textAntialiasMode`  
 要用於後續文字和繪製作業的字符的消除鋸齒模式。  
  
##  <a name="settextrenderingparams"></a>  CRenderTarget::SetTextRenderingParams  
 指定要套用到所有後續文字和繪製作業的圖像的文字呈現選項。  
  
```  
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```  
  
### <a name="parameters"></a>參數  
 `textRenderingParams`  
 要套用到所有後續文字和繪製作業; 圖像的文字轉譯選項NULL 以清除目前的文字呈現選項。  
  
##  <a name="settransform"></a>  CRenderTarget::SetTransform  
 將指定的轉換套用至呈現目標，取代現有的轉換。 後續的所有繪圖作業發生在轉換後的空間。  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);  
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```  
  
### <a name="parameters"></a>參數  
 `transform`  
 要套用到轉譯目標的轉換。  
  
##  <a name="verifyresource"></a>  CRenderTarget::VerifyResource  
 驗證 CD2DResource 物件的有效性。如果它已不存在，請建立的物件。  
  
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
