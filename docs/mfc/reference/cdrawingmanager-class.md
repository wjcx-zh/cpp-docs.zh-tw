---
title: CDrawingManager 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
dev_langs:
- C++
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36b297f8ea4cb4b6e6a0866a717f9107281cce37
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957425"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager 類別
`CDrawingManager`類別會實作複雜繪圖演算法。  
  
## <a name="syntax"></a>語法  
  
```  
class CDrawingManager : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|建構 `CDrawingManager` 物件。|  
|`CDrawingManager::~CDrawingManager`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|建立應用程式可以直接寫入 32 位元裝置獨立點陣圖 (DIB)。|  
|[CDrawingManager::DrawAlpha](#drawalpha)|顯示具有透明或半透明的像素的點陣圖。|  
|[CDrawingManager::DrawRotated](#drawrotated)|旋轉的來源 DC + /-90 度的給定矩形內的內容|  
|[CDrawingManager::DrawEllipse](#drawellipse)|繪製橢圓形使用提供的填滿和框線色彩。|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|會繪製信號，填滿漸層色彩。|  
|[CDrawingManager::DrawLine CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|繪製線條。|  
|[CDrawingManager::DrawRect](#drawrect)|繪製有提供填滿和框線色彩的矩形。|  
|[CDrawingManager::DrawShadow](#drawshadow)|繪製一個陰影的矩形區域。|  
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|填滿之矩形區域，使用兩個色彩漸層。|  
|[CDrawingManager::FillGradient](#fillgradient)|使用指定的色彩漸層，填滿之矩形區域。|  
|[CDrawingManager::FillGradient2](#fillgradient2)|使用指定的色彩漸層，填滿之矩形區域。 同時指定漸層的色彩變更方向。|  
|[CDrawingManager::GrayRect](#grayrect)|使用指定的灰色色彩，填滿的矩形。|  
|[CDrawingManager::HighlightRect](#highlightrect)|反白顯示的矩形區域。|  
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|將色彩從 HLS 表示法轉換為 RGB 表示。|  
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|將色彩從 HLS 表示法轉換為 RGB 表示。|  
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|將色彩從 HSV 表示法轉換為 RGB 表示。|  
|[CDrawingManager::HuetoRGB](#huetorgb)|Helper 方法，將紅色、 綠色或藍色元件的色調值。|  
|[CDrawingManager::MirrorRect](#mirrorrect)|翻轉的矩形區域。|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|Helper 方法，決定半透明的像素的完稿色彩。|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|建立可用來當做陰影的點陣圖。|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|將色彩的 RGB 表示轉換為 HSL 表示。|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|將色彩的 RGB 表示轉換為 HSV 表示。|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|色彩部分透明的像素點陣圖中的 helper 方法。|  
|[CDrawingManager::SetPixel](#setpixel)|指定的色彩變更單一像素點陣圖中的 helper 方法。|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|結合兩個色彩來根據加權比例。|  
  
## <a name="remarks"></a>備註  
 `CDrawingManager`類別會提供函數來繪製陰影、 色彩漸層和反白顯示的矩形。 它也會執行 alpha 透明混色。 若要直接變更應用程式的 UI，您可以使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdrawmanager.h  
  
##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager  
 建構[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)物件。  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>參數  
 [in]*dc*  
 裝置內容的參考。 `CDrawingManager`繪圖會使用此內容。  
  
##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32  
 建立應用程式可以直接寫入 32 位元裝置獨立點陣圖 (DIB)。  
  
```  
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,  
    void** pBits);
 
static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,  
    COLORREF clrTransparent = -1);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*大小*|A [CSize](../../atl-mfc-shared/reference/csize-class.md)參數，指出點陣圖的大小。|  
|[out]*pBits*|指向接收的 DIB 位置的資料指標的位元值。|  
|*點陣圖*|原始點陣圖的控制代碼|  
|*clrTransparent*|指定的原始點陣圖的透明色彩的 RGB 值。|  
  
### <a name="return-value"></a>傳回值  
 控制代碼，新建立的 DIB 點陣圖如果此方法成功。否則`NULL`。  
  
### <a name="remarks"></a>備註  
 如需如何建立 DIB 點陣圖的詳細資訊，請參閱[CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491)。  
  
##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha  
 顯示具有透明或半透明的像素的點陣圖。  
  
