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
ms.openlocfilehash: f14b21c97e5a36d5107e7db526e4153446ae2a01
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278526"
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
|[CDrawingManager::DrawRotated](#drawrotated)|旋轉的來源 DC + /-90 度，將所指定之矩形內部的內容|
|[CDrawingManager::DrawEllipse](#drawellipse)|繪製橢圓形使用提供的填滿和框線色彩。|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|繪製通道和其填滿漸層色彩。|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|繪製一條線。|
|[CDrawingManager::DrawRect](#drawrect)|繪製矩形與所提供的填滿和框線色彩。|
|[CDrawingManager::DrawShadow](#drawshadow)|繪製一個陰影的矩形區域。|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|會使用兩個色彩漸層，填滿的矩形區域。|
|[CDrawingManager::FillGradient](#fillgradient)|使用指定的色彩漸層，填滿的矩形區域。|
|[CDrawingManager::FillGradient2](#fillgradient2)|使用指定的色彩漸層，填滿的矩形區域。 此外，也會指定漸層的色彩變更的方向。|
|[CDrawingManager::GrayRect](#grayrect)|使用指定的灰色色彩，填滿的矩形。|
|[CDrawingManager::HighlightRect](#highlightrect)|反白顯示的矩形區域。|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|將色彩從 HLS 表示法轉換為 RGB 表示。|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|將色彩從 HLS 表示法轉換為 RGB 表示。|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|將色彩從 HSV 表示法轉換為 RGB 表示。|
|[CDrawingManager::HuetoRGB](#huetorgb)|Helper 方法，將 hue 值轉換成紅色、 綠色或藍色元件。|
|[CDrawingManager::MirrorRect](#mirrorrect)|翻轉的矩形區域。|
|[CDrawingManager::PixelAlpha](#pixelalpha)|決定半透明的像素的完稿色彩的 helper 方法。|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|建立可用作陰影的點陣圖。|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|將色彩從 RGB 表示法轉換為的 HSL 表示。|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|將色彩 RGB 表示轉換成 HSV 表示。|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|色彩點陣圖中的部分透明像素的 helper 方法。|
|[CDrawingManager::SetPixel](#setpixel)|變更指定的色彩點陣圖中的單一像素的 helper 方法。|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|結合的加權比例為基礎的兩個色彩。|

## <a name="remarks"></a>備註

`CDrawingManager`類別會提供函數來繪製陰影的色彩漸層，反白顯示的矩形。 它也會執行 alpha 透明混色。 若要直接變更應用程式的 UI，您可以使用這個類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>需求

**標頭：** afxdrawmanager.h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

建構[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)物件。

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>參數

*dc*<br/>
[in]裝置內容的參考。 `CDrawingManager`會使用此內容為繪圖。

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
|*size*|[in]A [CSize](../../atl-mfc-shared/reference/csize-class.md)參數，表示點陣圖的大小。|
|*pBits*|[out]指向資料指標所收到的 DIB 位置的位元值。|
|*bitmap*|原始點陣圖控制代碼|
|*clrTransparent*|指定的原始點陣圖的透明色彩的 RGB 值。|

### <a name="return-value"></a>傳回值

如果這個方法成功，新建立 DIB 點陣圖控制代碼否則為 NULL。

### <a name="remarks"></a>備註

如需如何建立 DIB 點陣圖的詳細資訊，請參閱[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibitmap)。

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

*pDstDC*<br/>
[in]目的地裝置內容指標。

*rectDst*<br/>
[in]目的矩形。

*pSrcDC*<br/>
[in]來源裝置內容指標。

*rectSrc*<br/>
[in]來源矩形。

### <a name="remarks"></a>備註

這個方法執行兩個點陣圖 alpha 透明混色。 如需 alpha 透明混色的詳細資訊，請參閱[alphablend，還有旁邊](/windows/desktop/api/wingdi/nf-wingdi-alphablend)Windows SDK 中。

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

繪製橢圓形使用提供的填滿和框線色彩。

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*rect*<br/>
[in]橢圓形的週框。

*clrFill*<br/>
[in]這個方法會使用以填滿橢圓形的色彩。

*clrLine*<br/>
[in]這個方法會使用為橢圓形的框線色彩。

### <a name="remarks"></a>備註

這個方法會傳回不繪製橢圓形，如果其中一個色彩設定為-1。 它也會傳回不繪製橢圓形，如果指定的週框的任一個維度是 0。

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

繪製通道和其填滿漸層色彩。

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
[in]A [CRect](../../atl-mfc-shared/reference/crect-class.md)參數，指定漸層停駐的信號的界限。

*colorStart*<br/>
[in]漸層的第一個色彩。

*colorFinish*<br/>
[in]最後的色彩漸層。

*colorBorder*<br/>
[in]框線的色彩。

*nAngle*<br/>
[in]參數來指定初始的漸層繪製角度。 這個值應該是介於 0 和 360 之間。

*nWidth*<br/>
[in]響鈴框線的寬度。

*clrFace*<br/>
[in]環形的內部的色彩。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

所定義的矩形*rect*必須至少 5 個像素寬和 5 個像素高。

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

繪製一條線。

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
|*x1*|[in]行開頭位置的 x 座標。|
|*y1*|[in]行開頭位置的 y 座標。|
|*x2*|[in]線條的結束位置的 x 座標。|
|*y2*|[in]線條的結束位置的 y 座標。|
|*clrLine*|[in]線條色彩。|

### <a name="remarks"></a>備註

如果這個方法會失敗*clrLine*等於-1。

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

繪製矩形與所提供的填滿和框線色彩。

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*rect*<br/>
[in]矩形界限。

*clrFill*<br/>
[in]這個方法會使用以填滿矩形的色彩。

*clrLine*<br/>
[in]這個方法會使用矩形的框線色彩。

### <a name="remarks"></a>備註

這個方法傳回時不繪製矩形，如果其中一個色彩設定為-1。 它也會傳回如果任一個矩形的維度是 0。

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

*rect*<br/>
[in]您的應用程式中的矩形區域。 繪製管理員將此區域下方繪製一個陰影。

*nDepth*<br/>
[in]寬度和高度的陰影。

*iMinBrightness*<br/>
[in]陰影的最小的亮度。

*iMaxBrightness*<br/>
[in]陰影的最大的亮度。

*pBmpSaveBottom*<br/>
[in]指標，包含影像的下半部陰影的點陣圖。

*pBmpSaveRight*<br/>
[in]指標，包含該映像，矩形右側繪製陰影的點陣圖。

*clrBase*<br/>
[in]陰影色彩。

*bRightShadow*<br/>
[in]布林值參數，指出如何繪製陰影。 如果*bRightShadow*是`TRUE`，`DrawShadow`矩形右側上繪製一個陰影。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您也可以使用參數的下框線和右 shadows 提供兩個有效的點陣圖*pBmpSaveBottom*並*pBmpSaveRight*。 如果有這些[CBitmap](../../mfc/reference/cbitmap-class.md)物件具有附加的 GDI 物件，`DrawShadow`將用作陰影的點陣圖。 如果`CBitmap`參數沒有附加的 GDI 物件，`DrawShadow`繪製陰影，並將點陣圖附加的參數。 在未來呼叫`DrawShadow`，您可以提供這些點陣圖，以加快繪製程序。 如需詳細資訊`CBitmap`類別和 GDI 物件，請參閱 <<c2> [ 圖形物件](../../mfc/graphic-objects.md)。

如果其中一個參數是`NULL`，`DrawShadow`將自動繪製陰影。

如果您設定*bRightShadow*設為 FALSE，陰影繪製下方和左側的矩形區域。

### <a name="example"></a>範例

下列範例示範如何使用`DrawShadow`方法的`CDrawingManager`類別。 此程式碼片段是一部分[Prop 表示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

會使用兩個色彩漸層，填滿的矩形區域。

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
[in]要填滿的矩形。

*colorStart1*<br/>
[in]第一個的色彩漸層的初始色彩。

*colorFinish1*<br/>
[in]第一個色彩漸層的完稿色彩。

*colorStart2*<br/>
[in]第二個的色彩漸層的初始色彩。

*colorFinish2*<br/>
[in]第二個色彩漸層的完稿色彩。

*bHorz*<br/>
[in]布林值，指出參數是否`Fill4ColorsGradient`水平或垂直的漸層的色彩。 TRUE 表示水平漸層。

*nPercentage*<br/>
[in]從 0 到 100 的整數。 這個值表示要使用的第一個色彩漸層填滿的矩形的百分比。

### <a name="remarks"></a>備註

當兩個色彩漸層填滿矩形時，它們會位於彼此的上方或下一步，值而定*bHorz*。 每個色彩漸層的計算，使用方法的方式單獨[CDrawingManager::FillGradient](#fillgradient)。

如果這個方法會產生判斷提示失敗*nPercentage*小於 0 或大於 100。

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

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

*rect*<br/>
[in]要填滿的矩形區域。

*colorStart*<br/>
[in]漸層的第一個色彩。

*colorFinish*<br/>
[in]完稿色彩的漸層。

*bHorz*<br/>
[in]布林值參數，指定是否`FillGradient`應該繪製在水平或垂直漸層。

*nStartFlatPercentage*<br/>
[in]矩形的百分比，`FillGradient`填入*colorStart*開始之漸層之前。

*nEndFlatPercentage*<br/>
[in]矩形的百分比，`FillGradient`填入*colorFinish*完成之漸層之後。

### <a name="example"></a>範例

下列範例示範如何使用`FillGradient`方法的`CDrawingManager`類別。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

使用指定的色彩漸層，填滿的矩形區域。

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>參數

*rect*<br/>
[in]要填滿的矩形區域。

*colorStart*<br/>
[in]漸層的第一個色彩。

*colorFinish*<br/>
[in]最後的色彩漸層。

*nAngle*<br/>
[in]整數，介於 0 和 360 之間。 此參數指定之色彩漸層的方向。

### <a name="remarks"></a>備註

使用*nAngle*以指定之色彩漸層的方向。 當您指定之色彩漸層的方向時，您也指定之色彩漸層的開始位置。 值為 0，表示*nAngle*表示從矩形頂端的漸層開始。 作為*nAngle*增加時，起始位置的漸層中根據角度以逆時鐘方向的移動。

### <a name="example"></a>範例

下列範例示範如何使用`FillGradient2`方法的`CDrawingManager`類別。 此程式碼片段是一部分[新的控制項範例](../../visual-cpp-samples.md)。

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

*rect*<br/>
[in]要填滿的矩形區域。

*nPercentage*<br/>
[in]您想要在矩形的灰色的百分比。

*clrTransparent*<br/>
[in]透明的色彩。

*clrDisabled*<br/>
[in]如果這個方法會使用取消的飽和度的色彩*nPercentage*設定為-1。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

參數*nPercentage*，較低的值表示較深的色彩。

最大值*nPercentage*為 200。 大於 200 的值不會變更矩形的外觀。 如果值為-1，這個方法會使用*clrDisabled*限制矩形的飽和度。

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

*rect*<br/>
[in]若要反白顯示的矩形區域。

*nPercentage*<br/>
[in]百分比來指出應該是透明的反白顯示。

*clrTransparent*<br/>
[in]透明的色彩。

*nTolerance*<br/>
[in]表示的整數 0 和 255 之間的色彩容錯。

*clrBlend*<br/>
[in]混用基底的色彩。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

如果*nPercentage*是介於 0 到 99，`HighlightRect`使用 alpha 透明混色演算法。 如需 alpha 透明混色的詳細資訊，請參閱[Alpha 混色線條和填色](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果*nPercentage*為-1，這個方法會使用預設的反白顯示的層級。 如果*nPercentage*是 100，這個方法不做任何動作，並傳回 TRUE。

此方法會使用參數*nTolerance*來判斷是否要反白顯示的矩形區域。 反白顯示在矩形中，您的應用程式的背景色彩之間的差異並*clrTransparent*必須是小於*nTolerance* （紅色、 綠色和藍色），每個色彩元件中。

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

將色彩從 HLS 表示法轉換為 RGB 表示。

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>參數

*H*<br/>
[in]介於 0 到 1，表示色彩的色調。

*L*<br/>
[in]介於 0 和 1，表示色彩的亮度。

*S*<br/>
[in]介於 0 和 1，表示色彩的飽和度。

### <a name="return-value"></a>傳回值

提供的 HLS 色彩 RGB 表示法。

### <a name="remarks"></a>備註

色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需不同的色彩表示方式的詳細資訊，請參閱[色彩](/windows/desktop/uxguide/vis-color)。

這個方法和`CDrawingManager::HLStoRGB_TWO`方法執行相同的作業，但需要不同的值，如*H*參數。 在此方法中， *H*是圓形的百分比。 在 `CDrawingManager::HLStoRGB_TWO`方法中， *H*是程度，值介於 0 到 360 度，表示這兩個紅色。 比方說，使用`HLStoRGB_ONE`，值 0.25，如*H*相當於值與 90 `HLStoRGB_TWO`。

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

將色彩從 HLS 表示法轉換為 RGB 表示。

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>參數

*H*<br/>
[in]表示數字介於 0 和 360 之間的色彩色調。

*L*<br/>
[in]介於 0 和 1，表示色彩的亮度。

*S*<br/>
[in]介於 0 和 1，表示色彩的飽和度。

### <a name="return-value"></a>傳回值

提供的 HLS 色彩 RGB 表示法。

### <a name="remarks"></a>備註

色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需不同的色彩表示方式的詳細資訊，請參閱[色彩](/windows/desktop/uxguide/vis-color)。

這個方法和[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法執行相同的作業，但需要不同的值，如*H*參數。 在此方法中， *H*是程度，值介於 0 到 360 度，表示這兩個紅色。 在  [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法， *H*是圓形的百分比。 比方說，使用`HLStoRGB_ONE`，值 0.25，如*H*相當於值與 90 `HLStoRGB_TWO`。

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
|*H*|[in]表示的數字介於 0 和 360 之間的色彩色調。|
|*S*|[in]介於 0 和 1，表示色彩的飽和度。|
|*V*|[in]介於 0 和 1，表示色彩的值。|

### <a name="return-value"></a>傳回值

提供 HSV 色彩的 RGB 呈現。

### <a name="remarks"></a>備註

色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需不同的色彩表示方式的詳細資訊，請參閱[色彩](/windows/desktop/uxguide/vis-color)。

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

紅色、 綠色或藍色元件會將色調值。

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
[in]請參閱 < 備註 >。

*m2*<br/>
[in]請參閱 < 備註 >。

*h*<br/>
[in]請參閱 < 備註 >。

*rm1*<br/>
[in]請參閱 < 備註 >。

*rm2*<br/>
[in]請參閱 < 備註 >。

*rh*<br/>
[in]請參閱 < 備註 >。

### <a name="return-value"></a>傳回值

提供 hue 的個別紅色、 綠色或藍色元件。

### <a name="remarks"></a>備註

這個方法是一個 helper 方法，`CDrawingManager`類別用來計算個別的紅色、 綠色和藍色元件 HSV 或 HSL 的表示法中的色彩。 這個方法不是直接由程式設計人員呼叫。 輸入的參數是取決於轉換演算法的值。

若要轉換 HSV 或 HSL 色彩的 RGB 表示法，呼叫下列方法之一：

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

*rect*<br/>
[in]若要翻轉區域的周框。

*bHorz*<br/>
[in]布林值參數，指出矩形是否會水平或垂直翻轉。

### <a name="remarks"></a>備註

這個方法可以反轉所擁有的裝置任何的內容區域`CDrawingManager`類別。 如果*bHorz*是設為 TRUE，這個方法的區域會水平翻轉。 否則，它的區域垂直翻轉。

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

*srcPixel*<br/>
[in]像素的初始色彩。

*percent*<br/>
[in]表示數字介於 0 到 100 之間的透明度百分比。 值為 100 表示的初始色彩是完全透明的。

*percentR*<br/>
[in]表示數字介於 0 到 100 之間的紅色元件的透明度百分比。

*percentG*<br/>
[in]表示數字介於 0 到 100 之間的綠色元件的透明度百分比。

*percentB*<br/>
[in]表示數字介於 0 到 100 之間的藍色元件透明度百分比。

*dstPixel*<br/>
[in]基底的像素色彩。

### <a name="return-value"></a>傳回值

半透明的像素的完稿色彩。

### <a name="remarks"></a>備註

這是一個 helper 類別，以色彩標示半透明的點陣圖，而且不是直接由程式設計人員呼叫。

當您使用的版本具有方法*dstPixel*，完稿色彩是由組成*dstPixel*並*srcPixel*。 *SrcPixel*色彩停留的基底的色彩為部分透明的色彩*dstPixel*。

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

建立可用作陰影的點陣圖。

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>參數

*nDepth*<br/>
[in]寬度和高度的陰影。

*clrBase*<br/>
[in]陰影色彩。

*iMinBrightness*<br/>
[in]陰影的最小的亮度。

*iMaxBrightness*<br/>
[in]陰影的最大的亮度。

### <a name="return-value"></a>傳回值

如果成功，這個方法建立點陣圖控制代碼否則為 NULL。

### <a name="remarks"></a>備註

如果*nDepth*是設為 0，這個方法會結束，並傳回 NULL。 如果*nDepth*小於 3，陰影的高度與寬度設定為 3 個像素為單位。

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

將色彩從紅色、 綠色和藍 (RGB) 表示法的色調、 飽和度和亮度 (HSL) 表示法。

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
|*rgb*|[in]色彩 RGB 值。|
|*H*|[out]Double 值，這個方法儲存的色彩色調的位置指標。|
|*S*|[out]Double 值，這個方法儲存的色彩飽和度的位置指標。|
|*L*|[out]Double 值，這個方法儲存的色彩亮度的位置指標。|

### <a name="remarks"></a>備註

色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需不同的色彩表示方式的詳細資訊，請參閱[色彩](/windows/desktop/uxguide/vis-color)。

傳回的值*H*以介於 0 和 1 0 和 1 代表紅色的一小部分。 傳回的值*S*並*L*是介於 0 和 1 之間的數字。

##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV

將色彩 RGB 表示轉換成 HSV 表示。

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>參數

*rgb*<br/>
[in]要轉換的 RGB 表示法中的色彩。

*H*<br/>
[out]Double 值，這個方法儲存產生的色彩色調的位置指標。

*S*<br/>
[out]Double 值，這個方法儲存產生的色彩飽和度的位置指標。

*V*<br/>
[out]Double 值，這個方法儲存產生的色彩值的位置指標。

### <a name="remarks"></a>備註

色彩可以表示為 HSV （色調、 飽和度和值）、 （色調、 飽和度和亮度） 的 HSL 或 RGB （紅色、 綠色和藍色）。 如需不同的色彩表示方式的詳細資訊，請參閱[色彩](/windows/desktop/uxguide/vis-color)。

傳回的值*H*是 0 和 360 之間的數字 0 到 360 度指出紅色。 傳回值*S*並*V*是介於 0 和 1 之間的數字。

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

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

*pBits*<br/>
[in]點陣圖的位元值指標。

*rect*<br/>
[in]您的應用程式中的矩形區域。 繪圖 manager 繪製一個陰影下方和右邊的這個區域。

*x*<br/>
[in]色彩的像素水平座標。

*y*<br/>
[in]像素色彩的垂直座標。

*percent*<br/>
[in]透明度百分比。

*iShadowSize*<br/>
[in]寬度和高度的陰影。

*clrBase*<br/>
[in]陰影色彩。

*bIsRight*<br/>
[in]布林值參數，指出哪一個像素的色彩。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

這個方法是 helper 方法，以供[CDrawingManager::DrawShadow](#drawshadow)方法。 我們建議，如果您想要繪製一個陰影，呼叫`CDrawingManager::DrawShadow`改。

如果*bIsRight*是設為 TRUE，色彩的像素為單位*x*的右邊緣像素*rect*。 如果是 FALSE，以像素色彩*x*像素的左邊緣*rect*。

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

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
|*pBits*|[in]點陣圖的位元值指標。|
|*cx*|[in]點陣圖的總寬度。|
|*cy*|[in]點陣圖的高度總計。|
|*x*|[in]若要變更點陣圖與像素 x 座標。|
|*y*|[in]若要變更點陣圖與像素的 y 座標。|
|*color*|[in]新提供的座標所識別的像素色彩。|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

結合的加權比例為基礎的兩個色彩。

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
|*color1*|[in]混合的第一個色彩。|
|*color2*|[in]混用第二個色彩。|
|*dblLumRatio*|[in]新的色彩亮度的比例。 `SmartMixColors` 乘以此比率的混合色彩的亮度然後再判斷完稿色彩。|
|*k1*|[in]第一個色彩加權的比例。|
|*k2*|[in]第二個色彩的加權的比例。|

### <a name="return-value"></a>傳回值

表示加權的混合提供色彩的色彩。

### <a name="remarks"></a>備註

這個方法會失敗並發生錯誤，如果有任一*k1*或是*k2*小於零。 如果這兩個參數會設定為 0，則方法會傳回`RGB(0, 0, 0)`。

加權的比例使用下列公式計算: (color1\*版 k1 的 powerapps + 色 2 \* k2) /(k1 + k2)。 決定的加權的比例之後，方法會計算的混合色彩的亮度。 它接著會將由亮度*dblLumRatio*。 如果值大於 1.0，方法會設定為新值的混合色彩的亮度。 否則，亮度會設定為 1.0。

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

旋轉 90 度的來源 DC 給定矩形內的內容。

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>參數

*rectDest*<br/>
目的矩形。

*dcSrc*<br/>
來源裝置內容。

*bClockWise*<br/>
TRUE 表示旋轉的 + 90 度。FALSE 表示旋轉的-90 度。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
