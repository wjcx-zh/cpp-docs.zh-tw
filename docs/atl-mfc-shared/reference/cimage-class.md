---
title: CImage 類別
ms.date: 08/19/2019
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
ms.openlocfilehash: 3b278f37bbcbe2ee879d9c3d2837267fe31e57e2
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630721"
---
# <a name="cimage-class"></a>CImage 類別

`CImage`提供增強的點陣圖支援, 包括以 JPEG、GIF、BMP 和可移植網狀圖形 (PNG) 格式載入和儲存影像的能力。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CImage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CImage::CImage](#cimage)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|顯示具有透明或半透明圖元的點陣圖。|
|[CImage::Attach](#attach)|將 HBITMAP 附加至`CImage`物件。 可以與非 DIB 區段點陣圖或 DIB 區段點陣圖搭配使用。|
|[CImage::BitBlt](#bitblt)|將點陣圖從來源裝置內容複寫到這個目前的裝置內容。|
|[CImage::Create](#create)|建立 DIB 區段點陣圖, 並將其附加至先前`CImage`所建立的物件。|
|[CImage::CreateEx](#createex)|建立 DIB 區段點陣圖 (含其他參數), 並將它附加至先前`CImage`所建立的物件。|
|[CImage::Destroy](#destroy)|從`CImage`物件卸離點陣圖, 然後銷毀點陣圖。|
|[CImage::Detach](#detach)|從`CImage`物件卸離點陣圖。|
|[CImage::Draw](#draw)|將點陣圖從來源矩形複製到目的地矩形。 `Draw`視需要縮放或壓縮點陣圖以符合目的矩形的尺寸, 並處理 Alpha 混合和透明色彩。|
|[CImage::GetBits](#getbits)|抓取點陣圖實際圖元值的指標。|
|[CImage::GetBPP](#getbpp)|抓取每圖元的位數。|
|[CImage::GetColorTable](#getcolortable)|從 color 資料表中的某個專案範圍, 抓取紅色、綠色、藍色 (RGB) 色彩值。|
|[CImage::GetDC](#getdc)|抓取要在其中選取目前點陣圖的裝置內容。|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|尋找可用的影像格式及其描述。|
|[CImage::GetHeight](#getheight)|抓取目前影像的高度 (以圖元為單位)。|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|尋找可用的影像格式及其描述。|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|抓取 color 資料表中的最大專案數。|
|[CImage::GetPitch](#getpitch)|抓取目前影像的間距 (以位元組為單位)。|
|[CImage::GetPixel](#getpixel)|抓取*x*和*y*所指定之圖元的色彩。|
|[CImage::GetPixelAddress](#getpixeladdress)|抓取指定圖元的位址。|
|[CImage::GetTransparentColor](#gettransparentcolor)|抓取 color 資料表中透明色彩的位置。|
|[CImage::GetWidth](#getwidth)|抓取目前影像的寬度 (以圖元為單位)。|
|[CImage::IsDIBSection](#isdibsection)|判斷附加的點陣圖是否為 DIB 區段。|
|[CImage::IsIndexed](#isindexed)|表示點陣圖的色彩會對應至索引色板。|
|[CImage::IsNull](#isnull)|指出目前是否已載入來源點陣圖。|
|[CImage::IsTransparencySupported](#istransparencysupported)|指出應用程式是否支援透明點陣圖。|
|[CImage::Load](#load)|從指定的檔案載入影像。|
|[CImage::LoadFromResource](#loadfromresource)|從指定的資源載入影像。|
|[CImage::MaskBlt](#maskblt)|使用指定的遮罩和點陣運算, 結合來源與目的地點陣圖的色彩資料。|
|[CImage::PlgBlt](#plgblt)|執行位區塊從來源裝置內容中的矩形傳送到目的地裝置內容中的平行四邊形。|
|[CImage::ReleaseDC](#releasedc)|釋放使用[CImage:: GetDC](#getdc)所抓取的裝置內容。|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|釋放 GDI + 所使用的資源。 必須呼叫, 才能釋放由全域`CImage`物件所建立的資源。|
|[CImage::Save](#save)|將影像儲存為指定的類型。 `Save`無法指定影像選項。|
|[CImage::SetColorTable](#setcolortable)|在 DIB 區段的 color 資料表中, 設定專案範圍內的紅色、綠色、藍色 RGB) 色彩值。|
|[CImage::SetPixel](#setpixel)|將指定座標處的圖元設定為指定的色彩。|
|[CImage::SetPixelIndexed](#setpixelindexed)|將指定座標處的圖元設定為調色板指定索引處的色彩。|
|[CImage::SetPixelRGB](#setpixelrgb)|將指定座標處的圖元設定為指定的紅色、綠色、藍色 (RGB) 值。|
|[CImage::SetTransparentColor](#settransparentcolor)|設定要視為透明的色彩索引。 調色板中只有一個色彩可以是透明的。|
|[CImage::StretchBlt](#stretchblt)|將點陣圖從來源矩形複製到目的地矩形, 視需要延展或壓縮點陣圖以符合目的矩形的尺寸。|
|[CImage::TransparentBlt](#transparentblt)|從來源裝置內容, 將具有透明色彩的點陣圖複製到這個目前的裝置內容。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CImage:: operator HBITMAP](#operator_hbitmap)|傳回附加至`CImage`物件的 Windows 控制碼。|

## <a name="remarks"></a>備註

`CImage`採用不是裝置獨立點陣圖 (DIB) 區段的點陣圖;不過, 您只能使用具有 DIB 區段的[Create](#create)或[CImage:: Load](#load) 。 您可以使用[attach](#attach)將非 DIB 區段點陣圖附加`CImage`至`CImage`物件, 但是您無法使用下列僅支援 DIB 區段點陣圖的方法:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

若要判斷附加的點陣圖是否為 DIB 區段, 請呼叫[IsDibSection](#isdibsection)。

> [!NOTE]
> 在 Visual Studio .net 2003 中, 此類別會保留所建立的`CImage`物件數目計數。 每當計數變成0時, `GdiplusShutdown`就會自動呼叫函式來釋放 gdi + 所使用的資源。 這可確保由`CImage` dll 直接或間接建立的任何物件一律會正確地終結`GdiplusShutdown` , 而且不會`DllMain`從呼叫。

> [!NOTE]
> 不建議`CImage`在 DLL 中使用全域物件。 如果您需要在 DLL 中使用`CImage`全域物件, 請呼叫[CImage:: ReleaseGDIPlus](#releasegdiplus)以明確釋放 gdi + 所使用的資源。

`CImage`無法選取到新的[CDC](../../mfc/reference/cdc-class.md)。 `CImage`為映射建立自己的 HDC。 因為一次只能將一個 HBITMAP 選取為一個 hdc, 所以與`CImage`關聯的 HBITMAP 無法選取至另一個 hdc。 如果您需要 CDC, 請從`CImage`取出此 HDC, 並將其提供給[CDC:: FromHandle](../../mfc/reference/cdc-class.md#fromhandle)。

## <a name="example"></a>範例

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

當您在`CImage` MFC 專案中使用時, 請注意專案中的成員函式會預期[CBitmap](../../mfc/reference/cbitmap-class.md)物件的指標。 如果您想要使用`CImage`搭配這類函式 (例如[CMenu:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)), 請使用[CBitmap:: FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), `CImage`將您的 HBITMAP 傳遞給`CBitmap*`它, 然後使用傳回的。

## <a name="example"></a>範例

```cpp
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);

    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x,
    point.y, this);
}
```

透過`CImage`, 您可以存取 DIB 區段的實際位。 您可以在先前`CImage`使用過 Win32 HBITMAP 或 DIB 區段的任何位置使用物件。

您可以從`CImage` MFC 或 ATL 使用。

> [!NOTE]
> 當您使用`CImage`建立專案時, 您必須在`CString`包含*atlimage*之前定義。 如果您的專案使用 ATL 但沒有 MFC, 請在包含*atlimage*之前加入*和 atlstr.h* 。 如果您的專案使用 MFC (或者, 如果它是具有 MFC 支援的 ATL 專案), 請在包含*atlimage*之前加入*afxstr* 。<br/>
> <br/>
> 同樣地, 在包含*atlimpl*之前, 您必須包含*atlimage* 。 若要輕鬆完成這項操作, 請在您的*pch .h*中包含*atlimage* (在 Visual Studio 2017 和更早版本中的*stdafx.h* )。

## <a name="requirements"></a>需求

**標頭:** atlimage。h

##  <a name="alphablend"></a>CImage:: AlphaBlend

顯示具有透明或半透明圖元的點陣圖。

```
BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    const POINT& pointDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>參數

*hDestDC*<br/>
目的地裝置內容的控制碼。

*xDest*<br/>
目的矩形左上角的 x 座標 (以邏輯單位表示)。

*yDest*<br/>
目的矩形左上角的 y 座標 (以邏輯單位表示)。

*bSrcAlpha*<br/>
要在整個來源點陣圖上使用的 Alpha 透明度值。 預設的 0xff (255) 會假設您的影像不透明, 而且您只想要使用每個圖元的 Alpha 值。

*bBlendOp*<br/>
適用于來源和目的地點陣圖的 Alpha 混合函式、要套用至整個來源點陣圖的全域 Alpha 值, 以及來源點陣圖的格式資訊。 來源和目的地 blend 函數目前僅限於 AC_SRC_OVER。

*pointDest*<br/>
[點](/previous-versions/dd162805\(v=vs.85\))結構的參考, 識別目的矩形的左上角 (以邏輯單位表示)。

*nDestWidth*<br/>
目的地矩形的寬度 (以邏輯單位表示)。

*nDestHeight*<br/>
目的地矩形的高度 (以邏輯單位表示)。

*xSrc*<br/>
來源矩形左上角的邏輯 x 座標。

*ySrc*<br/>
來源矩形左上角的邏輯 y 座標。

*nSrcWidth*<br/>
來源矩形的寬度 (以邏輯單位表示)。

*nSrcHeight*<br/>
來源矩形的高度 (以邏輯單位表示)。

*rectDest*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考, 識別目的地。

*rectSrc*<br/>
`RECT`結構的參考, 識別來源。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

Alpha-blend 點陣圖支援以每個圖元為基礎的色彩混合。

當*bBlendOp*設定為 AC_SRC_OVER 的預設值時, 會根據來源圖元的 Alpha 值, 將來源點陣圖放在目的地點陣圖上。

##  <a name="attach"></a>CImage:: Attach

將*hBitmap*附加至`CImage`物件。

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
HBITMAP 的控制碼。

*eOrientation*<br/>
指定點陣圖的方向。 可以是下列其中一項：

- DIBOR_DEFAULT 點陣圖的方向是由作業系統決定。

- DIBOR_BOTTOMUP 點陣圖的線條是以反向順序排列。 這會導致[CImage:: GetBits](#getbits)傳回點陣圖緩衝區結尾附近的指標, 而[CImage:: GetPitch](#getpitch)會傳回負數。

- DIBOR_TOPDOWN: 點陣圖的線條是從上到下的順序。 這會使[CImage:: GetBits](#getbits)傳回點陣圖緩衝區第一個位元組的指標, 並使用[CImage:: GetPitch](#getpitch)傳回正數。

### <a name="remarks"></a>備註

點陣圖可以是非 DIB 區段點陣圖或 DIB 區段點陣圖。 如需您只能搭配 DIB 區段點陣圖使用之方法的清單, 請參閱[IsDIBSection](#isdibsection) 。

##  <a name="bitblt"></a>  CImage::BitBlt

將點陣圖從來源裝置內容複寫到這個目前的裝置內容。

```
BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const POINT& pointDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>參數

*hDestDC*<br/>
目的地 HDC。

*xDest*<br/>
目的矩形左上角的邏輯 x 座標。

*yDest*<br/>
目的矩形左上角的邏輯 y 座標。

*dwROP*<br/>
要執行的點陣運算。 「點陣操作代碼」定義了如何結合來源、目的地和模式 (如目前選取的筆刷所定義) 的位來形成目的地的確切方式。 如需其他點陣作業代碼及其描述的清單, 請參閱 Windows SDK 中的[BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 。

*pointDest*<br/>
[點](/previous-versions/dd162805\(v=vs.85\))結構, 指出目的矩形的左上角。

*nDestWidth*<br/>
目的地矩形的寬度 (以邏輯單位表示)。

*nDestHeight*<br/>
目的地矩形的高度 (以邏輯單位表示)。

*xSrc*<br/>
來源矩形左上角的邏輯 x 座標。

*ySrc*<br/>
來源矩形左上角的邏輯 y 座標。

*rectDest*<br/>
表示目的矩形的[矩形](/previous-versions/dd162897\(v=vs.85\))結構。

*pointSrc*<br/>
`POINT`結構, 表示來源矩形的左上角。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 。

##  <a name="cimage"></a>CImage:: CImage

建構 `CImage` 物件。

```
CImage() throw();
```

### <a name="remarks"></a>備註

一旦您已建立物件, 請呼叫[Create](#create)、 [Load](#load)、 [LoadFromResource](#loadfromresource)或[attach](#attach) , 將點陣圖附加至物件。

**注意**在 Visual Studio 中, 這個類別會保留所建立的`CImage`物件數目計數。 每當計數變成0時, `GdiplusShutdown`就會自動呼叫函式來釋放 gdi + 所使用的資源。 這可確保由`CImage` dll 直接或間接建立的任何物件一律會正確地終結`GdiplusShutdown` , 而且不會從 DllMain 呼叫。

不建議`CImage`在 DLL 中使用全域物件。 如果您需要在 DLL 中使用`CImage`全域物件, 請呼叫[CImage:: ReleaseGDIPlus](#releasegdiplus)以明確釋放 gdi + 所使用的資源。

##  <a name="create"></a>CImage:: Create

建立點陣圖, 並將其附加至`CImage`先前所建立的物件。 `CImage`

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*nWidth*<br/>
`CImage`點陣圖的寬度 (以圖元為單位)。

*nHeight*<br/>
`CImage`點陣圖的高度 (以圖元為單位)。 如果*nHeight*為正數, 則點陣圖是由上而下的 DIB, 其原點是左下角。 如果*nHeight*是負數, 則點陣圖是由上而下的 DIB, 其原點是左上角。

*nBPP*<br/>
點陣圖中每個圖元的位數。 通常是4、8、16、24或32。 單色點陣圖或遮罩可以是1。

*dwFlags*<br/>
指定點陣圖物件是否有 Alpha 色板。 可以是下列零個或多個值的組合:

- *createAlphaChannel*只有在*nBPP*為 32, 且*eCompression*為 BI_RGB 時, 才可以使用。 如果指定, 則建立的影像會有每個圖元的 Alpha (透明度) 值, 儲存在每個圖元的第4個位元組 (未在非 Alpha 32 位影像中使用)。 呼叫[CImage:: AlphaBlend](#alphablend)時, 會自動使用此 Alpha 色板。

> [!NOTE]
> 在[CImage::D raw](#draw)的呼叫中, 具有 Alpha 色板的影像會自動以 Alpha 方式混合到目的地。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="createex"></a>CImage:: CreateEx

建立點陣圖, 並將其附加至`CImage`先前所建立的物件。 `CImage`

```
BOOL CreateEx(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD eCompression,
    const DWORD* pdwBitmasks = NULL,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*nWidth*<br/>
`CImage`點陣圖的寬度 (以圖元為單位)。

*nHeight*<br/>
`CImage`點陣圖的高度 (以圖元為單位)。 如果*nHeight*為正數, 則點陣圖是由上而下的 DIB, 其原點是左下角。 如果*nHeight*是負數, 則點陣圖是由上而下的 DIB, 其原點是左上角。

*nBPP*<br/>
點陣圖中每個圖元的位數。 通常是4、8、16、24或32。 單色點陣圖或遮罩可以是1。

*eCompression*<br/>
指定壓縮的底部點陣圖的壓縮類型 (無法壓縮由上而下的 Dib)。 可為下列其中一個值：

- BI_RGB 格式已解壓縮。 當呼叫`CImage::CreateEx`相當於呼叫`CImage::Create`時, 指定此值。

- BI_BITFIELDS 格式已解壓縮, 而 color 資料表包含三個 DWORD 色彩遮罩, 分別指定每個圖元的紅色、綠色和藍色元件。 這在與16和 32-bpp 點陣圖搭配使用時是有效的。

*pdwBitfields*<br/>
只有在*eCompression*設定為 BI_BITFIELDS 時才會使用, 否則它必須是 Null。 三個 DWORD 位元遮罩之陣列的指標, 指定每個圖元的位分別用於色彩的紅色、綠色和藍色元件。 如需位欄位限制的詳細資訊, 請參閱 Windows SDK 中的[BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) 。

*dwFlags*<br/>
指定點陣圖物件是否有 Alpha 色板。 可以是下列零個或多個值的組合:

- *createAlphaChannel*只有在*nBPP*為 32, 且*eCompression*為 BI_RGB 時, 才可以使用。 如果指定, 則建立的影像會有每個圖元的 Alpha (透明度) 值, 儲存在每個圖元的第4個位元組 (未在非 Alpha 32 位影像中使用)。 呼叫[CImage:: AlphaBlend](#alphablend)時, 會自動使用此 Alpha 色板。

   > [!NOTE]
   > 在[CImage::D raw](#draw)的呼叫中, 具有 Alpha 色板的影像會自動以 Alpha 方式混合到目的地。

### <a name="return-value"></a>傳回值

如果成功, 則為 TRUE。 否則為 FALSE。

### <a name="example"></a>範例

下列範例會建立100x100 圖元點陣圖, 並使用16位來編碼每個圖元。 在指定的16位圖元中, bits 0-3 會將紅色元件編碼、bits 4-7 編碼為綠色, 而 bits 8-11 編碼為藍色。 剩餘的4個位則未使用。

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>CImage::D estroy

從`CImage`物件卸離點陣圖, 然後銷毀點陣圖。

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

從`CImage`物件卸離點陣圖。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>傳回值

卸離點陣圖的控制碼, 如果未附加點陣圖則為 Null。

##  <a name="draw"></a>CImage::D raw

將點陣圖從來源裝置內容複寫到目前的裝置內容。

```
BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest) const throw();

BOOL Draw(
    HDC hDestDC,
    const POINT& pointDest) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest) const throw();
```

### <a name="parameters"></a>參數

*hDestDC*<br/>
目的地裝置內容的控制碼。

*xDest*<br/>
目的矩形左上角的 x 座標 (以邏輯單位表示)。

*yDest*<br/>
目的矩形左上角的 y 座標 (以邏輯單位表示)。

*nDestWidth*<br/>
目的地矩形的寬度 (以邏輯單位表示)。

*nDestHeight*<br/>
目的地矩形的高度 (以邏輯單位表示)。

*xSrc*<br/>
來源矩形左上角的 x 座標 (以邏輯單位表示)。

*ySrc*<br/>
來源矩形左上角的 y 座標 (以邏輯單位表示)。

*nSrcWidth*<br/>
來源矩形的寬度 (以邏輯單位表示)。

*nSrcHeight*<br/>
來源矩形的高度 (以邏輯單位表示)。

*rectDest*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考, 識別目的地。

*rectSrc*<br/>
`RECT`結構的參考, 識別來源。

*pointDest*<br/>
[點](/previous-versions/dd162805\(v=vs.85\))結構的參考, 識別目的矩形的左上角 (以邏輯單位表示)。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Draw`會執行與[StretchBlt](#stretchblt)相同的作業, 除非影像包含透明色彩或 Alpha 色板。 在此情況下`Draw` , 會視需要執行與[TransparentBlt](#transparentblt)或[AlphaBlend](#alphablend)相同的作業。

若為未`Draw`指定來源矩形的版本, 則整個來源影像為預設值。 若為未指定`Draw`目的地矩形大小的版本, 則來源影像的大小為預設值, 而且不會發生任何延展或縮小。

##  <a name="getbits"></a>CImage:: GetBits

抓取點陣圖中給定圖元之實際位值的指標。

```
void* GetBits() throw();
```

### <a name="return-value"></a>傳回值

點陣圖緩衝區的指標。 如果點陣圖是由上而下的 DIB, 指標會指向緩衝區結尾附近。 如果點陣圖是由上而下的 DIB, 指標會指向緩衝區的第一個位元組。

### <a name="remarks"></a>備註

使用這個指標以及[GetPitch](#getpitch)所傳回的值, 您可以找出並變更影像中的個別圖元。

> [!NOTE]
> 這個方法只支援 DIB 區段點陣圖;因此, 您可以使用與 DIB 區段`CImage`圖元相同的方式來存取物件的圖元。 傳回的指標指向位置 (0, 0) 的圖元。

##  <a name="getbpp"></a>  CImage::GetBPP

抓取每個圖元的位數值。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>傳回值

每圖元的位數數目。

### <a name="remarks"></a>備註

這個值會決定定義每個圖元的位數, 以及點陣圖中的最大色彩數目。

每圖元的位數通常是1、4、8、16、24或32。 如需此值的詳細資訊, 請參閱 Windows SDK 中的[BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) 成員。`biBitCount`

##  <a name="getcolortable"></a>  CImage::GetColorTable

從 DIB 區段的調色板中的某個專案範圍, 抓取紅色、綠色、藍色 (RGB) 色彩值。

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>參數

*iFirstColor*<br/>
要抓取之第一個專案的 color 資料表索引。

*nColors*<br/>
要取出的色彩資料表專案數目。

*prgbColors*<br/>
要抓取色彩資料表專案之[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)結構陣列的指標。

##  <a name="getdc"></a>  CImage::GetDC

抓取目前已在其中選取影像的裝置內容。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>傳回值

裝置內容的控制代碼。

### <a name="remarks"></a>備註

對於的每個`GetDC`呼叫, 您都必須有後續的[ReleaseDC](#releasedc)呼叫。

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

尋找可用於儲存影像的影像格式。

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>參數

*strExporters*<br/>
對 `CSimpleString` 物件的參考。 如需詳細資訊, 請參閱**備註**。

*aguidFileTypes*<br/>
Guid 的陣列, 其中每個元素都會對應至字串中的其中一個檔案類型。 在下面*pszAllFilesDescription*的範例中, *aguidFileTypes*[0] 是 GUID_Null, 而其餘的陣列值則是目前作業系統所支援的影像檔案格式。

> [!NOTE]
> 如需常數的完整清單, 請參閱 Windows SDK 中的**影像檔案格式常數**。

*pszAllFilesDescription*<br/>
如果此參數不是 Null, 則篩選字串在清單的開頭會有一個額外的篩選。 此篩選器的描述會有目前的*pszAllFilesDescription*值, 並接受清單中任何其他匯出工具所支援之任何副檔名的檔案。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
一組位旗標, 用來指定要從清單中排除的檔案類型。 允許的旗標如下:

- `excludeGIF`= 0x01 排除 GIF 檔案。

- `excludeBMP`= 0x02 排除 BMP (Windows 點陣圖) 檔案。

- `excludeEMF`= 0x04 排除 EMF (增強型中繼檔) 檔案。

- `excludeWMF`= 0x08 排除 WMF (Windows 中繼檔) 檔案。

- `excludeJPEG`= 0x10 排除 JPEG 檔案。

- `excludePNG`= 0x20 排除 PNG 檔案。

- `excludeTIFF`= 0x40 排除 TIFF 檔案。

- `excludeIcon`= 0x80 排除 .ICO (Windows 圖示) 檔案。

- `excludeOther`= 0x80000000 排除以上未列出的任何其他檔案類型。

- `excludeDefaultLoad`= 0 載入時, 預設會包含所有檔案類型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`針對儲存, 預設會排除這些檔案, 因為它們通常有特殊需求。

*chSeparator*<br/>
影像格式之間使用的分隔符號。 如需詳細資訊, 請參閱**備註**。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞至 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)物件, 以公開 [檔案另存新檔] 對話方塊中可用影像格式的副檔名。

參數*strExporter*的格式如下:

file description0&#124; \*. ext0&#124;&#124;filedescription1\*. ext1&#124;.。。檔案描述*n* &#124; \*. ext *n*&#124;&#124;

其中 '&#124;' 是所指定`chSeparator`的分隔字元。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果您將此字串&#124;傳遞至 MFC `CFileDialog`物件, 請使用預設分隔符號 ' '。 如果您將此字串傳遞至通用 [檔案儲存] 對話方塊, 請使用 null 分隔符號 ' \ 0 '。

##  <a name="getheight"></a>CImage:: GetHeight

抓取影像的高度 (以圖元為單位)。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>傳回值

影像的高度 (以圖元為單位)。

##  <a name="getimporterfilterstring"></a>CImage:: GetImporterFilterString

尋找可用於載入影像的影像格式。

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>參數

*strImporters*<br/>
對 `CSimpleString` 物件的參考。 如需詳細資訊, 請參閱**備註**。

*aguidFileTypes*<br/>
Guid 的陣列, 其中每個元素都會對應至字串中的其中一個檔案類型。 在下面的*pszAllFilesDescription*範例中, *aguidFileTypes*[0] 是 GUID_Null, 其餘的陣列值是目前作業系統所支援的影像檔案格式。

> [!NOTE]
> 如需常數的完整清單, 請參閱 Windows SDK 中的**影像檔案格式常數**。

*pszAllFilesDescription*<br/>
如果此參數不是 Null, 則篩選字串在清單的開頭會有一個額外的篩選。 此篩選器的描述會有目前的*pszAllFilesDescription*值, 並接受清單中任何其他匯出工具所支援之任何副檔名的檔案。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
一組位旗標, 用來指定要從清單中排除的檔案類型。 允許的旗標如下:

- `excludeGIF`= 0x01 排除 GIF 檔案。

- `excludeBMP`= 0x02 排除 BMP (Windows 點陣圖) 檔案。

- `excludeEMF`= 0x04 排除 EMF (增強型中繼檔) 檔案。

- `excludeWMF`= 0x08 排除 WMF (Windows 中繼檔) 檔案。

- `excludeJPEG`= 0x10 排除 JPEG 檔案。

- `excludePNG`= 0x20 排除 PNG 檔案。

- `excludeTIFF`= 0x40 排除 TIFF 檔案。

- `excludeIcon`= 0x80 排除 .ICO (Windows 圖示) 檔案。

- `excludeOther`= 0x80000000 排除以上未列出的任何其他檔案類型。

- `excludeDefaultLoad`= 0 載入時, 預設會包含所有檔案類型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`針對儲存, 預設會排除這些檔案, 因為它們通常有特殊需求。

*chSeparator*<br/>
影像格式之間使用的分隔符號。 如需詳細資訊, 請參閱**備註**。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞至 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)物件, 以在 [**開啟**檔案] 對話方塊中公開可用影像格式的副檔名。

參數*strImporter*的格式如下:

file description0&#124; \*. ext0&#124;&#124;filedescription1\*. ext1&#124;.。。檔案描述*n* &#124; \*. ext *n*&#124;&#124;

其中 '&#124;' 是*chSeparator*所指定的分隔字元。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果您將此字串&#124;傳遞至 MFC `CFileDialog`物件, 請使用預設分隔符號 ' '。 如果您將此字串傳遞至通用的 [**開啟**檔案] 對話方塊, 請使用 null 分隔符號 ' \ 0 '。

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

抓取 color 資料表中的最大專案數。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>傳回值

Color 資料表中的專案數。

### <a name="remarks"></a>備註

這個方法只支援 DIB 區段點陣圖。

##  <a name="getpitch"></a>  CImage::GetPitch

抓取影像的音調。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>傳回值

影像的間距。 如果傳回值是負數, 表示點陣圖是底部的 DIB, 而其原點是左下角。 如果傳回值是正數, 則點陣圖是由上而下的 DIB, 而其原點是左上角。

### <a name="remarks"></a>備註

音調是兩個記憶體位址之間的距離 (以位元組為單位), 代表一個點陣圖行的開頭和下一個點陣圖行的開頭。 因為音調是以位元組為單位來測量, 所以影像的間距可協助您判斷像素格式。 音調也可以包含額外的記憶體, 為點陣圖保留。

使用`GetPitch` with [GetBits](#getbits)來尋找影像的個別圖元。

> [!NOTE]
> 這個方法只支援 DIB 區段點陣圖。

##  <a name="getpixel"></a>  CImage::GetPixel

抓取*x*和*y*所指定位置的圖元色彩。

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>參數

*x*<br/>
圖元的 x 座標。

*y*<br/>
圖元的 y 座標。

### <a name="return-value"></a>傳回值

圖元的紅色、綠色、藍色 (RGB) 值。 如果圖元位於目前的裁剪區域之外, 則傳回值為 CLR_INVALID。

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

抓取圖元的確切位址。

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
圖元的 x 座標。

*y*<br/>
圖元的 y 座標。

### <a name="remarks"></a>備註

位址是根據圖元的座標、點陣圖的間距以及每圖元的位數來決定。

對於每圖元小於8位的格式, 這個方法會傳回包含圖元的位元組位址。 例如, 如果您的影像格式每圖元有4個位, `GetPixelAddress`會傳回位元組中第一個圖元的位址, 而且您必須計算每個位元組2個圖元。

> [!NOTE]
> 這個方法只支援 DIB 區段點陣圖。

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

抓取色彩調色板中透明色彩的索引位置。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>傳回值

透明色彩的索引。

##  <a name="getwidth"></a>  CImage::GetWidth

抓取影像的寬度 (以圖元為單位)。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>傳回值

點陣圖的寬度 (以圖元為單位)。

##  <a name="isdibsection"></a>  CImage::IsDIBSection

判斷附加的點陣圖是否為 DIB 區段。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>傳回值

如果附加的點陣圖是 DIB 區段, 則為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

如果點陣圖不是 dib 區段, 您就無法使用下列`CImage`僅支援 dib 區段點陣圖的方法:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>CImage:: IsIndexed

決定點陣圖的圖元是否對應到調色板。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>傳回值

如果已編制索引, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

只有當點陣圖為8位 (256 色) 或更少時, 這個方法才會傳回 TRUE。

> [!NOTE]
> 這個方法只支援 DIB 區段點陣圖。

##  <a name="isnull"></a>  CImage::IsNull

判斷點陣圖目前是否已載入。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>備註

如果目前未載入點陣圖, 這個方法會傳回 TRUE;否則為 FALSE。

##  <a name="istransparencysupported"></a>CImage:: IsTransparencySupported

指出應用程式是否支援透明點陣圖。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>傳回值

如果目前平臺支援透明度, 則為非零。 否則為0。

### <a name="remarks"></a>備註

如果傳回值為非零, 而且支援透明度, 則[AlphaBlend](#alphablend)、 [TransparentBlt](#transparentblt)或[Draw](#draw)的呼叫將會處理透明色彩。

##  <a name="load"></a>CImage:: Load

載入影像。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pszFileName*<br/>
字串的指標, 其中包含要載入之影像檔案的名稱。

*pStream*<br/>
資料流程的指標, 其中包含要載入之影像檔案的名稱。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

載入*pszFileName*或*pStream*所指定的影像。

有效的影像類型為 BMP、GIF、JPEG、PNG 和 TIFF。

##  <a name="loadfromresource"></a>CImage:: LoadFromResource

從點陣圖資源載入影像。

```
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>參數

*hInstance*<br/>
包含要載入之影像的模組實例的控制碼。

*pszResourceName*<br/>
字串的指標, 其中包含包含要載入之影像的資源名稱。

*nIDResource*<br/>
要載入的資源識別碼。

### <a name="remarks"></a>備註

資源必須是點陣圖類型。

##  <a name="maskblt"></a>CImage:: MaskBlt

使用指定的遮罩和點陣運算, 結合來源與目的地點陣圖的色彩資料。

```
BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    HBITMAP hbmMask,
    int xMask,
    int yMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    HBITMAP hbmMask,
    const POINT& pointMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const POINT& pointDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>參數

*hDestDC*<br/>
模組的控制碼, 其可執行檔包含資源。

*xDest*<br/>
目的矩形左上角的 x 座標 (以邏輯單位表示)。

*yDest*<br/>
目的矩形左上角的 y 座標 (以邏輯單位表示)。

*nDestWidth*<br/>
目的地矩形和來源點陣圖的寬度 (以邏輯單位表示)。

*nDestHeight*<br/>
目的地矩形和來源點陣圖的高度 (以邏輯單位表示)。

*xSrc*<br/>
來源點陣圖左上角的邏輯 x 座標。

*ySrc*<br/>
來源點陣圖左上角的邏輯 y 座標。

*hbmMask*<br/>
單色遮罩點陣圖的控制碼, 與來源裝置內容中的色彩點陣圖結合。

*xMask*<br/>
*HbmMask*參數所指定之遮罩點陣圖的水準圖元位移。

*yMask*<br/>
*HbmMask*參數所指定之遮罩點陣圖的垂直圖元位移。

*dwROP*<br/>
指定方法用來控制來源與目的地資料組合的前景和背景三元點陣作業代碼。 背景點陣作業程式碼是以此值的高序位字組的高序位位元組來儲存。前景點陣作業程式碼會以此值的高序位單字的低序位位元組儲存。這個值的低序位字組會被忽略, 而且應該是零。 如需這個方法內容中前景和背景的討論, 請參閱`MaskBlt` Windows SDK 中的。 如需常見的點陣操作程式代碼清單, `BitBlt`請參閱 Windows SDK 中的。

*rectDest*<br/>
`RECT`結構的參考, 識別目的地。

*pointSrc*<br/>
`POINT`結構, 表示來源矩形的左上角。

*pointMask*<br/>
`POINT`結構, 表示遮罩點陣圖的左上角。

*pointDest*<br/>
`POINT`結構的參考, 識別目的矩形的左上角 (以邏輯單位表示)。

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 否則為0。

### <a name="remarks"></a>備註

此方法僅適用于 Windows NT (版本4.0 和更新版本)。

##  <a name="operator_hbitmap"></a>CImage:: operator HBITMAP

使用這個運算子取得`CImage`物件附加的 Windows GDI 控制碼。 這個運算子是一個轉型運算子, 可支援直接使用 HBITMAP 物件。

##  <a name="plgblt"></a>  CImage::PlgBlt

執行位區塊從來源裝置內容中的矩形傳送到目的地裝置內容中的平行四邊形。

```
BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    HBITMAP hbmMask = NULL,
    int xMask = 0,
    int yMask = 0) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    const RECT& rectSrc,
    HBITMAP hbmMask = NULL,
    const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>參數

*hDestDC*<br/>
目的地裝置內容的控制碼。

*pPoints*<br/>
邏輯空間中三個點之陣列的指標, 可識別目的地平行四邊形的三個角落。 來源矩形的左上角會對應至此陣列中的第一個點、此陣列中第二個點的右上角, 以及第三個點的左下角。 來源矩形的右下角會對應到平行四邊形中的隱含第四個點。

*hbmMask*<br/>
選擇性單色點陣圖的控制碼, 用來遮罩來源矩形的色彩。

*xSrc*<br/>
來源矩形左上角的 x 座標 (以邏輯單位表示)。

*ySrc*<br/>
來源矩形左上角的 y 座標 (以邏輯單位表示)。

*nSrcWidth*<br/>
來源矩形的寬度 (以邏輯單位表示)。

*nSrcHeight*<br/>
來源矩形的高度 (以邏輯單位表示)。

*xMask*<br/>
單色點陣圖左上角的 x 座標。

*yMask*<br/>
單色點陣圖左上角的 y 座標。

*rectSrc*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考, 指定來源矩形的座標。

*pointMask*<br/>
[點](/previous-versions/dd162805\(v=vs.85\))結構, 指出遮罩點陣圖的左上角。

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 否則為0。

### <a name="remarks"></a>備註

如果*hbmMask*識別有效的單色點陣圖, `PlgBit`會使用這個點陣圖來遮罩來源矩形的色彩資料位。

此方法僅適用于 Windows NT (版本4.0 和更新版本)。 如需詳細資訊, 請參閱 Windows SDK 中的[PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) 。

##  <a name="releasedc"></a>CImage:: ReleaseDC

釋放裝置內容。

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>備註

因為一次只能選取一個點陣圖到裝置內容中, 所以您必須呼叫`ReleaseDC` [GetDC](#getdc)的每個呼叫。

##  <a name="releasegdiplus"></a>CImage:: ReleaseGDIPlus

釋放 GDI + 所使用的資源。

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>備註

您必須呼叫這個方法, 才能釋放由全域`CImage`物件所配置的資源。 請參閱[CImage:: CImage](#cimage)。

##  <a name="save"></a>CImage:: Save

將影像儲存至指定的資料流程或磁片上的檔案。

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>參數

*pStream*<br/>
COM IStream 物件的指標, 其中包含檔案映射資料。

*pszFileName*<br/>
影像的檔案名指標。

*guidFileType*<br/>
要用來儲存影像的檔案類型。 可以是下列其中一項：

- `ImageFormatBMP`未壓縮的點陣圖影像。

- `ImageFormatPNG`可移植網狀圖形 (PNG) 壓縮的影像。

- `ImageFormatJPEG`JPEG 壓縮影像。

- `ImageFormatGIF`GIF 壓縮的影像。

> [!NOTE]
> 如需常數的完整清單, 請參閱 Windows SDK 中的**影像檔案格式常數**。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

呼叫此函式, 以使用指定的名稱和類型來儲存影像。 如果未包含*guidFileType*參數, 則會使用檔案名的副檔名來決定影像格式。 如果未提供任何副檔名, 則會以 BMP 格式儲存影像。

##  <a name="setcolortable"></a>  CImage::SetColorTable

設定 DIB 區段之調色板中某個專案範圍的紅色、綠色、藍色 (RGB) 色彩值。

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>參數

*iFirstColor*<br/>
要設定之第一個專案的色彩表索引。

*nColors*<br/>
要設定的色彩資料表專案數目。

*prgbColors*<br/>
要設定色彩資料表專案之[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)結構陣列的指標。

### <a name="remarks"></a>備註

這個方法只支援 DIB 區段點陣圖。

##  <a name="setpixel"></a>  CImage::SetPixel

在點陣圖中的指定位置設定圖元的色彩。

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
要設定之圖元的水準位置。

*y*<br/>
要設定之圖元的垂直位置。

*color*<br/>
您要設定圖元的色彩。

### <a name="remarks"></a>備註

如果圖元座標位於選取的裁剪區域之外, 這個方法就會失敗。

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

將圖元色彩設定為色彩調色板中位於*iIndex*的色彩。

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
要設定之圖元的水準位置。

*y*<br/>
要設定之圖元的垂直位置。

*iIndex*<br/>
色彩色板中色彩的索引。

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

在紅色、綠色、藍色 (RGB) 影像中, 將*x*和*y*指定之位置的圖元設定為*r*、 *g*和*b*所指示的色彩。

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
要設定之圖元的水準位置。

*y*<br/>
要設定之圖元的垂直位置。

*r*<br/>
紅色的濃度。

*g*<br/>
綠色色彩的濃度。

*b*<br/>
藍色的濃度。

### <a name="remarks"></a>備註

紅色、綠色和藍色參數分別以0到255之間的數位表示。 如果您將這三個參數全部設為零, 則結合產生的色彩會是黑色。 如果您將這三個參數全部設為 255, 則結合產生的色彩會是白色。

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

在指定的索引位置上, 將色彩設定為透明。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>參數

*iTransparentColor*<br/>
要設定為透明的色彩之色彩調色板中的索引。 如果為-1, 則不會將色彩設定為透明。

### <a name="return-value"></a>傳回值

先前設定為透明的色彩索引。

##  <a name="stretchblt"></a>  CImage::StretchBlt

將點陣圖從來源裝置內容複寫到這個目前的裝置內容。

```
BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>參數

*hDestDC*<br/>
目的地裝置內容的控制碼。

*xDest*<br/>
目的矩形左上角的 x 座標 (以邏輯單位表示)。

*yDest*<br/>
目的矩形左上角的 y 座標 (以邏輯單位表示)。

*nDestWidth*<br/>
目的地矩形的寬度 (以邏輯單位表示)。

*nDestHeight*<br/>
目的地矩形的高度 (以邏輯單位表示)。

*dwROP*<br/>
要執行的點陣運算。 「點陣操作代碼」定義了如何結合來源、目的地和模式 (如目前選取的筆刷所定義) 的位來形成目的地的確切方式。 如需其他點陣作業代碼及其描述的清單, 請參閱 Windows SDK 中的[BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 。

*rectDest*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考, 識別目的地。

*xSrc*<br/>
來源矩形左上角的 x 座標 (以邏輯單位表示)。

*ySrc*<br/>
來源矩形左上角的 y 座標 (以邏輯單位表示)。

*nSrcWidth*<br/>
來源矩形的寬度 (以邏輯單位表示)。

*nSrcHeight*<br/>
來源矩形的高度 (以邏輯單位表示)。

*rectSrc*<br/>
`RECT`結構的參考, 識別來源。

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 否則為0。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) 。

##  <a name="transparentblt"></a>CImage:: TransparentBlt

將點陣圖從來源裝置內容複寫到這個目前的裝置內容。

```
BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>參數

*hDestDC*<br/>
目的地裝置內容的控制碼。

*xDest*<br/>
目的矩形左上角的 x 座標 (以邏輯單位表示)。

*yDest*<br/>
目的矩形左上角的 y 座標 (以邏輯單位表示)。

*nDestWidth*<br/>
目的地矩形的寬度 (以邏輯單位表示)。

*nDestHeight*<br/>
目的地矩形的高度 (以邏輯單位表示)。

*crTransparent*<br/>
來源點陣圖中要視為透明的色彩。 根據預設, CLR_INVALID, 表示應該使用目前設定為影像之透明色彩的色彩。

*rectDest*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考, 識別目的地。

*xSrc*<br/>
來源矩形左上角的 x 座標 (以邏輯單位表示)。

*ySrc*<br/>
來源矩形左上角的 y 座標 (以邏輯單位表示)。

*nSrcWidth*<br/>
來源矩形的寬度 (以邏輯單位表示)。

*nSrcHeight*<br/>
來源矩形的高度 (以邏輯單位表示)。

*rectSrc*<br/>
`RECT`結構的參考, 識別來源。

### <a name="return-value"></a>傳回值

如果成功, 則為 TRUE, 否則為 FALSE。

### <a name="remarks"></a>備註

`TransparentBlt`支援每圖元4個位的來源點陣圖和每圖元8位。 使用[CImage:: AlphaBlend](#alphablend)以透明方式指定32位的每圖元點陣圖。

### <a name="example"></a>範例

```cpp
// Performs a transparent blit from the source image to the destination
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage,
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```

## <a name="see-also"></a>另請參閱

[MMXSwarm 範例](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage 範例](../../overview/visual-cpp-samples.md)<br/>
[與裝置無關的點陣圖](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[與裝置無關的點陣圖](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