```  
void DrawAlpha(
    CDC* pDstDC,  
    const CRect& rectDst,  
    CDC* pSrcDC,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDstDC*  
 目的地裝置內容的指標。  
  
 [in]*rectDst*  
 目的矩形。  
  
 [in]*pSrcDC*  
 來源裝置內容的指標。  
  
 [in]*rectSrc*  
 來源矩形。  
  
### <a name="remarks"></a>備註  
 這個方法會執行 alpha 透明混色兩個點陣圖。 如需 alpha 透明混色的詳細資訊，請參閱[AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) Windows SDK 中。  
  
##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse  
 繪製橢圓形使用提供的填滿和框線色彩。  
  
```  
void DrawEllipse(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 橢圓形之周框。  
  
 [in]*clrFill*  
 這個方法會使用以填滿橢圓形的色彩。  
  
 [in]*clrLine*  
 這個方法會使用為橢圓形的框線色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回不繪製橢圓形，如果其中一個色彩設為-1。 它也會傳回不繪製橢圓形，如果週框的任一個維度是 0。  
  
##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing  
 會繪製信號，填滿漸層色彩。  
  
```  
BOOL DrawGradientRing(
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    COLORREF colorBorder,  
    int nAngle,  
    int nWidth,  
    COLORREF clrFace = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)參數，指定漸層的環形的界限。  
  
 [in]*colorStart*  
 漸層的第一個色彩。  
  
 [in]*colorFinish*  
 最後一個漸層的色彩。  
  
 [in]*colorBorder*  
 框線的色彩。  
  
 [in]*nAngle*  
 指定初始的漸層繪製角度參數。 這個值應該是介於 0 和 360 之間。  
  
 [in]*nWidth*  
 此環形的框線寬度。  
  
 [in]*clrFace*  
 環形的內部的色彩。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 所定義的矩形*rect*必須至少 5 像素寬和 5 像素高。  
  
##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine CDrawingManager::DrawLineA  
 繪製線條。  
  
```  
void DrawLine(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    COLORREF clrLine);
 
void DrawLineA(
    double x1,  
    double y1,  
    double x2,  
    double y2,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*x1*|線條開始位置的 x 座標。|  
|[in]*y1*|線條開始位置的 y 座標。|  
|[in]*x2*|線條結束位置的 x 座標。|  
|[in]*y2*|線條結束位置的 y 座標。|  
|[in]*clrLine*|線條的色彩。|  
  
### <a name="remarks"></a>備註  
 如果這個方法會失敗*clrLine*等於-1。  
  
##  <a name="drawrect"></a>  CDrawingManager::DrawRect  
 繪製有提供填滿和框線色彩的矩形。  
  
```  
void DrawRect(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 矩形界限。  
  
 [in]*clrFill*  
 這個方法會使用以填滿之矩形的色彩。  
  
 [in]*clrLine*  
 這個方法會使用矩形的框線色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回但不繪製矩形，如果其中一個色彩設為-1。 它也會傳回如果任一個矩形的維度是 0。  
  
##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow  
 繪製一個陰影的矩形區域。  
  
```  
BOOL DrawShadow(
    CRect rect,  
    int nDepth,  
    int iMinBrightness = 100,  
    int iMaxBrightness = 50,  
    CBitmap* pBmpSaveBottom = NULL,  
    CBitmap* pBmpSaveRight = NULL,  
    COLORREF clrBase = (COLORREF)-1,  
    BOOL bRightShadow = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 在您的應用程式中的矩形區域。 繪圖管理員將此區域下方繪製一個陰影。  
  
 [in]*nDepth*  
 高度與寬度的陰影。  
  
 [in]*iMinBrightness*  
 陰影的最小的亮度。  
  
 [in]*iMaxBrightness*  
 陰影的最大的亮度。  
  
 [in]*pBmpSaveBottom*  
 包含陰影的下半部的影像之點陣圖的指標。  
  
 [in]*pBmpSaveRight*  
 指標，包含該映像，矩形右側繪製陰影的點陣圖。  
  
 [in]*clrBase*  
 陰影的色彩。  
  
 [in]*bRightShadow*  
 表示如何繪製陰影的布林參數。 如果*bRightShadow*是`TRUE`，`DrawShadow`矩形右側上繪製一個陰影。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您也可以使用參數的底端和右方陰影提供兩個有效的點陣圖*pBmpSaveBottom*和*pBmpSaveRight*。 如果這些[CBitmap](../../mfc/reference/cbitmap-class.md)物件有附加的 GDI 物件`DrawShadow`當成陰影的點陣圖。 如果`CBitmap`參數沒有附加的 GDI 物件`DrawShadow`繪製陰影，並將點陣圖附加至參數。 在未來呼叫`DrawShadow`，您可以提供這些點陣圖，以加快繪製程序。 如需有關`CBitmap`類別和 GDI 物件，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
 如果其中一個參數是`NULL`，`DrawShadow`時，會自動繪製陰影。  
  
 如果您設定*bRightShadow*至`FALSE`、 下方和左側的矩形區域，就會繪製陰影。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`DrawShadow`方法`CDrawingManager`類別。 此程式碼片段是部分[屬性工作表示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]  
  
##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient  
 填滿之矩形區域，使用兩個色彩漸層。  
  
```  
void Fill4ColorsGradient(
    CRect rect,  
    COLORREF colorStart1,  
    COLORREF colorFinish1,  
    COLORREF colorStart2,  
    COLORREF colorFinish2,  
    BOOL bHorz = TRUE,  
    int nPercentage = 50);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 要填滿的矩形。  
  
 [in]*colorStart1*  
 初始的第一個色彩漸層色彩。  
  
 [in]*colorFinish1*  
 最終的第一個色彩漸層色彩。  
  
 [in]*colorStart2*  
 初始的第二個色彩漸層色彩。  
  
 [in]*colorFinish2*  
 最後第二個色彩漸層色彩。  
  
 [in]*bHorz*  
 布林值，指出參數是否`Fill4ColorsGradient`水平或垂直漸層的色彩。 `TRUE` 表示水平漸層。  
  
 [in]*nPercentage*  
 從 0 到 100 之間的整數。 這個值會指出要使用的第一個色彩漸層填滿的矩形的百分比。  
  
### <a name="remarks"></a>備註  
 當使用兩個色彩漸層填滿的矩形時，它們是位於彼此的上方或下一個的值而定， *bHorz*。 每個色彩漸層方法會獨立計算[CDrawingManager::FillGradient](#fillgradient)。  
  
 如果這個方法會產生判斷提示失敗*nPercentage*小於 0 或大於 100。  
  
##  <a name="fillgradient"></a>  CDrawingManager::FillGradient  
 使用指定的色彩漸層，填滿之矩形區域。  
  
```  
void FillGradient(
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    BOOL bHorz = TRUE,  
    int nStartFlatPercentage = 0,  
    int nEndFlatPercentage = 0);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 要填滿的矩形區域。  
  
 [in]*colorStart*  
 漸層的第一個色彩。  
  
 [in]*colorFinish*  
 最終的漸層色彩。  
  
 [in]*bHorz*  
 布林值參數，指定是否`FillGradient`應該繪製的水平或垂直漸層。  
  
 [in]*nStartFlatPercentage*  
 矩形的百分比，`FillGradient`填入*colorStart*漸層開始之前。  
  
 [in]*nEndFlatPercentage*  
 矩形的百分比，`FillGradient`填入*colorFinish*之後完成之漸層。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`FillGradient`方法`CDrawingManager`類別。 此程式碼片段是部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]  
  
##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2  
 使用指定的色彩漸層，填滿之矩形區域。  
  
```  
void FillGradient2 (
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    int nAngle = 0);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 要填滿的矩形區域。  
  
 [in]*colorStart*  
 漸層的第一個色彩。  
  
 [in]*colorFinish*  
 最後一個漸層的色彩。  
  
 [in]*nAngle*  
 整數，介於 0 和 360 之間。 此參數指定的色彩漸層的方向。  
  
### <a name="remarks"></a>備註  
 使用*nAngle*以指定的色彩漸層的方向。 當您指定的色彩漸層的方向時，您也指定的色彩漸層的開始位置。 值為 0 *nAngle*指出所使用漸層開始從矩形的頂端。 做為*nAngle*增加時，開始位置的漸層會根據角度逆時針方向移動。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`FillGradient2`方法`CDrawingManager`類別。 此程式碼片段是部分[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]  
  
##  <a name="grayrect"></a>  CDrawingManager::GrayRect  
 使用指定的灰色色彩，填滿的矩形。  
  
```  
BOOL GrayRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    COLORREF clrDisabled = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 要填滿的矩形區域。  
  
 [in]*nPercentage*  
 您想要在矩形的灰色的百分比。  
  
 [in]*clrTransparent*  
 透明的色彩。  
  
 [in]*clrDisabled*  
 如果這個方法會使用如變形飽和的色彩*nPercentage*設定為-1。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果該方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 參數*nPercentage*，較低的值表示較深的色彩。  
  
 最大值*nPercentage*為 200。 大於 200 的值不會變更矩形的外觀。 如果值為-1，這個方法會使用*clrDisabled*限制飽和度的矩形。  
  
##  <a name="highlightrect"></a>  CDrawingManager::HighlightRect  
 反白顯示的矩形區域。  
  
```  
BOOL HighlightRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    int nTolerance = 0,  
    COLORREF clrBlend = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 若要反白顯示的矩形區域。  
  
 [in]*nPercentage*  
 指出反白顯示的應該是透明程度的百分比。  
  
 [in]*clrTransparent*  
 透明的色彩。  
  
 [in]*nTolerance*  
 介於 0 和 255 之間整數，表示色彩容錯。  
  
 [in]*clrBlend*  
 基底色彩混合。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果*nPercentage*介於 0 到 99 之間，`HighlightRect`使用 alpha 混色演算法。 如需 alpha 混色的詳細資訊，請參閱[Alpha 混色線條和填色](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果*nPercentage*為-1，這個方法會使用預設的反白顯示層級。 如果*nPercentage*是 100，這個方法不做任何動作，並傳回`TRUE`。  
  
 此方法會使用參數*nTolerance*來判斷是否要反白顯示的矩形區域。 若要反白顯示在矩形中，您的應用程式的背景色彩之間的差異和*clrTransparent*必須是小於*nTolerance* （紅色、 綠色和藍色） 的每個色彩元件中。  
  
##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE  
 將色彩從 HLS 表示法轉換為 RGB 表示。  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>參數  
 [in]*H*  
 0 到 1 之間的數字表示的色彩色調。  
  
 [in]*L*  
 0 到 1 之間的數字表示的色彩亮度。  
  
 [in]*S*  
 0 到 1 之間的數字表示的色彩飽和度。  
  
### <a name="return-value"></a>傳回值  
 提供 HLS 色彩的 RGB 呈現。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 這個方法和`CDrawingManager::HLStoRGB_TWO`方法執行相同的作業，但需要不同的值，如*H*參數。 在此方法中， *H*是圓形的百分比。 在`CDrawingManager::HLStoRGB_TWO`方法， *H*是介於 0 到 360 度，表示這兩個紅色程度值。 例如， `HLStoRGB_ONE`，0.25 的值*H*相當於值與 90 `HLStoRGB_TWO`。  
  
##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO  
 將色彩從 HLS 表示法轉換為 RGB 表示。  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>參數  
 [in]*H*  
 表示色彩的色調 0 和 360 之間的數字。  
  
 [in]*L*  
 0 到 1 之間的數字表示的色彩亮度。  
  
 [in]*S*  
 0 到 1 之間的數字表示的色彩飽和度。  
  
### <a name="return-value"></a>傳回值  
 提供 HLS 色彩的 RGB 呈現。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 這個方法和[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法執行相同的作業，但需要不同的值，如*H*參數。 在此方法中， *H*是介於 0 到 360 度，表示這兩個紅色程度值。 在[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法， *H*是圓形的百分比。 例如， `HLStoRGB_ONE`，0.25 的值*H*相當於值與 90 `HLStoRGB_TWO`。  
  
##  <a name="hsvtorgb"></a>  CDrawingManager::HSVtoRGB  
 將色彩從 HSV 表示法轉換為 RGB 表示。  
  
```  
static COLORREF __stdcall HSVtoRGB(
    double H,  
    double S,  
    double V);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*H*|表示色彩的色調 0 和 360 之間的數字。|  
|[in]*S*|0 到 1 之間的數字表示的色彩飽和度。|  
|[in]*V*|0 到 1 之間的數字表示的色彩值。|  
  
### <a name="return-value"></a>傳回值  
 提供 HSV 色彩的 RGB 呈現。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB  
 將紅色、 綠色或藍色元件的色調值。  
  
```  
static double __stdcall HuetoRGB(
    double m1,  
    double m2,  
    double h);

 
static BYTE __stdcall HueToRGB(
    float rm1,  
    float rm2,  
    float rh);
```  
  
### <a name="parameters"></a>參數  
 [in]*m1*  
 請參閱＜備註＞。  
  
 [in]*m2*  
 請參閱＜備註＞。  
  
 [in]*h*  
 請參閱＜備註＞。  
  
 [in]*rm1*  
 請參閱＜備註＞。  
  
 [in]*rm2*  
 請參閱＜備註＞。  
  
 [in]*rh*  
 請參閱＜備註＞。  
  
### <a name="return-value"></a>傳回值  
 提供的色調個別紅色、 綠色或藍色元件。  
  
### <a name="remarks"></a>備註  
 這個方法是 helper 方法，`CDrawingManager`類別用來計算個別的紅色、 綠色和藍色元件 HSV 或 HSL 的表示法中的色彩。 這個方法不是直接由程式設計人員呼叫。 輸入的參數是取決於轉換演算法的值。  
  
 若要轉換的 RGB 表示 HSV 或 HSL 色彩，呼叫下列方法之一：  
  
- [CDrawingManager::HSVtoRGB](#hsvtorgb)  
  
- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)  
  
- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)  
  
##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect  
 翻轉的矩形區域。  
  
```  
void MirrorRect(
    CRect rect,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
 若要翻轉區域的週框。  
  
 [in]*bHorz*  
 布林值參數，指出矩形是否會水平或垂直翻轉。  
  
### <a name="remarks"></a>備註  
 這個方法可以翻轉所擁有的裝置任何的內容區域`CDrawingManager`類別。 如果*bHorz*設`TRUE`，這個方法會水平翻轉的區域。 否則，它在區域垂直翻轉。  
  
##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha  
 計算半透明的像素的完稿色彩。  
  
```  
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,  
    int percent);
 
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,  
    double percentR,  
    double percentG,  
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,  
    COLORREF dstPixel,  
    int percent);
