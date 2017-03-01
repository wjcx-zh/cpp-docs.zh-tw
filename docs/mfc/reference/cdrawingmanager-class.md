---
title: "CDrawingManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDrawingManager
dev_langs:
- C++
helpviewer_keywords:
- CDrawingManager class
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
caps.latest.revision: 30
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 53929fff6df57b4e5fe00572f8a7cec8a218c638
ms.lasthandoff: 02/24/2017

---
# <a name="cdrawingmanager-class"></a>CDrawingManager 類別
`CDrawingManager`類別會實作複雜繪圖演算法。  
  
## <a name="syntax"></a>語法  
  
```  
class CDrawingManager : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|建構 `CDrawingManager` 物件。|  
|`CDrawingManager::~CDrawingManager`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|建立應用程式可以直接寫入至 32 位元與裝置無關點陣圖 (DIB)。|  
|[CDrawingManager::DrawAlpha](#drawalpha)|顯示具有透明或半透明的像素的點陣圖。|  
|[CDrawingManager::DrawRotated](#drawrotated)|旋轉的來源 DC + /-90 度的指定矩形內部的內容|  
|[CDrawingManager::DrawEllipse](#drawellipse)|繪製橢圓形與提供的填滿和框線色彩。|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|繪製信號，使用色彩漸層填滿它。|  
|[CDrawingManager::DrawLine CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|繪製直線。|  
|[CDrawingManager::DrawRect](#drawrect)|繪製的矩形，以提供的填滿和框線色彩。|  
|[CDrawingManager::DrawShadow](#drawshadow)|繪製的矩形區域的陰影。|  
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|填滿的矩形區域，使用兩個色彩漸層。|  
|[CDrawingManager::FillGradient](#fillgradient)|使用指定的色彩漸層，填滿的矩形區域。|  
|[CDrawingManager::FillGradient2](#fillgradient2)|使用指定的色彩漸層，填滿的矩形區域。 也會指定變更的漸層色彩的方向。|  
|[CDrawingManager::GrayRect](#grayrect)|使用指定的灰色色彩，填滿的矩形。|  
|[CDrawingManager::HighlightRect](#highlightrect)|反白顯示的矩形區域。|  
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|從 HLS 表示法，將色彩轉換為 RGB 表示。|  
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|從 HLS 表示法，將色彩轉換為 RGB 表示。|  
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|從 HSV 表示法，將色彩轉換為 RGB 表示。|  
|[CDrawingManager::HuetoRGB](#huetorgb)|將色調值轉換成紅色、 綠色或藍色元件的 helper 方法。|  
|[CDrawingManager::MirrorRect](#mirrorrect)|翻轉的矩形區域。|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|決定半透明的像素的最終色彩的 helper 方法。|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|建立可用來當做陰影的點陣圖。|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|將色彩 RGB 表示之間相互轉換 HSL 表示。|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|從 RGB 表示法，將色彩轉換為 HSV 表示。|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|色彩點陣圖中的部分透明像素的 helper 方法。|  
|[CDrawingManager::SetPixel](#setpixel)|變更指定的色彩點陣圖中的單一像素的 helper 方法。|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|結合兩個色彩來根據加權的比率。|  
  
## <a name="remarks"></a>備註  
 `CDrawingManager`類別所提供函式可繪製陰影、 色彩漸層和反白顯示的矩形。 它也會執行 alpha 混色。 若要直接變更應用程式的 UI，您可以使用這個類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdrawmanager.h  
  
##  <a name="a-namecdrawingmanagera--cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager  
 建構[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)物件。  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>參數  
 [in] `dc`  
 裝置內容的參考。 `CDrawingManager`繪圖會使用此內容。  
  
##  <a name="a-namecreatebitmap32a--cdrawingmanagercreatebitmap32"></a><a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32  
 建立應用程式可以直接寫入至 32 位元與裝置無關點陣圖 (DIB)。  
  
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
|[in] `size`|A [CSize](../../atl-mfc-shared/reference/csize-class.md)參數，指出點陣圖的大小。|  
|[輸出] `pBits`|指向接收 DIB 位置的資料指標的位元值。|  
|`bitmap`|原始點陣圖控制代碼|  
|`clrTransparent`|指定原始點陣圖的透明色彩的 RGB 值。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，新建立 DIB 點陣圖控制代碼否則`NULL`。  
  
### <a name="remarks"></a>備註  
 如需如何建立 DIB 點陣圖的詳細資訊，請參閱[CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491)。  
  
##  <a name="a-namedrawalphaa--cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>CDrawingManager::DrawAlpha  
 顯示具有透明或半透明的像素的點陣圖。  
  
```  
void DrawAlpha(
    CDC* pDstDC,  
    const CRect& rectDst,  
    CDC* pSrcDC,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDstDC`  
 目的地裝置內容的指標。  
  
 [in] `rectDst`  
 目的矩形。  
  
 [in] `pSrcDC`  
 來源裝置內容的指標。  
  
 [in] `rectSrc`  
 來源矩形。  
  
### <a name="remarks"></a>備註  
 此方法執行兩個點陣圖 alpha 混色。 如需 alpha 混色的詳細資訊，請參閱[alphablend，還有旁邊](http://msdn.microsoft.com/library/windows/desktop/dd183351)Windows SDK 中。  
  
##  <a name="a-namedrawellipsea--cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>CDrawingManager::DrawEllipse  
 繪製橢圓形與提供的填滿和框線色彩。  
  
```  
void DrawEllipse(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 橢圓形之周框。  
  
 [in] `clrFill`  
 這個方法會使用以填滿橢圓形的色彩。  
  
 [in] `clrLine`  
 這個方法會使用為橢圓形的框線色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回不繪製橢圓形，如果其中一個色彩設定為-1。 它也會傳回不繪製橢圓形，如果週框的任一個維度是 0。  
  
##  <a name="a-namedrawgradientringa--cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawingManager::DrawGradientRing  
 繪製信號，使用色彩漸層填滿它。  
  
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
 [in] `rect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)參數，指定漸層的環形的界限。  
  
 [in] `colorStart`  
 漸層的第一個色彩。  
  
 [in] `colorFinish`  
 最後的漸層色彩。  
  
 [in] `colorBorder`  
 框線的色彩。  
  
 [in] `nAngle`  
 指定初始的漸層繪製角度參數。 這個值應該是介於 0 和 360 之間。  
  
 [in] `nWidth`  
 環框線的寬度。  
  
 [in] `clrFace`  
 此環形的內部色彩。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 所定義的矩形`rect`必須至少 5 個像素寬和 5 個像素高。  
  
##  <a name="a-namedrawlinecdrawingmanagerdrawlineaa--cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine CDrawingManager::DrawLineA  
 繪製直線。  
  
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
|[in] `x1`|行開頭位置的 x 座標。|  
|[in] `y1`|行開頭位置的 y 座標。|  
|[in] `x2`|線條的結束處的 x 座標。|  
|[in] `y2`|線條的結束處的 y 座標。|  
|[in] `clrLine`|線條的色彩。|  
  
### <a name="remarks"></a>備註  
 如果`clrLine`等於-1。  
  
##  <a name="a-namedrawrecta--cdrawingmanagerdrawrect"></a><a name="drawrect"></a>CDrawingManager::DrawRect  
 繪製的矩形，以提供的填滿和框線色彩。  
  
```  
void DrawRect(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 矩形的界限。  
  
 [in] `clrFill`  
 這個方法會使用以填滿之矩形的色彩。  
  
 [in] `clrLine`  
 這個方法會使用矩形的框線色彩。  
  
### <a name="remarks"></a>備註  
 此方法傳回時不繪製矩形，如果其中一個色彩設定為-1。 它也會傳回如果任一個矩形的維度是 0。  
  
##  <a name="a-namedrawshadowa--cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>CDrawingManager::DrawShadow  
 繪製的矩形區域的陰影。  
  
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
 [in] `rect`  
 在您的應用程式中的矩形區域。 繪圖管理員將此區域下方繪製一個陰影。  
  
 [in] `nDepth`  
 高度與寬度的陰影。  
  
 [in] `iMinBrightness`  
 陰影的最小的亮度。  
  
 [in] `iMaxBrightness`  
 最大陰影的亮度。  
  
 [in] `pBmpSaveBottom`  
 包含陰影的下半部的影像的點陣圖指標。  
  
 [in] `pBmpSaveRight`  
 包含陰影矩形右側繪製影像的點陣圖指標。  
  
 [in] `clrBase`  
 陰影的色彩。  
  
 [in] `bRightShadow`  
 布林值的參數，指出如何繪製陰影。 如果`bRightShadow`是`TRUE`，`DrawShadow`矩形右側上繪製一個陰影。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您也可以使用參數的底端和右側陰影提供兩個有效的點陣圖`pBmpSaveBottom`和`pBmpSaveRight`。 如果這些[CBitmap](../../mfc/reference/cbitmap-class.md)物件已附加的 GDI 物件`DrawShadow`會使用這些點陣圖，以陰影。 如果`CBitmap`參數沒有附加的 GDI 物件`DrawShadow`繪製陰影，並將點陣圖附加到參數。 在未來呼叫`DrawShadow`，您可以提供這些點陣圖可加快繪製程序。 如需詳細資訊`CBitmap`類別和 GDI 物件，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
 如果其中一個參數是`NULL`，`DrawShadow`時，會自動繪製陰影。  
  
 如果您設定`bRightShadow`至`FALSE`下, 面和矩形區域左側繪製陰影。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`DrawShadow`方法`CDrawingManager`類別。 此程式碼片段是一部分[屬性工作表示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_PropSheetDemo #&1;](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]  
  
##  <a name="a-namefill4colorsgradienta--cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient  
 填滿的矩形區域，使用兩個色彩漸層。  
  
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
 [in] `rect`  
 要填滿的矩形。  
  
 [in] `colorStart1`  
 初始的第一個色彩漸層色彩。  
  
 [in] `colorFinish1`  
 最終的第一個色彩漸層色彩。  
  
 [in] `colorStart2`  
 初始的第二個色彩漸層色彩。  
  
 [in] `colorFinish2`  
 最終的第二個色彩漸層色彩。  
  
 [in] `bHorz`  
 布林值，指出參數是否`Fill4ColorsGradient`水平或垂直漸層的色彩。 `TRUE`表示水平漸層。  
  
 [in] `nPercentage`  
 0-100 的整數。 這個值會指出要使用的第一個色彩漸層填滿的矩形的百分比。  
  
### <a name="remarks"></a>備註  
 兩個色彩漸層填滿矩形，就是位於彼此的上方或下一步，根據的值`bHorz`。 每個色彩漸層的方法獨立計算[CDrawingManager::FillGradient](#fillgradient)。  
  
 如果此方法會產生判斷提示失敗`nPercentage`小於 0 或大於 100。  
  
##  <a name="a-namefillgradienta--cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>CDrawingManager::FillGradient  
 使用指定的色彩漸層，填滿的矩形區域。  
  
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
 [in] `rect`  
 要填滿的矩形區域。  
  
 [in] `colorStart`  
 漸層的第一個色彩。  
  
 [in] `colorFinish`  
 最終的漸層色彩。  
  
 [in] `bHorz`  
 布林值參數，指定是否`FillGradient`應繪製的水平或垂直漸層。  
  
 [in] `nStartFlatPercentage`  
 矩形的百分比，`FillGradient`填入`colorStart`漸層開始之前。  
  
 [in] `nEndFlatPercentage`  
 矩形的百分比，`FillGradient`填入`colorFinish`完成漸層之後。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`FillGradient`方法`CDrawingManager`類別。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&12;](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]  
  
##  <a name="a-namefillgradient2a--cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>CDrawingManager::FillGradient2  
 使用指定的色彩漸層，填滿的矩形區域。  
  
```  
void FillGradient2 (
    CRect rect,  
    COLORREF colorStart,  
    COLORREF colorFinish,  
    int nAngle = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 要填滿的矩形區域。  
  
 [in] `colorStart`  
 漸層的第一個色彩。  
  
 [in] `colorFinish`  
 最後的漸層色彩。  
  
 [in] `nAngle`  
 介於 0 和 360 之間的整數。 此參數指定色彩漸層的方向。  
  
### <a name="remarks"></a>備註  
 使用`nAngle`以指定的色彩漸層方向。 當您指定的色彩漸層的方向時，您也指定的色彩漸層的開始位置。 值為 0，表示`nAngle`表示漸層開始上方的矩形。 做為`nAngle`增加時，起始位置的漸層根據角度以逆時針方向移動。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`FillGradient2`方法`CDrawingManager`類別。 此程式碼片段是一部分[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&37;](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]  
  
##  <a name="a-namegrayrecta--cdrawingmanagergrayrect"></a><a name="grayrect"></a>CDrawingManager::GrayRect  
 使用指定的灰色色彩，填滿的矩形。  
  
```  
BOOL GrayRect(
    CRect rect,  
    int nPercentage = -1,  
    COLORREF clrTransparent = (COLORREF)-1,  
    COLORREF clrDisabled = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 要填滿的矩形區域。  
  
 [in] `nPercentage`  
 灰色矩形中您想要的百分比。  
  
 [in] `clrTransparent`  
 透明的色彩。  
  
 [in] `clrDisabled`  
 如果這個方法會使用取消飽和度的色彩`nPercentage`設定為-1。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 參數`nPercentage`，較低的值表示較深的色彩。  
  
 最大值`nPercentage`為 200。 大於 200 的值不會變更矩形的外觀。 如果值為-1，這個方法會使用`clrDisabled`限制飽和度的矩形。  
  
##  <a name="a-namehighlightrecta--cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>CDrawingManager::HighlightRect  
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
 [in] `rect`  
 若要反白顯示的矩形區域。  
  
 [in] `nPercentage`  
 指出反白顯示的應該是透明程度的百分比。  
  
 [in] `clrTransparent`  
 透明的色彩。  
  
 [in] `nTolerance`  
 介於 0 和 255 之間整數，表示色彩容錯。  
  
 [in] `clrBlend`  
 混用基底的色彩。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果`nPercentage`介於 0 到 99 之間，`HighlightRect`使用的 alpha 混合演算法。 如需 alpha 混色的詳細資訊，請參閱[Alpha 混色線條和填色](http://msdn.microsoft.com/library/5440f48c-3ac9-44c3-b170-c1c110bdbab8)。 如果`nPercentage`為-1，這個方法會使用預設反白顯示的層級。 如果`nPercentage`是 100，這個方法不做任何動作，並傳回`TRUE`。  
  
 此方法會使用參數`nTolerance`來判斷是否要反白顯示的矩形區域。 若要反白顯示在矩形中，您的應用程式的背景色彩之間的差異和`clrTransparent`必須是小於`nTolerance`中每個色彩元件 （紅色、 綠色和藍色）。  
  
##  <a name="a-namehlstorgbonea--cdrawingmanagerhlstorgbone"></a><a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE  
 從 HLS 表示法，將色彩轉換為 RGB 表示。  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>參數  
 [in] `H`  
 介於 0 和 1，表示色彩的色調。  
  
 [in] `L`  
 介於 0 和 1，表示色彩的亮度。  
  
 [in] `S`  
 介於 0 和 1，表示色彩的濃度。  
  
### <a name="return-value"></a>傳回值  
 提供 HLS 色彩的 RGB 呈現。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 這個方法和`CDrawingManager::HLStoRGB_TWO`方法執行相同的作業，但需要不同的值，如`H`參數。 在這種方法，`H`是圓形的百分比。 在`CDrawingManager::HLStoRGB_TWO`方法，`H`是程度，值介於 0 到 360 度，表示這兩個紅色。 比方說，使用`HLStoRGB_ONE`，值為 0.25`H`相當於值為 90 與`HLStoRGB_TWO`。  
  
##  <a name="a-namehlstorgbtwoa--cdrawingmanagerhlstorgbtwo"></a><a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO  
 從 HLS 表示法，將色彩轉換為 RGB 表示。  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>參數  
 [in] `H`  
 表示色彩的色調 0 和 360 之間的數字。  
  
 [in] `L`  
 介於 0 和 1，表示色彩的亮度。  
  
 [in] `S`  
 介於 0 和 1，表示色彩的濃度。  
  
### <a name="return-value"></a>傳回值  
 提供 HLS 色彩的 RGB 呈現。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 這個方法和[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法執行相同的作業，但需要不同的值，如`H`參數。 在這種方法，`H`是程度，值介於 0 到 360 度，表示這兩個紅色。 在[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法，`H`是圓形的百分比。 比方說，使用`HLStoRGB_ONE`，值為 0.25`H`相當於值為 90 與`HLStoRGB_TWO`。  
  
##  <a name="a-namehsvtorgba--cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB  
 從 HSV 表示法，將色彩轉換為 RGB 表示。  
  
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
|[in] `H`|表示色彩的色調 0 和 360 之間的數字。|  
|[in] `S`|介於 0 和 1，表示色彩的濃度。|  
|[in] `V`|介於 0 和 1，表示色彩的值。|  
  
### <a name="return-value"></a>傳回值  
 提供 HSV 色彩的 RGB 呈現。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/linkid=119126)。  
  
##  <a name="a-namehuetorgba--cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawingManager::HuetoRGB  
 將色調值轉換成紅色、 綠色或藍色元件。  
  
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
 [in] `m1`  
 請參閱＜備註＞。  
  
 [in] `m2`  
 請參閱＜備註＞。  
  
 [in] `h`  
 請參閱＜備註＞。  
  
 [in] `rm1`  
 請參閱＜備註＞。  
  
 [in] `rm2`  
 請參閱＜備註＞。  
  
 [in] `rh`  
 請參閱＜備註＞。  
  
### <a name="return-value"></a>傳回值  
 提供的色調個別紅色、 綠色或藍色元件。  
  
### <a name="remarks"></a>備註  
 這個方法是 helper 方法，`CDrawingManager`類別用來計算個別的紅色、 綠色和藍色元件 HSV 或 HSL 的表示法中的色彩。 這個方法不是直接由程式設計人員呼叫。 輸入的參數是取決於轉換演算法的值。  
  
 若要轉換的 RGB 表示 HSV 或 HSL 色彩，呼叫下列方法之一︰  
  
- [CDrawingManager::HSVtoRGB](#hsvtorgb)  
  
- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)  
  
- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)  
  
##  <a name="a-namemirrorrecta--cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>CDrawingManager::MirrorRect  
 翻轉的矩形區域。  
  
```  
void MirrorRect(
    CRect rect,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 若要翻轉的區域，這個周框。  
  
 [in] `bHorz`  
 布林值的參數，指出矩形是否會水平或垂直翻轉。  
  
### <a name="remarks"></a>備註  
 這個方法可以反轉所擁有的裝置任何的內容區域`CDrawingManager`類別。 如果`bHorz`設為`TRUE`，這個方法會水平翻轉的區域。 否則，它在區域垂直翻轉。  
  
##  <a name="a-namepixelalphaa--cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawingManager::PixelAlpha  
 計算半透明的像素的最終色彩。  
  
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
 [in] `srcPixel`  
 初始色彩像素。  
  
 [in] `percent`  
 表示數字 0 到 100 之間的透明度百分比。 值 100 表示初始色彩完全透明。  
  
 [in] `percentR`  
 表示數字 0 到 100 之間的紅色元件的透明度百分比。  
  
 [in] `percentG`  
 表示數字 0 到 100 之間的綠色元件的透明度百分比。  
  
 [in] `percentB`  
 表示數字 0 到 100 之間的藍色元件的透明度百分比。  
  
 [in] `dstPixel`  
 基底像素色彩。  
  
### <a name="return-value"></a>傳回值  
 半透明的像素之完稿色彩。  
  
### <a name="remarks"></a>備註  
 這是一個 helper 類別，以色彩標示半透明的點陣圖，並不是直接由程式設計人員呼叫。  
  
 當您使用的方法具有版本`dstPixel`，最終色彩是組合`dstPixel`和`srcPixel`。 `srcPixel`色彩是部分透明色彩的基準色彩透過`dstPixel`。  
  
##  <a name="a-nameprepareshadowmaska--cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask  
 建立可用來當做陰影的點陣圖。  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>參數  
 [in] `nDepth`  
 高度與寬度的陰影。  
  
 [in] `clrBase`  
 陰影的色彩。  
  
 [in] `iMinBrightness`  
 陰影的最小的亮度。  
  
 [in] `iMaxBrightness`  
 最大陰影的亮度。  
  
### <a name="return-value"></a>傳回值  
 如果成功，這個方法建立的點陣圖控制代碼否則`NULL`。  
  
### <a name="remarks"></a>備註  
 如果`nDepth`是設定為 0，這個方法會結束並傳回`NULL`。 如果`nDepth`小於 3，陰影的高度與寬度會設定為 3 個像素為單位。  
  
##  <a name="a-namergbtohsla--cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL  
 將色彩從紅、 綠和藍 (RGB) 表示法色調、 飽和度和亮度 (HSL) 表示法。  
  
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
|[in] `rgb`|RGB 值中的色彩。|  
|[輸出] `H`|方法儲存的色彩色調的兩倍的指標。|  
|[輸出] `S`|方法儲存的色彩飽和度的兩倍的指標。|  
|[輸出] `L`|方法儲存的色彩亮度的兩倍的指標。|  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 傳回的值`H`表示介於 0 和 1 0 和 1 代表紅色之間的小數。 傳回的值`S`和`L`是介於 0 和 1 之間的數字。  
  
##  <a name="a-namergbtohsva--cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV  
 從 RGB 表示法，將色彩轉換為 HSV 表示。  
  
```  
static void __stdcall RGBtoHSV(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* V);
```  
  
### <a name="parameters"></a>參數  
 [in] `rgb`  
 要轉換的 RGB 表示法的色彩。  
  
 [輸出] `H`  
 Double 值，這個方法會產生的色彩色調的儲存位置指標。  
  
 [輸出] `S`  
 Double 值，這個方法會產生的色彩飽和度的儲存位置指標。  
  
 [輸出] `V`  
 Double 值，這個方法會產生之色彩的值的儲存位置指標。  
  
### <a name="remarks"></a>備註  
 色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需有關色彩不同的表示方式的詳細資訊，請參閱[色彩](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 傳回的值`H`是介於 0 和 360 之間的數字 0 到 360 度表示紅色。 傳回值`S`和`V`是介於 0 和 1 之間的數字。  
  
##  <a name="a-namesetalphapixela--cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel  
 色彩點陣圖中的透明像素。  
  
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
 [in] `pBits`  
 點陣圖的位元值指標。  
  
 [in] `rect`  
 在您的應用程式中的矩形區域。 繪圖 manager 繪製陰影，將此區域的右側。  
  
 [in] `x`  
 色彩的像素水平座標。  
  
 [in] `y`  
 像素色彩的垂直座標。  
  
 [in] `percent`  
 透明度百分比。  
  
 [in] `iShadowSize`  
 高度與寬度的陰影。  
  
 [in] `clrBase`  
 陰影的色彩。  
  
 [in] `bIsRight`  
 表示色彩的像素的布林參數。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="remarks"></a>備註  
 這個方法是 helper 方法，可由[CDrawingManager::DrawShadow](#drawshadow)方法。 我們建議，如果您想要繪製陰影，呼叫`CDrawingManager::DrawShadow`改。  
  
 如果`bIsRight`設為`TRUE`，色彩的像素為單位`x`像素的右邊緣的`rect`。 如果是`FALSE`，色彩的像素為單位`x`從左邊的像素`rect`。  
  
##  <a name="a-namesetpixela--cdrawingmanagersetpixel"></a><a name="setpixel"></a>CDrawingManager::SetPixel  
 變更指定的色彩點陣圖中的單一像素。  
  
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
|[in] `pBits`|點陣圖的位元值指標。|  
|[in] `cx`|點陣圖的總寬度。|  
|[in] `cy`|點陣圖的高度總計。|  
|[in] `x`|若要變更點陣圖中像素 x 軸座標。|  
|[in] `y`|若要變更點陣圖中像素的 y 座標。|  
|[in] `color`|新提供的座標所識別的像素色彩。|  
  
##  <a name="a-namesmartmixcolorsa--cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>CDrawingManager::SmartMixColors  
 結合兩個色彩來根據加權的比率。  
  
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
|[in] `color1`|第一個色彩混合。|  
|[in] `color2`|第二個色彩混合。|  
|[in] `dblLumRatio`|新的色彩亮度的比率。 `SmartMixColors`然後再判斷完稿色彩乘以這個比例混合色彩的亮度。|  
|[in] `k1`|第一個色彩加權的比例。|  
|[in] `k2`|第二個色彩加權的比率。|  
  
### <a name="return-value"></a>傳回值  
 表示加權的混合提供色彩的色彩。  
  
### <a name="remarks"></a>備註  
 這個方法會失敗並發生錯誤，如果`k1`或`k2`小於零。 如果這兩個參數會設為 0，則方法會傳回`RGB(0, 0, 0)`。  
  
 使用下列公式會計算加權的比率: (color1 * k1 + 色&2; \* k2) /(k1 + k2)。 判定加權的比例之後，方法會計算混合色彩的亮度。 然後將相乘的明暗度`dblLumRatio`。 如果值大於 1.0，方法會設定混合的色彩亮度的新值。 否則，亮度會設為 1.0。  
  
##  <a name="a-namedrawrotateda--cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>CDrawingManager::DrawRotated  
 旋轉 90 度的來源 DC 內指定的矩形的內容。  
  
```  
void DrawRotated(
    CRect rectDest,  
    CDC& dcSrc,  
    BOOL bClockWise);
```  
  
### <a name="parameters"></a>參數  
 `rectDest`  
 目的矩形。  
  
 `dcSrc`  
 來源裝置內容。  
  
 `bClockWise`  
 `TRUE`表示旋轉 +&90; 度。`FALSE`表示旋轉-90 度。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

