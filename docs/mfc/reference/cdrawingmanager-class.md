---
title: CDrawingManager 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 69365b66b12d5a9284c9b097b225ba041e07b6b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506800"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager 類別

`CDrawingManager`類別會執行複雜的繪圖演算法。

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
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|建立應用程式可以直接寫入32位與裝置無關的點陣圖 (DIB)。|
|[CDrawingManager::DrawAlpha](#drawalpha)|顯示具有透明或半透明圖元的點陣圖。|
|[CDrawingManager::DrawRotated](#drawrotated)|以 +/-90 度旋轉給定矩形內的來源 DC 內容|
|[CDrawingManager::DrawEllipse](#drawellipse)|以提供的填滿和框線色彩繪製橢圓形。|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|繪製環形, 並以色彩漸層填滿。|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|繪製線條。|
|[CDrawingManager::DrawRect](#drawrect)|以提供的填滿和框線色彩繪製矩形。|
|[CDrawingManager::DrawShadow](#drawshadow)|繪製矩形區域的陰影。|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|以兩個色彩漸層填滿矩形區域。|
|[CDrawingManager::FillGradient](#fillgradient)|使用指定的色彩漸層填滿矩形區域。|
|[CDrawingManager::FillGradient2](#fillgradient2)|使用指定的色彩漸層填滿矩形區域。 也會指定漸層色彩變更的方向。|
|[CDrawingManager::GrayRect](#grayrect)|以指定的灰色色彩填滿矩形。|
|[CDrawingManager::HighlightRect](#highlightrect)|反白顯示矩形區域。|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|將色彩從 HLS 表示轉換成 RGB 標記法。|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|將色彩從 HLS 表示轉換成 RGB 標記法。|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|將色彩從 HSV 表示轉換成 RGB 標記法。|
|[CDrawingManager::HuetoRGB](#huetorgb)|將色調值轉換成紅色、綠色或藍色元件的 Helper 方法。|
|[CDrawingManager::MirrorRect](#mirrorrect)|翻轉矩形區域。|
|[CDrawingManager::PixelAlpha](#pixelalpha)|判斷半透明圖元之最終色彩的 Helper 方法。|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|建立可當做陰影使用的點陣圖。|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|將色彩從 RGB 標記法轉換為 HSL 標記法。|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|將色彩從 RGB 標記法轉換為 HSV 標記法。|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|協助程式方法, 可將點陣圖中的部分透明圖元色彩。|
|[CDrawingManager::SetPixel](#setpixel)|Helper 方法, 可將點陣圖中的單一圖元變更為指定的色彩。|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|根據加權比例結合兩個色彩。|

## <a name="remarks"></a>備註

`CDrawingManager`類別提供繪製陰影、色彩漸層和反白顯示矩形的功能。 它也會執行 Alpha 混色。 您可以使用這個類別來直接變更應用程式的 UI。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>需求

**標頭:** afxdrawmanager。h

##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

結構[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)物件。

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>參數

*dc*<br/>
在裝置內容的參考。 會`CDrawingManager`使用此內容進行繪製。

##  <a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

建立應用程式可以直接寫入32位與裝置無關的點陣圖 (DIB)。

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
|*size*|在表示點陣圖大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)參數。|
|*pBits*|脫銷資料指標的指標, 可接收 DIB 位值的位置。|
|*bitmap*|原始點陣圖的控制碼|
|*clrTransparent*|RGB 值, 指定原始點陣圖的透明色彩。|

### <a name="return-value"></a>傳回值

如果此方法成功, 則為新建立之 DIB 點陣圖的控制碼;否則為 Null。

### <a name="remarks"></a>備註

如需如何建立 DIB 點陣圖的詳細資訊, 請參閱[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap)。

##  <a name="drawalpha"></a>CDrawingManager::D rawAlpha

顯示具有透明或半透明圖元的點陣圖。

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>參數

*pDstDC*<br/>
在目的地之裝置內容的指標。

*rectDst*<br/>
在目的地矩形。

*pSrcDC*<br/>
在來源之裝置內容的指標。

*rectSrc*<br/>
在來源矩形。

### <a name="remarks"></a>備註

這個方法會針對兩個位圖執行 Alpha 混合。 如需 Alpha 混合的詳細資訊, 請參閱 Windows SDK 中的[AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) 。

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

以提供的填滿和框線色彩繪製橢圓形。

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*rect*<br/>
在橢圓形的周框。

*clrFill*<br/>
在這個方法用來填滿橢圓形的色彩。

*clrLine*<br/>
在這個方法用來做為橢圓形框線的色彩。

### <a name="remarks"></a>備註

如果其中一種色彩設為-1, 這個方法就會傳回而不繪製橢圓形。 如果周框的任一個維度為 0, 它也會傳回而不繪製橢圓形。

##  <a name="drawgradientring"></a>CDrawingManager::D rawGradientRing

繪製環形, 並以色彩漸層填滿。

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

*rect*<br/>
在[CRect](../../atl-mfc-shared/reference/crect-class.md)參數, 指定漸層環形的界限。

*colorStart*<br/>
在漸層的第一個色彩。

*colorFinish*<br/>
在漸層的最後一個色彩。

*colorBorder*<br/>
在框線的色彩。

*nAngle*<br/>
在指定初始漸層繪製角度的參數。 此值應介於0到360之間。

*nWidth*<br/>
在環形框線的寬度。

*clrFace*<br/>
在環形內部的色彩。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*Rect*所定義的矩形必須至少為5圖元寬, 5 圖元高。

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

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
|*x1*|在行開始的 x 座標。|
|*y1*|在行開始的 y 座標。|
|*x2*|在行結束的 x 座標。|
|*y2*|在行結束的 y 座標。|
|*clrLine*|在線條的色彩。|

### <a name="remarks"></a>備註

如果*clrLine*等於-1, 這個方法就會失敗。

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

以提供的填滿和框線色彩繪製矩形。

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*rect*<br/>
在矩形的界限。

*clrFill*<br/>
在這個方法用來填滿矩形的色彩。

*clrLine*<br/>
在這個方法用於矩形框線的色彩。

### <a name="remarks"></a>備註

如果其中一種色彩設為-1, 這個方法就會傳回而不繪製矩形。 如果矩形的任一個維度為 0, 它也會傳回。

##  <a name="drawshadow"></a>CDrawingManager::D rawShadow

繪製矩形區域的陰影。

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

*rect*<br/>
在應用程式中的矩形區域。 繪圖管理員會在此區域下方繪製陰影。

*nDepth*<br/>
在陰影的寬度和高度。

*iMinBrightness*<br/>
在陰影的最小亮度。

*iMaxBrightness*<br/>
在陰影的最大亮度。

*pBmpSaveBottom*<br/>
在點陣圖的指標, 其中包含陰影下半部的影像。

*pBmpSaveRight*<br/>
在點陣圖的指標, 其中包含在矩形右側繪製之陰影的影像。

*clrBase*<br/>
在陰影的色彩。

*bRightShadow*<br/>
在布林值參數, 指出陰影的繪製方式。 如果*bRightShadow*為`TRUE`, `DrawShadow`則會在矩形的右側繪製陰影。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用*pBmpSaveBottom*和*pBmpSaveRight*參數, 為下和右陰影提供兩個有效的點陣圖。 如果這些[CBitmap](../../mfc/reference/cbitmap-class.md)物件具有附加的 GDI 物件, `DrawShadow`將會使用這些點陣圖作為陰影。 如果參數沒有附加的 GDI 物件, `DrawShadow`則繪製陰影, 並將點陣圖附加至參數。 `CBitmap` 在未來的呼叫`DrawShadow`中, 您可以提供這些點陣圖來加速繪製進程。 如需`CBitmap`類別和 GDI 物件的詳細資訊, 請參閱[繪圖物件](../../mfc/graphic-objects.md)。

如果其中一個參數是`NULL`, `DrawShadow`則會自動繪製陰影。

如果您將 [ *bRightShadow* ] 設定為 [FALSE], 陰影將會繪製在矩形區域的下方和左側。

### <a name="example"></a>範例

下列範例示範如何使用`DrawShadow` `CDrawingManager`類別的方法。 此程式碼片段是「元件[表示范」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

以兩個色彩漸層填滿矩形區域。

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

*rect*<br/>
在要填滿的矩形。

*colorStart1*<br/>
在第一個色彩漸層的初始色彩。

*colorFinish1*<br/>
在第一個色彩漸層的最終色彩。

*colorStart2*<br/>
在第二個色彩漸層的初始色彩。

*colorFinish2*<br/>
在第二個色彩漸層的最終色彩。

*bHorz*<br/>
在布林值參數, 指出是否`Fill4ColorsGradient`將色彩水準或垂直漸層。 TRUE 表示水準漸層。

*nPercentage*<br/>
在0-100 的整數。 此值表示要填滿第一個色彩漸層的矩形百分比。

### <a name="remarks"></a>備註

當矩形填滿兩個色彩漸層時, 視*bHorz*的值而定, 兩者都位於彼此上方或彼此相鄰。 每個色彩漸層都會與[CDrawingManager:: FillGradient](#fillgradient)方法分開計算。

如果*nPercentage*小於0或大於 100, 則這個方法會產生判斷提示失敗。

##  <a name="fillgradient"></a>CDrawingManager::FillGradient

使用指定的色彩漸層填滿矩形區域。

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

*rect*<br/>
在要填滿的矩形區域。

*colorStart*<br/>
在漸層的第一個色彩。

*colorFinish*<br/>
在漸層的最終色彩。

*bHorz*<br/>
在布林值參數, 指定是否`FillGradient`應該繪製水準或垂直漸層。

*nStartFlatPercentage*<br/>
在在啟動漸層之前, `FillGradient`填滿*colorStart*的矩形百分比。

*nEndFlatPercentage*<br/>
在完成漸層之後, `FillGradient`填滿*colorFinish*的矩形百分比。

### <a name="example"></a>範例

下列範例示範如何使用`FillGradient` `CDrawingManager`類別的方法。 此程式碼片段是[MS Office 2007 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>CDrawingManager::FillGradient2

使用指定的色彩漸層填滿矩形區域。

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>參數

*rect*<br/>
在要填滿的矩形區域。

*colorStart*<br/>
在漸層的第一個色彩。

*colorFinish*<br/>
在漸層的最後一種色彩。

*nAngle*<br/>
在介於0到360之間的整數。 這個參數會指定色彩漸層的方向。

### <a name="remarks"></a>備註

使用 [ *nAngle* ] 來指定色彩漸層的方向。 當您指定色彩漸層的方向時, 您也可以指定色彩漸層的開始位置。 *NAngle*的值為 0, 表示漸層從矩形頂端開始。 當*nAngle*增加時, 漸層的開始位置會根據角度以逆時針方向移動。

### <a name="example"></a>範例

下列範例示範如何使用`FillGradient2` `CDrawingManager`類別的方法。 此程式碼片段是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>CDrawingManager::GrayRect

以指定的灰色色彩填滿矩形。

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>參數

*rect*<br/>
在要填滿的矩形區域。

*nPercentage*<br/>
在矩形中您想要的灰色百分比。

*clrTransparent*<br/>
在透明色彩。

*clrDisabled*<br/>
在當*nPercentage*設定為-1 時, 此方法用於取消飽和度的色彩。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

對於參數*nPercentage*, 較低的值表示較暗的色彩。

*NPercentage*的最大值為200。 大於200的值不會變更矩形的外觀。 如果值為-1, 則這個方法會使用*clrDisabled*來限制矩形的飽和度。

##  <a name="highlightrect"></a>CDrawingManager::HighlightRect

反白顯示矩形區域。

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>參數

*rect*<br/>
在要反白顯示的矩形區域。

*nPercentage*<br/>
在表示反白顯示應如何透明化的百分比。

*clrTransparent*<br/>
在透明色彩。

*nTolerance*<br/>
在介於0和255之間的整數, 表示色彩承受度。

*clrBlend*<br/>
在要進行混合的基底色彩。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果*nPercentage*介於0到99之間, `HighlightRect`會使用 Alpha 混合演算法。 如需 Alpha 混色的詳細資訊, 請參閱[Alpha 混合線條和填滿](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果*nPercentage*為-1, 則這個方法會使用預設的反白顯示層級。 如果*nPercentage*為 100, 則這個方法不會執行任何操作, 而且會傳回 TRUE。

方法會使用參數*nTolerance*來決定是否要反白顯示矩形區域。 若要反白顯示矩形, 應用程式和*clrTransparent*的背景色彩之間的差異必須小於每個色彩元件中的*nTolerance* (紅色、綠色和藍色)。

##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

將色彩從 HLS 表示轉換成 RGB 標記法。

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>參數

*H*<br/>
在介於0和1之間的數位, 表示色彩的色調。

*L*<br/>
在介於0和1之間的數位, 表示色彩的亮度。

*S*<br/>
在介於0和1之間的數位, 表示色彩的飽和度。

### <a name="return-value"></a>傳回值

所提供之 HLS 色彩的 RGB 標記法。

### <a name="remarks"></a>備註

色彩可以表示為 HSV (色調、飽和度和值)、HSL (色調、飽和度和亮度) 或 RGB (紅色、綠色和藍色)。 如需不同色彩表示的詳細資訊, 請參閱[color](/windows/win32/uxguide/vis-color)。

這個方法和`CDrawingManager::HLStoRGB_TWO`方法會執行相同的作業, 但不需要*H*參數的不同值。 在此方法中, *H*是圓形的百分比。 在方法中, H 是介於0和360之間的度數值, 兩者都代表紅色。 `CDrawingManager::HLStoRGB_TWO` 例如, 使用`HLStoRGB_ONE`, *H*的值為 0.25, 相當於的`HLStoRGB_TWO`值90。

##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

將色彩從 HLS 表示轉換成 RGB 標記法。

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>參數

*H*<br/>
在介於0和360之間的數位, 表示色彩的色調。

*L*<br/>
在介於0和1之間的數位, 表示色彩的亮度。

*S*<br/>
在介於0和1之間的數位, 表示色彩的飽和度。

### <a name="return-value"></a>傳回值

所提供之 HLS 色彩的 RGB 標記法。

### <a name="remarks"></a>備註

色彩可以表示為 HSV (色調、飽和度和值)、HSL (色調、飽和度和亮度) 或 RGB (紅色、綠色和藍色)。 如需不同色彩表示的詳細資訊, 請參閱[color](/windows/win32/uxguide/vis-color)。

這個方法和[CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one)方法會執行相同的作業, 但不需要*H*參數的不同值。 在此方法中, *H*是介於0和360之間的度數值, 兩者都代表紅色。 在[CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one)方法中, *H*是圓形的百分比。 例如, 使用`HLStoRGB_ONE`, *H*的值為 0.25, 相當於的`HLStoRGB_TWO`值90。

##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

將色彩從 HSV 表示轉換成 RGB 標記法。

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
|*H*|在介於0和360之間的數位, 表示色彩的色調。|
|*S*|在介於0和1之間的數位, 表示色彩的飽和度。|
|*V*|在介於0和1之間的數位, 表示色彩的值。|

### <a name="return-value"></a>傳回值

所提供之 HSV 色彩的 RGB 標記法。

### <a name="remarks"></a>備註

色彩可以表示為 HSV (色調、飽和度和值)、HSL (色調、飽和度和亮度) 或 RGB (紅色、綠色和藍色)。 如需不同色彩表示的詳細資訊, 請參閱[color](/windows/win32/uxguide/vis-color)。

##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB

將色調值轉換成紅色、綠色或藍色的元件。

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

*m1*<br/>
在請參閱備註。

*m2*<br/>
在請參閱備註。

*h*<br/>
在請參閱備註。

*rm1*<br/>
在請參閱備註。

*rm2*<br/>
在請參閱備註。

*rh*<br/>
在請參閱備註。

### <a name="return-value"></a>傳回值

所提供之色調的個別紅色、綠色或藍色元件。

### <a name="remarks"></a>備註

這個方法是一個 helper 方法, `CDrawingManager`類別會使用它來計算 HSV 或 HSL 標記法中色彩的個別紅色、綠色和藍色元件。 這個方法並非設計成由程式設計師直接呼叫。 輸入參數是相依于轉換演算法的值。

若要將 HSV 或 HSL 色彩轉換成 RGB 標記法, 請呼叫下列其中一個方法:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>CDrawingManager::MirrorRect

翻轉矩形區域。

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>參數

*rect*<br/>
在要翻轉之區域的周框。

*bHorz*<br/>
在布林值參數, 指出矩形是水準或垂直翻轉。

### <a name="remarks"></a>備註

這個方法可以翻轉`CDrawingManager`類別所擁有之裝置內容的任何區域。 如果*bHorz*設定為 TRUE, 這個方法會水準翻轉區域。 否則, 它會垂直翻轉區域。

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

計算半透明圖元的最終色彩。

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

*srcPixel*<br/>
在圖元的初始色彩。

*percent*<br/>
在介於0和100之間的數位, 表示透明度的百分比。 值為100表示初始色彩是完全透明的。

*percentR*<br/>
在介於0和100之間的數位, 表示紅色元件的透明度百分比。

*percentG*<br/>
在介於0和100之間的數位, 代表綠色元件的透明度百分比。

*percentB*<br/>
在介於0和100之間的數位, 表示藍色元件的透明度百分比。

*dstPixel*<br/>
在圖元的基底色彩。

### <a name="return-value"></a>傳回值

半透明圖元的最終色彩。

### <a name="remarks"></a>備註

這是用來為半透明點陣圖著色的協助程式類別, 而且不是直接由程式設計人員呼叫。

當您使用具有*dstPixel*的方法版本時, 最後的色彩會是*dstPixel*和*srcPixel*的組合。 *SrcPixel*色彩是*dstPixel*基底色彩上的部分透明色彩。

##  <a name="prepareshadowmask"></a>CDrawingManager::P repareShadowMask

建立可當做陰影使用的點陣圖。

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>參數

*nDepth*<br/>
在陰影的寬度和高度。

*clrBase*<br/>
在陰影的色彩。

*iMinBrightness*<br/>
在陰影的最小亮度。

*iMaxBrightness*<br/>
在陰影的最大亮度。

### <a name="return-value"></a>傳回值

如果此方法成功, 則為所建立之點陣圖的控制碼;否則為 Null。

### <a name="remarks"></a>備註

如果*nDepth*設定為 0, 這個方法會結束並傳回 Null。 如果*nDepth*小於 3, 陰影的寬度和高度會設定為3圖元。

##  <a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

將色彩從紅色、綠色和藍色 (RGB) 標記法轉換成色調、飽和度和亮度 (HSL) 標記法。

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
|*rgb*|在RGB 值中的色彩。|
|*H*|脫銷雙精度浮點數的指標, 其中方法會儲存色彩的色調。|
|*S*|脫銷雙精度浮點數的指標, 其中方法會儲存色彩的飽和度。|
|*L*|脫銷雙精度浮點數的指標, 其中方法會儲存色彩的亮度。|

### <a name="remarks"></a>備註

色彩可以表示為 HSV (色調、飽和度和值)、HSL (色調、飽和度和亮度) 或 RGB (紅色、綠色和藍色)。 如需不同色彩表示的詳細資訊, 請參閱[color](/windows/win32/uxguide/vis-color)。

*H*的傳回值會表示為0和1之間的分數, 其中0和1代表紅色。 *S*和*L*的傳回值是介於0和1之間的數位。

##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

將色彩從 RGB 標記法轉換為 HSV 標記法。

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>參數

*rgb*<br/>
在要以 RGB 標記法轉換的色彩。

*H*<br/>
脫銷雙精度浮點數的指標, 這個方法會儲存色彩的結果色調。

*S*<br/>
脫銷雙精度浮點數的指標, 這個方法會儲存色彩的產生飽和度。

*V*<br/>
脫銷雙精度浮點數的指標, 這個方法會儲存色彩的結果值。

### <a name="remarks"></a>備註

色彩可以表示為 HSV (色調、飽和度和值)、HSL (色調、飽和度和亮度) 或 RGB (紅色、綠色和藍色)。 如需不同色彩表示的詳細資訊, 請參閱[color](/windows/win32/uxguide/vis-color)。

*H*的傳回值是介於0和360之間的數位, 其中0和360都表示紅色。 *S*和*V*的傳回值是介於0和1之間的數位。

##  <a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

在點陣圖中將透明圖元色彩。

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

*pBits*<br/>
在點陣圖之位值的指標。

*rect*<br/>
在應用程式中的矩形區域。 [繪圖管理員] 會在此區域的下方和右邊繪製一個陰影。

*x*<br/>
在要色彩之圖元的水準座標。

*y*<br/>
在要色彩之圖元的垂直座標。

*percent*<br/>
在透明度的百分比。

*iShadowSize*<br/>
在陰影的寬度和高度。

*clrBase*<br/>
在陰影的色彩。

*bIsRight*<br/>
在布林值參數, 指出要著色的圖元。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

這個方法是[CDrawingManager::D rawshadow](#drawshadow)方法所使用的 helper 方法。 如果您想要繪製陰影, 建議您改為呼叫`CDrawingManager::DrawShadow` 。

如果*bIsRight*設定為 TRUE, 則要色彩的圖元會從*矩形*右邊緣測量*x*圖元。 如果為 FALSE, 則色彩的圖元會從*矩形*左邊緣測量*x*圖元。

##  <a name="setpixel"></a>CDrawingManager:: Bitmap.setpixel

將點陣圖中的單一圖元變更為指定的色彩。

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
|*pBits*|在點陣圖位值的指標。|
|*cx*|在點陣圖的總寬度。|
|*cy*|在點陣圖的總高度。|
|*x*|在要變更之點陣圖中圖元的 x 座標。|
|*y*|在要變更之點陣圖中圖元的 y 座標。|
|*color*|在所提供座標所識別圖元的新色彩。|

##  <a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

根據加權比例結合兩個色彩。

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
|參數|說明|
|*color1*|在要混合的第一個色彩。|
|*color2*|在要混合的第二個色彩。|
|*dblLumRatio*|在新色彩亮度的比例。 `SmartMixColors`在決定最終色彩之前, 將混合色彩的亮度乘以此比例。|
|*k1*|在第一個色彩的加權比例。|
|*k2*|在第二個色彩的加權比例。|

### <a name="return-value"></a>傳回值

表示所提供色彩之加權混合的色彩。

### <a name="remarks"></a>備註

如果*版 k1*或*k2*小於零, 這個方法就會失敗並產生錯誤。 如果這兩個參數都設定為 0, 則方法`RGB(0, 0, 0)`會傳回。

加權比例的計算公式如下: (color1 \*版 k1 + color2 \* k2)/(版 k1 + k2)。 判斷加權比例之後, 方法會計算混合色彩的亮度。 然後, 它會將亮度乘以*dblLumRatio*。 如果值大於 1.0, 則方法會將混合色彩的亮度設定為新的值。 否則, 亮度會設定為1.0。

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

將指定矩形內的來源 DC 內容旋轉90度。

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>參數

*rectDest*<br/>
目的地矩形。

*dcSrc*<br/>
來源裝置內容。

*bClockWise*<br/>
TRUE 表示旋轉 + 90 度;FALSE 表示旋轉-90 度。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