```  
  
### <a name="parameters"></a>參數  
 [in]*srcPixel*  
 初始像素色彩。  
  
 [in]*百分比*  
 表示數字 0 到 100 之間的透明度百分比。 值為 100 表示初始色彩是完全透明的。  
  
 [in]*percentR*  
 表示數字 0 到 100 之間的紅色元件的透明度百分比。  
  
 [in]*percentG*  
 表示數字 0 到 100 之間的綠色元件的透明度百分比。  
  
 [in]*percentB*  
 表示數字 0 到 100 之間的藍色元件的透明度百分比。  
  
 [in]*dstPixel*  
 基底像素色彩。  
  
### <a name="return-value"></a>傳回值  
 半透明的像素的完稿色彩。  
  
### <a name="remarks"></a>備註  
 這是協助程式類別，可著色半透明的點陣圖，而且不是直接由程式設計人員呼叫。  
  
 當您使用的方法版本*dstPixel*，最終色彩是組合*dstPixel*和*srcPixel*。 *SrcPixel*色彩就是透明色彩的基準色彩透過*dstPixel*。  
  
##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask  
 建立可用來當做陰影的點陣圖。  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>參數  
 [in]*nDepth*  
 高度與寬度的陰影。  
  
 [in]*clrBase*  
 陰影的色彩。  
  
 [in]*iMinBrightness*  
 陰影的最小的亮度。  
  
 [in]*iMaxBrightness*  
 陰影的最大的亮度。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功; 建立點陣圖的控制代碼否則`NULL`。  
  
### <a name="remarks"></a>備註  
 如果*nDepth*是設定為 0，這個方法會結束並傳回`NULL`。 如果*nDepth*小於 3，陰影的高度與寬度會設定為 3 的像素為單位。  
  
##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL  
 將色彩從紅色、 綠色和藍色 (RGB) 表示法色調、 飽和度和亮度 (HSL) 表示法。  
  
```  
static void __stdcall RGBtoHSL(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* L);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*rgb*|RGB 值中的色彩。|  
|[out]*H*|Double 值，這個方法儲存的色彩色調指標。|  
|[out]*S*|Double 值，這個方法儲存的色彩飽和度指標。|  
|[out]*L*|Double 值，這個方法儲存的色彩亮度指標。|  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 傳回的值*H*以介於 0 和 1 0 和 1 代表紅色分數。 傳回的值*S*和*L*是介於 0 和 1 之間的數字。  
  
