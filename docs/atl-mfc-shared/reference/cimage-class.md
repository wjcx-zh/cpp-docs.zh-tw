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
ms.openlocfilehash: a6d20e1bf12f5fe7d1e9b41d88b088ca9fad35ed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747175"
---
# <a name="cimage-class"></a>CImage 類別

`CImage`提供增強的位圖支援,包括以 JPEG、GIF、BMP 和便攜式網路圖形 (PNG) 格式載入和保存影像的能力。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CImage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CImage:CImage](#cimage)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[圖片::阿爾法布林](#alphablend)|顯示具有透明或半透明圖元的位圖。|
|[CImage::附加](#attach)|將 HBITMAP`CImage`附加到 物件。 可用於非 DIB 截面位圖或 DIB 部分位圖。|
|[圖片::比特布拉特](#bitblt)|將點陣圖從源裝置上下文複製到此當前設備上下文。|
|[CImage:建立](#create)|創建 DIB 剖面位圖並將其附加到以前`CImage`構造 的物件。|
|[圖片::建立Ex](#createex)|創建 DIB 截面位圖(包含其他參數),並將其附加到以前`CImage`構造 的物件。|
|[圖片::D](#destroy)|從`CImage`物件分離位圖並銷毀點陣圖。|
|[圖片::D](#detach)|從`CImage`物件分離位圖。|
|[C圖像::D原](#draw)|將點陣圖從源矩形複製到目標矩形中。 `Draw`如有必要,拉伸或壓縮位圖以適合目標矩形的尺寸,並處理 Alpha 混合和透明顏色。|
|[CImage:抓取位](#getbits)|檢索指向位圖的實際像素值的指標。|
|[圖片::GetBPP](#getbpp)|檢索每像素的位。|
|[CImage:取得顏色表](#getcolortable)|從顏色表中的一系列條目中檢索紅色、綠色、藍色 (RGB) 顏色值。|
|[CImage:GetDC](#getdc)|檢索選擇當前位圖的設備上下文。|
|[CImage::取得匯出器篩選器字串](#getexporterfilterstring)|尋找可用的影像格式及其說明。|
|[CImage:取得高度](#getheight)|檢索當前圖像的高度(以像素為單位)。|
|[CImage:取得匯入篩選器字串](#getimporterfilterstring)|尋找可用的影像格式及其說明。|
|[CImage:取得最大顏色表條目](#getmaxcolortableentries)|檢索顏色表中的最大條目數。|
|[圖片::取得投球](#getpitch)|檢索當前圖像的間距(以位元組為單位)。|
|[CImage:抓取像素](#getpixel)|檢索*x*和*y*指定的像素的顏色。|
|[CImage:抓取像素位址](#getpixeladdress)|檢索給定像素的位址。|
|[CImage:抓取透明顏色](#gettransparentcolor)|檢索透明顏色在顏色表中的位置。|
|[CImage:取得寬度](#getwidth)|檢索當前圖像的寬度(以像素為單位)。|
|[圖片::IsDIB節](#isdibsection)|確定附加點陣圖是否為 DIB 部分。|
|[CImage:已編制索引](#isindexed)|指示點陣圖的顏色映射到索引調色板。|
|[C影像::IsNull](#isnull)|指示當前是否載入源點圖。|
|[CImage:是支援透明度的](#istransparencysupported)|指示應用程式是否支援透明位圖。|
|[CImage:載入](#load)|從指定的檔載入影像。|
|[CImage::從資源載入](#loadfromresource)|從指定資源載入影像。|
|[圖片::面具](#maskblt)|使用指定的蒙版和閘格操作組合源和目標位圖的顏色數據。|
|[圖片::PlgBlt](#plgblt)|在目標設備上下文中執行從源設備上下文中的矩形到並行四字形的位塊傳輸。|
|[CImage:釋放DC](#releasedc)|釋放使用 CImage 檢索的裝置內容內容[內容 ::GetDC](#getdc)。|
|[CImage::發佈GDIPlus](#releasegdiplus)|釋放 GDI+ 使用的資源。 必須調用以釋放由全域`CImage`對象創建的資源。|
|[CImage::儲存](#save)|將圖像保存為指定類型。 `Save`無法指定圖像選項。|
|[CImage:設定顏色表](#setcolortable)|在 DIB 部分的顏色表中的一系列條目中設置紅色、綠色、藍色 RGB 顏色值。|
|[CImage:設定像素](#setpixel)|將指定座標上的像素設定為指定顏色。|
|[CImage::設定像素索引](#setpixelindexed)|將指定座標處的圖元設置到調色板指定索引處的顏色。|
|[CImage:SetPixelRGB](#setpixelrgb)|將指定座標處的圖元設置為指定的紅色、綠色、藍色 (RGB) 值。|
|[CImage::設定透明色](#settransparentcolor)|設置要被視為透明的顏色的索引。 調色板中只有一種顏色是透明的。|
|[C影像:拉伸Blt](#stretchblt)|將點陣圖從源矩形複製到目標矩形中,根據需要拉伸或壓縮位圖以適合目標矩形的尺寸。|
|[圖片::透明布拉特](#transparentblt)|將具有透明顏色的位圖從源裝置上下文複製到此當前設備上下文。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CImage::操作員 HBITMAP](#operator_hbitmap)|返回附加到`CImage`物件的 Windows 句柄。|

## <a name="remarks"></a>備註

`CImage`獲取與設備無關的位圖 (DIB) 部分或不採用位圖;但是,您可以使用[「創建](#create)」或[「CImage::"](#load)僅使用 DIB 部分載入。 可以使用 Attach 將非 DIB`CImage`節位[Attach](#attach)圖 附加到物件`CImage`,但不能使用以下 方法,這些方法僅支援 DIB 節位圖:

- [取得位](#getbits)

- [取得顏色表](#getcolortable)

- [取得最大顏色表條目](#getmaxcolortableentries)

- [取得間距](#getpitch)

- [取得像素位址](#getpixeladdress)

- [IsIndexed](#isindexed)

- [設定顏色表](#setcolortable)

要確定附加點陣圖是否為 DIB 部分,請致電[IsDibSection](#isdibsection)。

> [!NOTE]
> 在 Visual Studio .NET 2003`CImage`中,此類保留創建的物件數的計數。 每當計數達到 0 時,將`GdiplusShutdown`自動調用函數以釋放 GDI+使用的資源。 這可確保由`CImage`DLL 直接或間接創建的任何物件始終被正確銷`GdiplusShutdown`毀,`DllMain`並且不會從調用。

> [!NOTE]
> 不建議`CImage`在 DLL 中使用全域物件。 如果需要在 DLL`CImage`中使用 全域物件,請致電[CImage::ReleaseGDIPlus](#releasegdiplus)以顯式釋放 GDI+使用的資源。

`CImage`無法選擇到新的[CDC](../../mfc/reference/cdc-class.md)中。 `CImage`為映射創建自己的 HDC。 由於 HBITMAP 一次只能選擇到一個 HDC 中,`CImage`因此無法將與 HBITMAP 關聯的 HBITMAP 選入另一個 HDC。 如果需要 CDC,請從 中檢索`CImage`HDC 並將其交給[CDC::fromHandle](../../mfc/reference/cdc-class.md#fromhandle)。

## <a name="example"></a>範例

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

在 MFC 專案`CImage`中使用 時,請注意專案中的哪個成員函數需要指向[CBitmap](../../mfc/reference/cbitmap-class.md)物件的指標。 如果要將此類函數(`CImage`如[CMenu::AppendMenu)](../../mfc/reference/cmenu-class.md#appendmenu)用於, 請使用[CBitmap::FromHandle,](../../mfc/reference/cbitmap-class.md#fromhandle)將其傳遞為`CImage`HBITMAP,並使用傳回`CBitmap*`的 。

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

通過`CImage`,您可以造訪 DIB 部分的實際位。 您可以在以前使用`CImage`Win32 HBITMAP 或 DIB 部分的任何位置使用物件。

您可以使用`CImage`MFC 或 ATL。

> [!NOTE]
> 使用`CImage`創建項目時,必須先在`CString`包含*atlimage.h*之前進行定義。 如果您的項目使用沒有 MFC 的 ATL,請在包含*atlimage.h*之前包括*atlstr.h。* 如果您的專案使用 MFC(或者它是支援 MFC 的 ATL 專案),請在包含*atlimage.h*之前包括*afxstr.h。*<br/>
> <br/>
> 同樣,在包含*atlimpl.cpp*之前,您必須包括*atlimage.h。* 要輕鬆完成此目的,請在*pch.h*中包括*atlimage.h(Visual* Studio 2017 及更早版本中的*stdafx.h)。*

## <a name="requirements"></a>需求

**標題:** atlimage.h

## <a name="cimagealphablend"></a><a name="alphablend"></a>圖片::阿爾法布林

顯示具有透明或半透明圖元的位圖。

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
處理目標設備上下文。

*xDest*<br/>
以邏輯單位表示目標矩形左上角的 x 座標。

*yDest*<br/>
以邏輯單位表示目標矩形左上角的 y 座標。

*bSrcAlpha*<br/>
要在整個源位圖上使用的 Alpha 透明度值。 預設 0xff (255) 假定圖像不透明,並且只想使用每圖元 alpha 值。

*bBlendOp*<br/>
源點圖和目標位圖的 Alpha 混合函數、要應用於整個來源位圖的全域 Alpha 值以及來源位圖的格式資訊。 源和目標混合函數目前僅限於AC_SRC_OVER。

*點 Dest*<br/>
對[POINT](/windows/win32/api/windef/ns-windef-point)結構的引用,該結構以邏輯單位標識目標矩形的左上角。

*nD最大寬度*<br/>
目標矩形的寬度(以邏輯單位為單位)。

*nDestHeight*<br/>
目標矩形的高度(以邏輯單位為單位)。

*xSrc*<br/>
源矩形左上角的邏輯 x 座標。

*伊斯爾克*<br/>
源矩形左上角的邏輯 y 座標。

*NSrcWidth*<br/>
源矩形的寬度(以邏輯單位為單位)。

*nSrcHeight*<br/>
源矩形的高度(以邏輯單位為單位)。

*整流*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,標識目標。

*雷克斯爾*<br/>
對結構的`RECT`引用,標識源。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

Alpha 混合點陣圖支援按像素進行顏色混合。

當*bBlendOp*設置為預設AC_SRC_OVER時,源點圖將根據源圖元的 alpha 值放置在目標位圖上。

## <a name="cimageattach"></a><a name="attach"></a>CImage::附加

將*hBitmap*`CImage`附加到物件。

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
HBITMAP 的句柄。

*e方向*<br/>
指定點陣圖的方向。 可以是下列其中一項：

- DIBOR_DEFAULT位圖的方向由操作系統確定。

- DIBOR_BOTTOMUP 位圖的行順序相反。 這將導致[CImage:getBits](#getbits)返回位圖緩衝區末尾附近的指標[,CImage:GetPitch](#getpitch)返回負數。

- DIBOR_TOPDOWN 位圖的行按從上到下的順序排列。 這會導致[CImage:getBits](#getbits)返回指向位圖緩衝區的第一個字節的指標[,CImage:getPitch](#getpitch)返回正數。

### <a name="remarks"></a>備註

位圖可以是非 DIB 部分位圖或 DIB 部分位圖。 有關只能對 DIB 部分位圖使用的方法清單,請參閱[IsDIBSection。](#isdibsection)

## <a name="cimagebitblt"></a><a name="bitblt"></a>圖片::比特布拉特

將點陣圖從源裝置上下文複製到此當前設備上下文。

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
目標 HDC。

*xDest*<br/>
目標矩形左上角的邏輯 x 座標。

*yDest*<br/>
目標矩形左上角的邏輯 y 座標。

*德沃羅普*<br/>
要執行的柵格操作。 柵格操作代碼精確定義如何組合源、目標和模式(由當前選擇的畫筆定義)以形成目標。 有關其他柵格操作代碼及其說明的清單,請參閱 Windows SDK 中的[BitBlt。](/windows/win32/api/wingdi/nf-wingdi-bitblt)

*點 Dest*<br/>
指示目標矩形左上角的[POINT](/windows/win32/api/windef/ns-windef-point)結構。

*nD最大寬度*<br/>
目標矩形的寬度(以邏輯單位為單位)。

*nDestHeight*<br/>
目標矩形的高度(以邏輯單位為單位)。

*xSrc*<br/>
源矩形左上角的邏輯 x 座標。

*伊斯爾克*<br/>
源矩形左上角的邏輯 y 座標。

*整流*<br/>
指示目標矩形的[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*點Src*<br/>
指示`POINT`源矩形左上角的結構。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[BitBlt。](/windows/win32/api/wingdi/nf-wingdi-bitblt)

## <a name="cimagecimage"></a><a name="cimage"></a>CImage:CImage

建構 `CImage` 物件。

```
CImage() throw();
```

### <a name="remarks"></a>備註

建構物件後,呼叫["創建](#create)、[載入](#load)、[載入資源](#loadfromresource)"或['附加](#attach)"以將位圖附加到物件。

**注意**在 Visual Studio 中,此類保留`CImage`所創建物件 數的計數。 每當計數達到 0 時,將`GdiplusShutdown`自動調用函數以釋放 GDI+使用的資源。 這可確保由`CImage`DLL 直接或間接創建的任何物件始終被正確銷`GdiplusShutdown`毀, 並且不會從 DllMain 調用。

不建議`CImage`在 DLL 中使用全域物件。 如果需要在 DLL`CImage`中使用 全域物件,請致電[CImage::ReleaseGDIPlus](#releasegdiplus)以顯式釋放 GDI+使用的資源。

## <a name="cimagecreate"></a><a name="create"></a>CImage:建立

創建`CImage`位圖並將其附加到以前建構`CImage`的物件。

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*n 寬度*<br/>
位圖的`CImage`寬度(以像素為單位)。

*nHeight*<br/>
`CImage`位圖的高度(以像素為單位)。 如果*nHeight*為正,則位圖是自下而上的 DIB,其原點是左下角。 如果*nHeight*為負數,則位圖是自上而下的 DIB,其原點是左上角。

*nBPP*<br/>
位圖中每像素的位數。 通常為 4、8、16、24 或 32。 可以是 1 用於單色位圖或蒙版。

*dwFlags*<br/>
指定點陣圖物件是否具有 Alpha 通道。 可以是以下零個或多個值的組合:

- *建立 Alpha 通道*僅當*nBPP*為 32 且*e 壓縮*是BI_RGB時才能使用。 如果指定,則創建的圖像具有每個圖元的 Alpha(透明度)值,存儲在每個圖元的第 4 個字節中(在非 Alpha 32 位圖像中未使用)。 此 Alpha 通道在調用[CImage::AlphaBlend](#alphablend)時會自動使用。

> [!NOTE]
> 在調用[CImage::Draw](#draw)中,具有 Alpha 通道的圖像會自動與目標混合 Alpha。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="cimagecreateex"></a><a name="createex"></a>圖片::建立Ex

創建`CImage`位圖並將其附加到以前建構`CImage`的物件。

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

*n 寬度*<br/>
位圖的`CImage`寬度(以像素為單位)。

*nHeight*<br/>
`CImage`位圖的高度(以像素為單位)。 如果*nHeight*為正,則位圖是自下而上的 DIB,其原點是左下角。 如果*nHeight*為負數,則位圖是自上而下的 DIB,其原點是左上角。

*nBPP*<br/>
位圖中每像素的位數。 通常為 4、8、16、24 或 32。 可以是 1 用於單色位圖或蒙版。

*電子壓縮*<br/>
指定壓縮自下而上位圖的壓縮類型(無法壓縮自上而下的 DIB)。 可以是下列其中一個值：

- BI_RGB格式未壓縮。 呼叫`CImage::CreateEx`時指定此值等效於呼`CImage::Create`叫 。

- BI_BITFIELDS 格式未壓縮,顏色表由三個 DWORD 顏色蒙版組成,分別指定每個圖元的紅色、綠色和藍色分量。 當與 16 和 32 bpp 位圖一起使用時,這一點有效。

*pdwBitfields*<br/>
僅當*e 壓縮*設定為BI_BITFIELDS時才使用,否則必須為 NULL。 指向三個 DWORD 位掩碼陣列的指標,分別指定每個畫素的哪些位分別用於顏色的紅色、綠色和藍色分量。 有關位欄位限制的資訊,請參閱 Windows SDK 中的[BITMAPINFOHEADER。](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader)

*dwFlags*<br/>
指定點陣圖物件是否具有 Alpha 通道。 可以是以下零個或多個值的組合:

- *建立 Alpha 通道*僅當*nBPP*為 32 且*e 壓縮*是BI_RGB時才能使用。 如果指定,則創建的圖像具有每個圖元的 Alpha(透明度)值,存儲在每個圖元的第 4 個字節中(在非 Alpha 32 位圖像中未使用)。 此 Alpha 通道在調用[CImage::AlphaBlend](#alphablend)時會自動使用。

   > [!NOTE]
   > 在調用[CImage::Draw](#draw)中,具有 Alpha 通道的圖像會自動與目標混合 Alpha。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE。 否則,FALSE。

### <a name="example"></a>範例

下面的範例創建一個 100x100 像素位圖,使用 16 位元對每個像素進行編碼。 在給定的 16 位圖元中,位 0-3 對紅色分量進行編碼,位 4-7 編碼綠色,位 8-11 編碼藍色。 其餘4位未使用。

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>圖片::D

從`CImage`物件分離位圖並銷毀點陣圖。

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>圖片::D

從`CImage`物件分離位圖。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>傳回值

已分離位圖的句柄,如果沒有附加位圖,則為 NULL。

## <a name="cimagedraw"></a><a name="draw"></a>C圖像::D原

將點陣圖從源裝置上下文複製到當前設備上下文。

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
目標設備上下文的句柄。

*xDest*<br/>
以邏輯單位表示目標矩形左上角的 x 座標。

*yDest*<br/>
以邏輯單位表示目標矩形左上角的 y 座標。

*nD最大寬度*<br/>
目標矩形的寬度(以邏輯單位為單位)。

*nDestHeight*<br/>
目標矩形的高度(以邏輯單位為單位)。

*xSrc*<br/>
源矩形左上角的 x 座標(以邏輯單位為單位)。

*伊斯爾克*<br/>
源矩形左上角的 y 座標(以邏輯單位為單位)。

*NSrcWidth*<br/>
源矩形的寬度(以邏輯單位為單位)。

*nSrcHeight*<br/>
源矩形的高度(以邏輯單位為單位)。

*整流*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,標識目標。

*雷克斯爾*<br/>
對結構的`RECT`引用,標識源。

*點 Dest*<br/>
對[POINT](/windows/win32/api/windef/ns-windef-point)結構的引用,該結構以邏輯單位標識目標矩形的左上角。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Draw`執行與[拉伸 Blt](#stretchblt)相同的操作,除非圖像包含透明顏色或 Alpha 通道。 在這種情況下,`Draw`根據需要執行與[透明 Blt](#transparentblt)或[AlphaBlend](#alphablend)相同的操作。

對於不指定`Draw`源矩形的版本,整個源圖像為預設值。 對於未指定目標`Draw`矩形大小的版本,源圖像的大小為預設值,並且不會發生拉伸或收縮。

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage:抓取位

檢索指向位圖中給定像素的實際位值的指標。

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>傳回值

指向位圖緩衝區的指標。 如果位圖是自下而上的 DIB,指標指向緩衝區末端附近。 如果位圖是自上而下的 DIB,指標將指向緩衝區的第一個字節。

### <a name="remarks"></a>備註

使用此指標,以及[GetPitch](#getpitch)返回的值,可以定位和更改圖像中的單個圖元。

> [!NOTE]
> 此方法僅支援 DIB 部分位圖;此方法僅支援 DIB 部分位圖。因此,訪問`CImage`物件的圖元的方式與 DIB 部分的圖元相同。 返回的指標指向位置 (0, 0) 處的圖元。

## <a name="cimagegetbpp"></a><a name="getbpp"></a>圖片::GetBPP

檢索每像素位值。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>傳回值

每像素的位數。

### <a name="remarks"></a>備註

此值確定定義每個像素的位數和位圖中的最大顏色數。

每像素的位數通常為1、4、8、16、24或32。 有關此值`biBitCount`的詳細資訊,請參閱 Windows SDK 中的[BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader)成員。

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage:取得顏色表

從 DIB 部分的調色板中的一系列條目中檢索紅色、綠色、藍色 (RGB) 顏色值。

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>參數

*i第一顏色*<br/>
要檢索的第一個條目的顏色表索引。

*n 顏色*<br/>
要檢索的顏色表條目數。

*普爾格顏色*<br/>
指向[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)結構陣列的指標,用於檢索顏色表條目。

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage:GetDC

檢索當前已選擇圖像的設備上下文。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>傳回值

裝置內容的控制代碼。

### <a name="remarks"></a>備註

對於對`GetDC`的每個調用 ,您必須對[ReleaseDC](#releasedc)進行後續調用。

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::取得匯出器篩選器字串

尋找可用於保存影像的影像格式。

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>參數

*斯特輸出*<br/>
`CSimpleString` 物件的參考。 有關詳細資訊,請參閱**備註**。

*阿吉德檔案類型*<br/>
一個 GUID 數位,每個元素對應於字串中的一個文件類型。 在下面的*pszAllFiles 描述*中的範例*中,aguidFileType*[0] GUID_NULL,其餘陣列是當前作業系統支援的影像檔格式。

> [!NOTE]
> 關於常數的完整清單,請參閱 Windows SDK 中**的影像檔案格式常量**。

*pszAll檔案描述*<br/>
如果此參數不是 NULL,則篩選器字串將在清單的開頭有一個額外的篩選器。 此篩選器將具有*pszAllFiles 描述*的當前值,並接受清單中任何其他匯出者支援的任何擴展檔。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
指定要從清單中排除的檔案類型的位標誌集。 允許的標誌包括:

- `excludeGIF`= 0x01 排除 GIF 檔。

- `excludeBMP`• 0x02 排除 BMP(Windows 位圖)檔。

- `excludeEMF`• 0x04 排除 EMF(增強型元檔)檔。

- `excludeWMF`• 0x08 排除 WMF(Windows 元檔)檔。

- `excludeJPEG`• 0x10 排除 JPEG 檔。

- `excludePNG`= 0x20 排除 PNG 檔。

- `excludeTIFF`• 0x40 排除 TIFF 檔。

- `excludeIcon`• 0x80 排除 ICO(Windows 圖示)檔。

- `excludeOther`= 0x8000000 排除上面未列出的任何其他文件類型。

- `excludeDefaultLoad`= 0 匯入,預設使用所有檔案類型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`對於保存,默認情況下排除這些文件,因為它們通常具有特殊要求。

*chseparator*<br/>
在影像格式之間使用的分隔符。 有關詳細資訊,請參閱**備註**。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞給 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)物件,以在「檔案儲存為」對話框中公開可用影像格式的檔案副檔名。

參數*str 匯出*具有以下格式:

檔案描述0 \*&#124;.ext0&#124;文件\*描述1&#124;.ext1&#124;...檔案描述*n* \*n&#124;.ext *n*&#124;&#124;

其中「&#124;」是指定的`chSeparator`分隔符。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果將此字串傳遞給 MFC`CFileDialog`物件,請使用預設分隔符「&#124;」。。 如果將此字串傳遞給公共檔案保存對話框,請使用空分隔符"\0"。

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage:取得高度

檢索圖像的高度(以像素為單位)。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>傳回值

圖像的高度(以像素為單位)。

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage:取得匯入篩選器字串

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

*串進口商*<br/>
`CSimpleString` 物件的參考。 有關詳細資訊,請參閱**備註**。

*阿吉德檔案類型*<br/>
一個 GUID 數位,每個元素對應於字串中的一個文件類型。 在下面的*pszAllFiles 描述*中的範例中 *,aguidFileType[0]* GUID_NULL,其餘陣列是目前作業系統支援的影像檔格式。

> [!NOTE]
> 關於常數的完整清單,請參閱 Windows SDK 中**的影像檔案格式常量**。

*pszAll檔案描述*<br/>
如果此參數不是 NULL,則篩選器字串將在清單的開頭有一個額外的篩選器。 此篩選器將具有*pszAllFiles 描述*的當前值,並接受清單中任何其他匯出者支援的任何擴展檔。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
指定要從清單中排除的檔案類型的位標誌集。 允許的標誌包括:

- `excludeGIF`= 0x01 排除 GIF 檔。

- `excludeBMP`• 0x02 排除 BMP(Windows 位圖)檔。

- `excludeEMF`• 0x04 排除 EMF(增強型元檔)檔。

- `excludeWMF`• 0x08 排除 WMF(Windows 元檔)檔。

- `excludeJPEG`• 0x10 排除 JPEG 檔。

- `excludePNG`= 0x20 排除 PNG 檔。

- `excludeTIFF`• 0x40 排除 TIFF 檔。

- `excludeIcon`• 0x80 排除 ICO(Windows 圖示)檔。

- `excludeOther`= 0x8000000 排除上面未列出的任何其他文件類型。

- `excludeDefaultLoad`= 0 匯入,預設使用所有檔案類型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`對於保存,默認情況下排除這些文件,因為它們通常具有特殊要求。

*chseparator*<br/>
在影像格式之間使用的分隔符。 有關詳細資訊,請參閱**備註**。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞給 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)物件,以在 **「檔案開啟」** 對話框中公開可用影像格式的檔案副檔名。

參數*str 匯入*器格式為:

檔案描述0 \*&#124;.ext0&#124;文件\*描述1&#124;.ext1&#124;...檔案描述*n* \*n&#124;.ext *n*&#124;&#124;

其中「&#124;」是*chSeparor*指定的分隔符。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果將此字串傳遞給 MFC`CFileDialog`物件,請使用預設分隔符「&#124;」。。 如果將此字串傳遞給公共**檔案打開**對話框,請使用空分隔符"\0"。

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage:取得最大顏色表條目

檢索顏色表中的最大條目數。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>傳回值

顏色表中的項目數。

### <a name="remarks"></a>備註

此方法僅支援 DIB 部分位圖。

## <a name="cimagegetpitch"></a><a name="getpitch"></a>圖片::取得投球

檢索圖像的間距。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>傳回值

圖像的間距。 如果返回值為負,則位圖是自下而上的 DIB,其原點是左下角。 如果返回值為正,則位圖是自上而下的 DIB,其原點是左上角。

### <a name="remarks"></a>備註

間距是兩個記憶體地址之間的距離(以位元組為單位)表示一個位圖線的開頭和下一位圖線的開頭。 由於間距以位元組為單位測量,因此圖像的間距可説明您確定圖元格式。 音高還可以包括額外的記憶體,為位圖保留。

與`GetPitch` [GetBits](#getbits)一起查找圖像的單個圖元。

> [!NOTE]
> 此方法僅支援 DIB 部分位圖。

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage:抓取像素

檢索*x*和*y*指定的位置的像素顏色。

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>參數

*x*<br/>
像素的 x 座標。

*Y*<br/>
圖元的 y 座標。

### <a name="return-value"></a>傳回值

圖元的紅色、綠色、藍色 (RGB) 值。 如果圖元在當前剪切區域之外,則返回值CLR_INVALID。

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage:抓取像素位址

檢索像素的確切位址。

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
像素的 x 座標。

*Y*<br/>
圖元的 y 座標。

### <a name="remarks"></a>備註

位址根據圖元的座標、位圖的間距和每圖元的位確定。

對於每圖元小於 8 位元的格式,此方法傳回包含圖元的位元組的位址。 例如,如果圖像格式為每圖元 4`GetPixelAddress`位元,請返回位元組中第一個圖元的位址,並且必須計算每個位元 2 個畫素。

> [!NOTE]
> 此方法僅支援 DIB 部分位圖。

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage:抓取透明顏色

檢索調色板中透明顏色的索引位置。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>傳回值

透明顏色的索引。

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage:取得寬度

檢索圖像的寬度(以像素為單位)。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>傳回值

位圖的寬度(以像素為單位)。

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>圖片::IsDIB節

確定附加點陣圖是否為 DIB 部分。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>傳回值

如果附加的位圖是 DIB 部分,則為 TRUE。 否則,FALSE。

### <a name="remarks"></a>備註

如果點陣圖不是 DIB 部分,則`CImage`無法使用以下 僅支援 DIB 部份位圖的方法:

- [取得位](#getbits)

- [取得顏色表](#getcolortable)

- [取得最大顏色表條目](#getmaxcolortableentries)

- [取得間距](#getpitch)

- [取得像素位址](#getpixeladdress)

- [IsIndexed](#isindexed)

- [設定顏色表](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage:已編制索引

確定位圖的圖元是否映射到調色板。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>傳回值

如果已編制索引,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

僅當位圖為 8 位(256 種顏色)或更少時,此方法才返回 TRUE。

> [!NOTE]
> 此方法僅支援 DIB 部分位圖。

## <a name="cimageisnull"></a><a name="isnull"></a>C影像::IsNull

確定當前是否載入點陣圖。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>備註

如果當前未載入位圖,則此方法返回 TRUE;如果當前未載入位圖,則此方法將返回 TRUE。否則 FALSE。

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage:是支援透明度的

指示應用程式是否支援透明位圖。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>傳回值

如果當前平臺支援透明度,則非零。 否則為 0。

### <a name="remarks"></a>備註

如果返回值是非零且支援透明度,則調用[AlphaBlend、](#alphablend)[透明 Blt](#transparentblt)或[Draw](#draw)將處理透明顏色。

## <a name="cimageload"></a><a name="load"></a>CImage:載入

載入影像。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pszFileName*<br/>
指向要載入的影像檔名稱的字串的指標。

*pStream*<br/>
指向要載入的影像檔名稱的流的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

載入*pszFileName*或*pStream*指定的影像。

有效圖像類型為 BMP、GIF、JPEG、PNG 和 TIFF。

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::從資源載入

從 BITMAP 資源載入映射。

```cpp
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>參數

*hInstance*<br/>
處理包含要載入的映像的模組實例。

*psz 資源名稱*<br/>
指向包含要載入的映像的資源名稱的字串的指標。

*nID資源*<br/>
要載入的資源 ID。

### <a name="remarks"></a>備註

資源必須為 BITMAP 類型。

## <a name="cimagemaskblt"></a><a name="maskblt"></a>圖片::面具

使用指定的蒙版和閘格操作組合源和目標位圖的顏色數據。

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
可執行檔包含資源的模組的句柄。

*xDest*<br/>
以邏輯單位表示目標矩形左上角的 x 座標。

*yDest*<br/>
以邏輯單位表示目標矩形左上角的 y 座標。

*nD最大寬度*<br/>
目標矩形和源位圖的寬度(以邏輯單位為單位)。

*nDestHeight*<br/>
目標矩形和源位圖的高度(以邏輯單位為單位)。

*xSrc*<br/>
源點陣圖左上角的邏輯 x 座標。

*伊斯爾克*<br/>
源點陣圖左上角的邏輯 y 座標。

*hbmMask*<br/>
處理單色蒙版位圖與源設備上下文中的顏色位圖結合使用。

*x蒙斯*<br/>
*hbmMask*參數指定的蒙版點陣圖的水準圖元偏移量。

*yMask*<br/>
*hbmMask*參數指定的蒙版點陣圖的垂直圖元偏移量。

*德沃羅普*<br/>
指定該方法用於控制源和目標數據組合的前景和後台三元柵格操作代碼。 後台柵格操作代碼存儲在此值的高階字的高階位元組中;前景柵格操作代碼存儲在此值的高階字的低階位元組中;此值的低階字將被忽略,並且應為零。 有關此方法上下文中的前景和背景的討論,請參閱`MaskBlt`Windows SDK。 有關常見柵格操作代碼的清單,請參閱`BitBlt`Windows SDK。

*整流*<br/>
對結構的`RECT`引用,標識目標。

*點Src*<br/>
指示`POINT`源矩形左上角的結構。

*點遮罩*<br/>
指示`POINT`蒙版點陣左上角的結構。

*點 Dest*<br/>
對以邏輯單位`POINT`標識目標矩形左上角的結構的引用。

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為 0。

### <a name="remarks"></a>備註

此方法僅適用於 Windows NT,版本 4.0 及更高版本。

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::操作員 HBITMAP

使用此運算元獲取`CImage`物件的附加 Windows GDI 句柄。 此運算子是強制轉換運算符,支援直接使用 HBITMAP 物件。

## <a name="cimageplgblt"></a><a name="plgblt"></a>圖片::PlgBlt

在目標設備上下文中執行從源設備上下文中的矩形到並行四字形的位塊傳輸。

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
目標設備上下文的句柄。

*pPoints*<br/>
指向邏輯空間中三個點的陣列的指標,用於標識目標平行四邊形的三個角。 源矩形的左上角映射到此陣列中的第一個點,右上角映射到此陣列中的第二個點,左下角映射到第三個點。 源矩形的右下角映射到平行四邊形中的隱式第四點。

*hbmMask*<br/>
用於遮蓋源矩形顏色的可選單色位圖的句柄。

*xSrc*<br/>
源矩形左上角的 x 座標(以邏輯單位為單位)。

*伊斯爾克*<br/>
源矩形左上角的 y 座標(以邏輯單位為單位)。

*NSrcWidth*<br/>
源矩形的寬度(以邏輯單位為單位)。

*nSrcHeight*<br/>
源矩形的高度(以邏輯單位為單位)。

*x蒙斯*<br/>
單色點圖左上角的 x 座標。

*yMask*<br/>
單色點圖左上角的 y 座標。

*雷克斯爾*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,指定源矩形的座標。

*點遮罩*<br/>
指示蒙版點陣左上角的[POINT](/windows/win32/api/windef/ns-windef-point)結構。

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為 0。

### <a name="remarks"></a>備註

如果*hbmMask*識別了有效的單色位`PlgBit`圖, 則使用此位圖來遮蓋源矩形中的顏色數據位。

此方法僅適用於 Windows NT,版本 4.0 及更高版本。 有關詳細資訊,請參閱 Windows SDK 中的[PlgBlt。](/windows/win32/api/wingdi/nf-wingdi-plgblt)

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage:釋放DC

釋放設備上下文。

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>備註

由於一次只能選擇一個位圖到設備上下文中,因此必須調用`ReleaseDC` [GetDC](#getdc)的每個調用。

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage::發佈GDIPlus

釋放 GDI+ 使用的資源。

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>備註

必須調用此方法以釋放由全域`CImage`物件分配的資源。 請參考[CImage:CImage](#cimage)。

## <a name="cimagesave"></a><a name="save"></a>CImage::儲存

將映射儲存到磁碟上的指定流或檔。

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
指向包含檔案影像資料的 COM IStream 物件的指標。

*pszFileName*<br/>
指向影像的檔名的指標。

*吉德檔案類型*<br/>
要將映射保存為的檔案類型。 可以是下列其中一項：

- `ImageFormatBMP`未壓縮點陣圖影像。

- `ImageFormatPNG`便攜式網路圖形 (PNG) 壓縮圖像。

- `ImageFormatJPEG`JPEG 壓縮圖像。

- `ImageFormatGIF`GIF 壓縮圖像。

> [!NOTE]
> 關於常數的完整清單,請參閱 Windows SDK 中**的影像檔案格式常量**。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

呼叫此函數以使用指定的名稱和類型保存圖像。 如果未包含*guidFileType*參數,則檔名的檔案副檔名的檔案擴展名將用於確定影像格式。 如果未提供擴展,則圖像將以 BMP 格式保存。

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage:設定顏色表

為 DIB 部分的調色板中一系列條目設置紅色、綠色、藍色 (RGB) 顏色值。

```cpp
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>參數

*i第一顏色*<br/>
要設置的第一個條目的顏色表索引。

*n 顏色*<br/>
要設置的顏色表條目數。

*普爾格顏色*<br/>
指向[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)結構陣列的指標,用於設置顏色表條目。

### <a name="remarks"></a>備註

此方法僅支援 DIB 部分位圖。

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage:設定像素

在位圖中給定位置設置像素的顏色。

```cpp
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
要設置的圖元的水準位置。

*Y*<br/>
要設置的圖元的垂直位置。

*顏色*<br/>
設置像素的顏色。

### <a name="remarks"></a>備註

如果像素座標位於所選剪切區域之外,則此方法將失敗。

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::設定像素索引

將像素顏色設置到調色板中*iIndex*處的顏色。

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
要設置的圖元的水準位置。

*Y*<br/>
要設置的圖元的垂直位置。

*iIndex*<br/>
調色板中顏色的索引。

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage:SetPixelRGB

將*x*和*y*指定位置的圖元設定為紅色、綠色、藍色 (RGB) 圖像中由*r、g*和*b*表示的顏色。 *g*

```cpp
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
要設置的圖元的水準位置。

*Y*<br/>
要設置的圖元的垂直位置。

*r*<br/>
紅色的強度。

*G*<br/>
綠色的強度。

*B*<br/>
藍色的強度。

### <a name="remarks"></a>備註

紅色、綠色和藍色參數分別由介於 0 和 255 之間的數位表示。 如果將所有三個參數設置為零,則組合生成的顏色為黑色。 如果將所有三個參數設置為 255,則組合生成的顏色為白色。

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::設定透明色

將給定索引位置的顏色設置為透明。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>參數

*i 透明色*<br/>
要設置為透明的顏色的索引(在調色板中)。 如果 -1,則不將任何顏色設置為透明。

### <a name="return-value"></a>傳回值

以前設置為透明的顏色的索引。

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>C影像:拉伸Blt

將點陣圖從源裝置上下文複製到此當前設備上下文。

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
目標設備上下文的句柄。

*xDest*<br/>
以邏輯單位表示目標矩形左上角的 x 座標。

*yDest*<br/>
以邏輯單位表示目標矩形左上角的 y 座標。

*nD最大寬度*<br/>
目標矩形的寬度(以邏輯單位為單位)。

*nDestHeight*<br/>
目標矩形的高度(以邏輯單位為單位)。

*德沃羅普*<br/>
要執行的柵格操作。 柵格操作代碼精確定義如何組合源、目標和模式(由當前選擇的畫筆定義)以形成目標。 有關其他柵格操作代碼及其說明的清單,請參閱 Windows SDK 中的[BitBlt。](/windows/win32/api/wingdi/nf-wingdi-bitblt)

*整流*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,標識目標。

*xSrc*<br/>
源矩形左上角的 x 座標(以邏輯單位為單位)。

*伊斯爾克*<br/>
源矩形左上角的 y 座標(以邏輯單位為單位)。

*NSrcWidth*<br/>
源矩形的寬度(以邏輯單位為單位)。

*nSrcHeight*<br/>
源矩形的高度(以邏輯單位為單位)。

*雷克斯爾*<br/>
對結構的`RECT`引用,標識源。

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為 0。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[拉伸 Blt。](/windows/win32/api/wingdi/nf-wingdi-stretchblt)

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>圖片::透明布拉特

將點陣圖從源裝置上下文複製到此當前設備上下文。

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
目標設備上下文的句柄。

*xDest*<br/>
以邏輯單位表示目標矩形左上角的 x 座標。

*yDest*<br/>
以邏輯單位表示目標矩形左上角的 y 座標。

*nD最大寬度*<br/>
目標矩形的寬度(以邏輯單位為單位)。

*nDestHeight*<br/>
目標矩形的高度(以邏輯單位為單位)。

*cr透明*<br/>
要視為透明源位圖中的顏色。 默認情況下,CLR_INVALID,指示應使用當前設置為圖像透明顏色的顏色。

*整流*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,標識目標。

*xSrc*<br/>
源矩形左上角的 x 座標(以邏輯單位為單位)。

*伊斯爾克*<br/>
源矩形左上角的 y 座標(以邏輯單位為單位)。

*NSrcWidth*<br/>
源矩形的寬度(以邏輯單位為單位)。

*nSrcHeight*<br/>
源矩形的高度(以邏輯單位為單位)。

*雷克斯爾*<br/>
對結構的`RECT`引用,標識源。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

`TransparentBlt`支援每圖元 4 位元和 8 位元/ 圖元的源點陣圖。 使用[CImage::AlphaBlend](#alphablend)指定具有透明度的 32 位/圖元位圖。

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

[MMXSwarm 樣品](../../overview/visual-cpp-samples.md)<br/>
[簡單影像範例](../../overview/visual-cpp-samples.md)<br/>
[裝置獨立圖](/windows/win32/gdi/device-independent-bitmaps)<br/>
[建立 DIB 節](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[裝置獨立圖](/windows/win32/gdi/device-independent-bitmaps)<br/>
[建立 DIB 節](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
