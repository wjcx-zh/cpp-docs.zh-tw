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
ms.openlocfilehash: 59c34a69b96cc9986db99b5f34bc38cf76f4909a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374022"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager 類別

類`CDrawingManager`實現複雜的繪圖演演演算法。

## <a name="syntax"></a>語法

```
class CDrawingManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C繪圖管理員:CDRAWING管理員](#cdrawingmanager)|建構 `CDrawingManager` 物件。|
|`CDrawingManager::~CDrawingManager`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDrawing 管理員::CreateBitmap_32](#createbitmap_32)|創建與設備無關的 32 位位元圖 (DIB),應用程式可以直接寫入該位圖。|
|[C繪圖管理員::D原阿爾法](#drawalpha)|顯示具有透明或半透明圖元的位圖。|
|[Cdrawing 管理員::D原始旋轉](#drawrotated)|在給定矩形內旋轉來源 DC 內容,按 +/- 90 度旋轉|
|[C 繪圖管理員::D原始橢圓](#drawellipse)|使用提供的填充和邊框顏色繪製橢圓。|
|[CDrawing 管理員::D原始漸變](#drawgradientring)|繪製環並填充其顏色漸變。|
|[C繪圖管理器::Drawline,Cdrawing經理::DrawlineA](#drawline_cdrawingmanager__drawlinea)|畫一條線。|
|[Cdrawing管理員::D原始](#drawrect)|使用提供的填充和邊框顏色繪製矩形。|
|[C繪圖管理員::D原始陰影](#drawshadow)|為矩形區域繪製陰影。|
|[繪圖管理員::填充4顏色漸變](#fill4colorsgradient)|用兩個顏色漸變填充矩形區域。|
|[C 繪圖管理員::填充漸變](#fillgradient)|使用指定的顏色漸變填充矩形區域。|
|[C 繪圖管理員::填充漸變2](#fillgradient2)|使用指定的顏色漸變填充矩形區域。 還指定漸變顏色變化的方向。|
|[C 繪製管理員:灰色 Rect](#grayrect)|用指定的灰色填充矩形。|
|[Cdrawing 管理員::突出顯示](#highlightrect)|突出顯示矩形區域。|
|[CDrawing 管理員:HLStoRGB_ONE](#hlstorgb_one)|將顏色從 HLS 表示形式轉換為 RGB 表示形式。|
|[CDrawing管理員::HLStoRGB_TWO](#hlstorgb_two)|將顏色從 HLS 表示形式轉換為 RGB 表示形式。|
|[CDrawing 管理員::HSVtoRGB](#hsvtorgb)|將顏色從 HSV 表示形式轉換為 RGB 表示形式。|
|[CDrawing 管理員::HuetoRGB](#huetorgb)|將色調值轉換為紅色、綠色或藍色分量的幫助器方法。|
|[C 繪圖管理員::鏡像重新](#mirrorrect)|翻轉矩形區域。|
|[CDrawing經理::Pixix阿爾法](#pixelalpha)|用於確定半透明圖元的最終顏色的幫助器方法。|
|[C 繪圖管理器::P重影陰影遮罩](#prepareshadowmask)|建立可用作陰影的點陣圖。|
|[CDrawing 管理員::RGBtoHSL](#rgbtohsl)|將顏色從 RGB 表示形式轉換為 HSL 表示形式。|
|[CDrawing管理員::RGBtoHSV](#rgbtohsv)|將顏色從 RGB 表示形式轉換為 HSV 表示形式。|
|[C 繪圖管理員::設定Alpha圖元](#setalphapixel)|説明方法,該方法在位圖中為部分透明圖元提供顏色。|
|[C 繪圖管理員::設定圖元](#setpixel)|説明方法,將位圖中的單個圖元更改為指定顏色。|
|[繪圖管理員::智慧混合顏色](#smartmixcolors)|基於加權比組合兩種顏色。|

## <a name="remarks"></a>備註

該`CDrawingManager`類提供用於繪製陰影、顏色漸變和突出顯示矩形的函數。 它還執行 Alpha 混合。 可以使用此類直接更改應用程式的 UI。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>需求

**標題:** afxdraw 管理器.h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>C繪圖管理員:CDRAWING管理員

構造[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)物件。

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>參數

*直流*<br/>
[在]對設備上下文的引用。 使用此`CDrawingManager`上下文進行繪圖。

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a>CDrawing 管理員::CreateBitmap_32

創建與設備無關的 32 位位元圖 (DIB),應用程式可以直接寫入該位圖。

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
|*大小*|[在]指示點陣圖大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)參數。|
|*pBits*|[出]指向接收 DIB 位值位置的數據指標的指標。|
|*點陣圖*|原始點陣圖的句柄|
|*clr透明*|指定原始點陣圖的透明顏色的 RGB 值。|

### <a name="return-value"></a>傳回值

如果此方法成功,則對新創建的 DIB 位元圖的句柄;否則 NULL。

### <a name="remarks"></a>備註

有關如何創建 DIB 位元圖的詳細資訊,請參閱[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap)。

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>C繪圖管理員::D原阿爾法

顯示具有透明或半透明圖元的位圖。

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>參數

*pDstDC*<br/>
[在]指向目標設備上下文的指標。

*rectDst*<br/>
[在]目標矩形。

*pSrcDC*<br/>
[在]指向源的設備上下文的指標。

*雷克斯爾*<br/>
[在]源矩形。

### <a name="remarks"></a>備註

此方法對兩個位圖執行 Alpha 混合。 有關 Alpha 混合的詳細資訊,請參閱 Windows SDK 中的[AlphaBlend。](/windows/win32/api/wingdi/nf-wingdi-alphablend)

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>C 繪圖管理員::D原始橢圓

使用提供的填充和邊框顏色繪製橢圓。

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]橢圓的邊界矩形。

*clrFill*<br/>
[在]此方法用於填充橢圓的顏色。

*clrLine*<br/>
[在]此方法用作橢圓邊框的顏色。

### <a name="remarks"></a>備註

如果任一顏色設置為 -1,則此方法返回時不繪製橢圓。 如果邊界矩形的任一尺寸為 0,則不繪製橢圓即可返回。

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawing 管理員::D原始漸變

繪製環並填充其顏色漸變。

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

*矩形*<br/>
[在]指定漸變環邊界的[CRect](../../atl-mfc-shared/reference/crect-class.md)參數。

*顏色開始*<br/>
[在]漸變的第一種顏色。

*顏色裝飾*<br/>
[在]漸變的最後一種顏色。

*顏色框*<br/>
[在]邊框的顏色。

*NAngle*<br/>
[在]指定初始漸變繪圖角度的參數。 此值應介於 0 和 360 之間。

*n 寬度*<br/>
[在]環的邊框寬度。

*clrFace*<br/>
[在]戒指內部的顏色。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

由*矩形*定義的矩形必須至少為 5 像素寬和 5 像素高。

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>C繪圖管理器::Drawline,Cdrawing經理::DrawlineA

畫一條線。

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
|*x1*|[在]線起點的 x 座標。|
|*y1*|[在]線啟動位置的 y 座標。|
|*x2*|[在]x 座標,線結束的位置。|
|*y2*|[在]線結束位置的 y 座標。|
|*clrLine*|[在]線條的顏色。|

### <a name="remarks"></a>備註

如果*clrLine*等於 -1,此方法將失敗。

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a>Cdrawing管理員::D原始

使用提供的填充和邊框顏色繪製矩形。

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]矩形的邊界。

*clrFill*<br/>
[在]此方法用於填充矩形的顏色。

*clrLine*<br/>
[在]此方法用於矩形邊框的顏色。

### <a name="remarks"></a>備註

如果任一顏色設置為 -1,則此方法返回而不繪製矩形。 如果矩形的任一尺寸為 0,它也會返回。

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>C繪圖管理員::D原始陰影

為矩形區域繪製陰影。

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

*矩形*<br/>
[在]應用程式中的矩形區域。 繪圖管理器將在此區域下方繪製陰影。

*n 深度*<br/>
[在]陰影的寬度和高度。

*伊明亮度*<br/>
[在]陰影的最小亮度。

*iMax亮度*<br/>
[在]陰影的最大亮度。

*pBmp 儲存底*<br/>
[在]指向位圖的指標,其中包含陰影底部的圖像。

*pBmpSaveRight*<br/>
[在]指向位圖的指標,其中包含在矩形右側繪製的陰影的圖像。

*clrBase*<br/>
[在]陰影的顏色。

*b 右影*<br/>
[在]指示陰影繪製方式的布爾參數。 如果*bRightShadow*是`TRUE`,`DrawShadow`則在矩形的右側繪製陰影。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用參數*pBmpSaveBottom*和*pBmpSaveRight*為底部和右側陰影提供兩個有效的位圖。 如果這些[CBitmap](../../mfc/reference/cbitmap-class.md)物件具有附加的`DrawShadow`GDI 物件,則使用這些位圖作為陰影。 如果`CBitmap`參數沒有附加的 GDI`DrawShadow`物件,請繪製陰影並將位圖附加到參數。 在將來調用`DrawShadow`中,可以提供這些位圖以加快繪圖過程。 有關`CBitmap`類別和 GDI 物件的詳細資訊,請參考[圖形物件](../../mfc/graphic-objects.md)。

如果這些參數中的任何一個為`NULL``DrawShadow`, 將自動繪製陰影。

如果將*bRightShadow*設置為 FALSE,陰影將在矩形區域的下方和左側繪製。

### <a name="example"></a>範例

下面的示例演示如何使用`DrawShadow``CDrawingManager`類的方法。 此代碼段是[道具表演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>繪圖管理員::填充4顏色漸變

用兩個顏色漸變填充矩形區域。

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

*矩形*<br/>
[在]要填充的矩形。

*顏色開始1*<br/>
[在]第一個顏色漸變的初始顏色。

*顏色完成1*<br/>
[在]第一個顏色漸變的最終顏色。

*顏色開始2*<br/>
[在]第二個顏色漸變的初始顏色。

*顏色完成2*<br/>
[在]第二個顏色漸變的最終顏色。

*布霍茲*<br/>
[在]表示`Fill4ColorsGradient`是水準漸變還是垂直漸變顏色的布爾參數。 TRUE 表示水準漸變。

*n 百分比*<br/>
[在]0-100 的整數。 此值指示要填充第一個顏色漸變的矩形的百分比。

### <a name="remarks"></a>備註

當矩形填充兩個顏色漸變時,它們要麼位於彼此之上,要麼位於彼此旁邊,具體取決於*bHorz*的值。 每個顏色漸變都使用方法[CDrawingManager::fill 漸變](#fillgradient)獨立計算。

如果*n%* 小於 0 或超過 100,此方法將產生斷言失敗。

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>C 繪圖管理員::填充漸變

使用指定的顏色漸變填充矩形區域。

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

*矩形*<br/>
[在]要填充的矩形區域。

*顏色開始*<br/>
[在]漸變的第一種顏色。

*顏色裝飾*<br/>
[在]漸變的最終顏色。

*布霍茲*<br/>
[在]指定是`FillGradient`繪製水準漸變還是垂直漸變的布爾參數。

*N 開始平率*<br/>
[在]在開始漸變之前用`FillGradient`*顏色"開始"* 填充的矩形的百分比。

*n 結束平率*<br/>
[在]完成漸變後用顏色`FillGradient`*Finish*填充的矩形的百分比。

### <a name="example"></a>範例

下面的示例演示如何使用`FillGradient``CDrawingManager`類的方法。 此代碼段是 MS [Office 2007 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>C 繪圖管理員::填充漸變2

使用指定的顏色漸變填充矩形區域。

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]要填充的矩形區域。

*顏色開始*<br/>
[在]漸變的第一種顏色。

*顏色裝飾*<br/>
[在]漸變的最後一種顏色。

*NAngle*<br/>
[在]介於 0 和 360 之間的整數。 此參數指定顏色漸變的方向。

### <a name="remarks"></a>備註

使用*nAngle*指定顏色漸變的方向。 指定顏色漸變的方向時,還可以指定顏色漸變的開始位置。 *nAngle*的值為 0 表示漸變從矩形頂部開始。 隨著*nAngle*的增加,漸變的起始位置根據角度以逆時針方向移動。

### <a name="example"></a>範例

下面的示例演示如何使用`FillGradient2``CDrawingManager`類的方法。 此代碼段是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a>C 繪製管理員:灰色 Rect

用指定的灰色填充矩形。

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]要填充的矩形區域。

*n 百分比*<br/>
[在]矩形中所需的灰色百分比。

*clr透明*<br/>
[在]透明顏色。

*clr 已關閉*<br/>
[在]如果*n%* 設定為 -1,則此方法用於消除飽和度的顏色。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

對於參數*n%,* 值越低表示顏色較深。

*n%* 的最大值為 200。 大於 200 的值不會更改矩形的外觀。 如果值為 -1,則此方法使用*clr"禁用"* 來限制矩形的飽和度。

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>Cdrawing 管理員::突出顯示

突出顯示矩形區域。

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]要突出顯示的矩形區域。

*n 百分比*<br/>
[在]表示突出顯示應有多透明的百分比。

*clr透明*<br/>
[在]透明顏色。

*n 公差*<br/>
[在]0 和 255 之間的整數,指示顏色容差。

*clrBlend*<br/>
[在]用於混合的基本顏色。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

如果*n%* 介於`HighlightRect`0 和 99 之間,則使用 Alpha 混合演演演算法。 有關 Alpha 混合的詳細資訊,請參閱[Alpha 混合線和填充](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果*n%* 為 -1,則此方法使用預設高光級別。 如果*n%* 為 100,則此方法不執行任何操作並返回 TRUE。

該方法使用參數*n 容差*來確定是否突出顯示矩形區域。 要突顯矩形,應用程式的背景顏色和*clrTransparent*之間的差值必須小於每個顏色元件(紅色、綠色和藍色)中的*n 容忍度*。

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a>CDrawing 管理員:HLStoRGB_ONE

將顏色從 HLS 表示形式轉換為 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>參數

*H*<br/>
[在]表示顏色色調的 0 和 1 之間的數位。

*我*<br/>
[在]0 和 1 之間的數位,指示顏色的亮度。

*S*<br/>
[在]0 和 1 之間的數位,指示顏色的飽和度。

### <a name="return-value"></a>傳回值

提供的 HLS 顏色的 RGB 表示形式。

### <a name="remarks"></a>備註

顏色可以表示為 HSV(色相、飽和度和值)、HSL(色相、飽和度和亮度)或 RGB(紅色、綠色和藍色)。 有關顏色的不同表示形式的詳細資訊,請參閱[顏色](/windows/win32/uxguide/vis-color)。

此方法和`CDrawingManager::HLStoRGB_TWO`方法執行相同的操作,但*要求 H*參數的值不同。 在此方法中 *,H*是圓的百分比。 在方法`CDrawingManager::HLStoRGB_TWO`中 *,H*是介於 0 和 360 之間的度值,兩者都表示紅色。 例如,對於`HLStoRGB_ONE` *,H*的值為 0.25 等效`HLStoRGB_TWO`於值 90 與 。

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a>CDrawing管理員::HLStoRGB_TWO

將顏色從 HLS 表示形式轉換為 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>參數

*H*<br/>
[在]表示顏色色調的 0 和 360 之間的數位。

*我*<br/>
[在]0 和 1 之間的數位,指示顏色的亮度。

*S*<br/>
[在]0 和 1 之間的數位,指示顏色的飽和度。

### <a name="return-value"></a>傳回值

提供的 HLS 顏色的 RGB 表示形式。

### <a name="remarks"></a>備註

顏色可以表示為 HSV(色相、飽和度和值)、HSL(色相、飽和度和亮度)或 RGB(紅色、綠色和藍色)。 有關顏色的不同表示形式的詳細資訊,請參閱[顏色](/windows/win32/uxguide/vis-color)。

此方法和[CDrawingManager:::HLStoRGB_ONE](#hlstorgb_one)方法執行相同的操作,但*要求 H*參數的值不同。 在此方法中 *,H*是介於 0 和 360 之間的度值,兩者都表示紅色。 在[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法中 *,H*是圓的百分比。 例如,對於`HLStoRGB_ONE` *,H*的值為 0.25 等效`HLStoRGB_TWO`於值 90 與 。

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawing 管理員::HSVtoRGB

將顏色從 HSV 表示形式轉換為 RGB 表示形式。

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
|*H*|[在]介於 0 和 360 之間的數位,指示顏色的色調。|
|*S*|[在]0 和 1 之間的數位,指示顏色的飽和度。|
|*五*|[在]0 和 1 之間的數位,指示顏色的值。|

### <a name="return-value"></a>傳回值

提供的 HSV 顏色的 RGB 表示形式。

### <a name="remarks"></a>備註

顏色可以表示為 HSV(色相、飽和度和值)、HSL(色相、飽和度和亮度)或 RGB(紅色、綠色和藍色)。 有關顏色的不同表示形式的詳細資訊,請參閱[顏色](/windows/win32/uxguide/vis-color)。

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawing 管理員::HuetoRGB

將色調值轉換為紅色、綠色或藍色分量。

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
[在]請參閱備註。

*m2*<br/>
[在]請參閱備註。

*H*<br/>
[在]請參閱備註。

*rm1*<br/>
[在]請參閱備註。

*rm2*<br/>
[在]請參閱備註。

*Rh*<br/>
[在]請參閱備註。

### <a name="return-value"></a>傳回值

提供色調的單個紅色、綠色或藍色分量。

### <a name="remarks"></a>備註

此方法是`CDrawingManager`一種説明器方法,類用於計算 HSV 或 HSL 表示形式中顏色的單個紅色、綠色和藍色分量。 此方法不是設計為由程式師直接調用的。 輸入參數是依賴於轉換演演算法的值。

要將 HSV 或 HSL 顏色轉換為 RGB 表示形式,請呼叫以下方法之一:

- [CDrawing 管理員::HSVtoRGB](#hsvtorgb)

- [CDrawing 管理員:HLStoRGB_ONE](#hlstorgb_one)

- [CDrawing管理員::HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>C 繪圖管理員::鏡像重新

翻轉矩形區域。

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]要翻轉的區域的邊界矩形。

*布霍茲*<br/>
[在]表示矩形是水平翻轉還是垂直翻轉的布爾參數。

### <a name="remarks"></a>備註

此方法可以翻轉`CDrawingManager`類擁有的設備上下文的任何區域。 如果*bHorz*設置為 TRUE,則此方法將水準翻轉區域。 否則,它會垂直翻轉區域。

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawing經理::Pixix阿爾法

計算半透明像素的最終顏色。

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
[在]像素的初始顏色。

*百分比*<br/>
[在]表示透明度百分比的 0 和 100 之間的數位。 值 100 表示初始顏色完全透明。

*百分比R*<br/>
[在]表示紅色元件透明度百分比的 0 和 100 之間的數位。

*百分比G*<br/>
[在]表示綠色元件透明度百分比的 0 和 100 之間的數位。

*百分比B*<br/>
[在]表示藍色元件透明度百分比的 0 和 100 之間的數位。

*dstPixel*<br/>
[在]圖元的基本顏色。

### <a name="return-value"></a>傳回值

半透明圖元的最終顏色。

### <a name="remarks"></a>備註

這是一個用於著色半透明位圖的幫助器類,並且不是設計為由程式師直接調用的。

當您使用具有*dstPixel*的方法的版本時,最終顏色是*dstPixel*和*srcPixel*的組合。 *srcPixel*顏色是*dstPixel*基礎顏色上的部分透明顏色。

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>C 繪圖管理器::P重影陰影遮罩

建立可用作陰影的點陣圖。

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>參數

*n 深度*<br/>
[在]陰影的寬度和高度。

*clrBase*<br/>
[在]陰影的顏色。

*伊明亮度*<br/>
[在]陰影的最小亮度。

*iMax亮度*<br/>
[在]陰影的最大亮度。

### <a name="return-value"></a>傳回值

如果此方法成功,則對創建的位圖的句柄;否則 NULL。

### <a name="remarks"></a>備註

如果*nDepth*設定為 0,則此方法將退出並返回 NULL。 如果*nDepth*小於 3,陰影的寬度和高度將設置為 3 圖元。

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawing 管理員::RGBtoHSL

將顏色從紅色、綠色和藍色 (RGB) 表示轉換為色調、飽和度和光度 (HSL) 表示。

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
|*Rgb*|[在]RGB 值中的顏色。|
|*H*|[出]指向雙精度值的指標,該方法在其中存儲顏色的色調。|
|*S*|[出]指向雙精度值的指標,該方法在其中存儲顏色的飽和度。|
|*我*|[出]指向雙精度值的指標,該方法在其中存儲顏色的輕盈度。|

### <a name="remarks"></a>備註

顏色可以表示為 HSV(色相、飽和度和值)、HSL(色相、飽和度和亮度)或 RGB(紅色、綠色和藍色)。 有關顏色的不同表示形式的詳細資訊,請參閱[顏色](/windows/win32/uxguide/vis-color)。

*H*的返回值表示為 0 和 1 之間的分數,其中 0 和 1 表示紅色。 *S*和*L*的返回值是介於 0 和 1 之間的數位。

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawing管理員::RGBtoHSV

將顏色從 RGB 表示形式轉換為 HSV 表示形式。

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>參數

*Rgb*<br/>
[在]要在 RGB 表示形式中轉換的顏色。

*H*<br/>
[出]指向雙精度值的指標,此方法在其中存儲顏色的結果色調。

*S*<br/>
[出]指向雙精度值的指標,此方法存儲生成的顏色飽和度。

*五*<br/>
[出]指向雙精度值的指標,其中此方法存儲顏色的生成值。

### <a name="remarks"></a>備註

顏色可以表示為 HSV(色相、飽和度和值)、HSL(色相、飽和度和亮度)或 RGB(紅色、綠色和藍色)。 有關顏色的不同表示形式的詳細資訊,請參閱[顏色](/windows/win32/uxguide/vis-color)。

*H*的返回值是介於 0 和 360 之間的數位,其中 0 和 360 都表示紅色。 *S*和*V*的傳回值是介於 0 和 1 之間的數位。

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>C 繪圖管理員::設定Alpha圖元

在點陣圖中為透明圖元添加顏色。

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
[在]指向位圖的位值的指標。

*矩形*<br/>
[在]應用程式中的矩形區域。 繪圖管理器在此區域的下方和右側繪製陰影。

*X.*<br/>
[在]像素到顏色的水平座標。

*Y*<br/>
[在]像素到顏色的垂直座標。

*百分比*<br/>
[在]透明度的百分比。

*iShadowSize*<br/>
[在]陰影的寬度和高度。

*clrBase*<br/>
[在]陰影的顏色。

*bIsRight*<br/>
[在]指示要著色的像素的布爾參數。 如需詳細資訊，請參閱「備註」一節。

### <a name="remarks"></a>備註

此方法是[CDrawingManager::DrawShadow](#drawshadow)方法使用的説明方法。 我們建議您,如果要繪製陰影,請改為呼叫`CDrawingManager::DrawShadow`。

如果*bIsRight*設定為 TRUE,則從*rect*的右*邊緣測量到*顏色的圖元 x 圖元。 如果是 FALSE,則從*rect*的左*邊緣測量到*顏色的圖元 x 圖元。

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a>C 繪圖管理員::設定圖元

將點陣圖中的單個像素更改為指定顏色。

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
|*pBits*|[在]指向位圖的位值的指標。|
|*殘雪*|[在]位圖的總寬度。|
|*cy*|[在]位圖的總高度。|
|*X.*|[在]要更改的點陣圖中像素的 x 座標。|
|*Y*|[在]要更改的點陣圖中畫素的 y 座標。|
|*顏色*|[在]由提供的座標標識的圖元的新顏色。|

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>繪圖管理員::智慧混合顏色

基於加權比組合兩種顏色。

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
|*顏色1*|[在]要混合的第一種顏色。|
|*顏色2*|[在]要混合的第二種顏色。|
|*德布勒雷比*|[在]新顏色亮度的比率。 `SmartMixColors`在確定最終顏色之前,將混合顏色的亮度乘以此比率。|
|*k1*|[在]第一種顏色的加權比率。|
|*k2*|[在]第二種顏色的加權比率。|

### <a name="return-value"></a>傳回值

表示所提供顏色的加權混合的顏色。

### <a name="remarks"></a>備註

如果*k1*或*k2*小於零,則此方法失敗,出現錯誤。 如果這兩個參數都設定為 0,則方法將`RGB(0, 0, 0)`傳回 。

加權比率的計算公式如下:(顏色 1 \* k1\*= 顏色 2 k2)/(k1 = k2)。 確定加權比后,該方法計算混合顏色的亮度。 然後,它將亮度乘以*dblLumratio。* 如果值大於 1.0,則該方法將混合顏色的亮度設置為新值。 否則,亮度設置為 1.0。

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>Cdrawing 管理員::D原始旋轉

將給定矩形內的源 DC 內容旋轉 90 度。

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>參數

*整流*<br/>
目標矩形。

*直流*<br/>
源設備上下文。

*bClockWise*<br/>
TRUE 表示旋轉 +90 度;TRUE 表示旋轉 90 度;FALSE 表示旋轉 -90 度。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