##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV  
 將色彩的 RGB 表示轉換為 HSV 表示。  
  
```  
static void __stdcall RGBtoHSV(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* V);
```  
  
### <a name="parameters"></a>參數  
 [in]*rgb*  
 要轉換的 RGB 表示法中的色彩。  
  
 [out]*H*  
 Double 值，這個方法會產生的色彩色調的儲存位置指標。  
  
 [out]*S*  
 Double 值，這個方法會產生的色彩飽和度的儲存位置指標。  
  
 [out]*V*  
 Double 值，這個方法會產生的色彩值的儲存位置指標。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 傳回的值*H*是介於 0 和 360 之間的數字 0 到 360 度表示紅色。 傳回值*S*和*V*是介於 0 和 1 之間的數字。  
  
##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel  
 色彩透明的像素點陣圖中。  
  
```  
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,  
    CRect rect,  
    int x,  
    int y,  
    int percent,  
    int iShadowSize,  
    COLORREF clrBase = (COLORREF)-1,  
    BOOL bIsRight = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*pBits*  
 點陣圖的位元值指標。  
  
 [in]*rect*  
 在您的應用程式中的矩形區域。 繪圖管理員繪製陰影下面和此區域的右側。  
  
 [in]*x*  
 色彩的像素水平座標。  
  
 [in]*y*  
 像素色彩的垂直座標。  
  
 [in]*百分比*  
 透明度百分比。  
  
 [in]*iShadowSize*  
 高度與寬度的陰影。  
  
 [in]*clrBase*  
 陰影的色彩。  
  
 [in]*bIsRight*  
 表示色彩的像素的布林參數。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="remarks"></a>備註  
 這個方法是 helper 方法，以供[CDrawingManager::DrawShadow](#drawshadow)方法。 我們建議，如果您想要繪製一個陰影，呼叫`CDrawingManager::DrawShadow`改為。  
  
 如果*bIsRight*設`TRUE`，色彩的像素為單位*x*像素的右邊緣*rect*。 如果是`FALSE`，色彩的像素為單位*x*像素的左邊緣*rect*。  
  
##  <a name="setpixel"></a>  CDrawingManager::SetPixel  
 變更單一像素點陣圖中的指定的色彩。  
  
```  
static void __stdcall SetPixel(
    COLORREF* pBits,  
    int cx,  
    int cy,  
    int x,  
    int y,  
    COLORREF color);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*pBits*|點陣圖的位元值指標。|  
|[in]*cx*|點陣圖的寬度總計。|  
|[in]*cy*|總點陣圖的高度。|  
|[in]*x*|若要變更點陣圖中的像素 x 軸座標。|  
|[in]*y*|若要變更點陣圖中的像素的 y 座標。|  
|[in]*色彩*|像素所提供的座標識別新的色彩。|  
  
##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors  
 結合兩個色彩來根據加權比例。  
  
```  
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,  
    COLORREF color2,  
    double dblLumRatio = 1.,  
    int k1 = 1,  
    int k2 = 1);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*color1*|第一個色彩混合。|  
|[in]*色 2*|第二個色彩混合。|  
|[in]*dblLumRatio*|新的色彩亮度的比率。 `SmartMixColors` 然後再判斷完稿色彩乘以此比率混合色彩的亮度。|  
|[in]*k1*|第一個色彩加權的比例。|  
|[in]*k2*|第二個色彩加權的比例。|  
  
### <a name="return-value"></a>傳回值  
 表示加權的混合提供色彩的色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會失敗並發生錯誤，如果*k1*或*k2*小於零。 如果這兩個參數會設定為 0，則方法會傳回`RGB(0, 0, 0)`。  
  
 加權的比例使用以下公式計算: (color1 * k1 + 色 2 \* k2) /(k1 + k2)。 決定加權的比例之後，方法會計算混合的色彩亮度。 然後將相乘的亮度*dblLumRatio*。 如果值大於 1.0，方法會將混合色彩的亮度設定新的值。 否則，亮度會設為 1.0。  
  
##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated  
 將給定矩形內的 DC 內容的來源旋轉 90 度。  
  
```  
void DrawRotated(
    CRect rectDest,  
    CDC& dcSrc,  
    BOOL bClockWise);
```  
  
### <a name="parameters"></a>參數  
 *rectDest*  
 目的矩形。  
  
 *dcSrc*  
 來源裝置內容。  
  
 *bClockWise*  
 `TRUE` 表示旋轉 + 90 度。`FALSE`表示旋轉-90 度。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
