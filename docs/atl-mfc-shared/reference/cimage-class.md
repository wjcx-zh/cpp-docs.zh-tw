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
ms.openlocfilehash: 6e7197648fd91b2280d406c19c1019ca23f6a470
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684296"
---
# <a name="cimage-class"></a>CImage 類別

`CImage` 提供增強的點陣圖支援，包括以 JPEG、GIF、BMP 和可移植網狀圖形載入和儲存影像的能力 (PNG) 格式。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
class CImage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CImage：： CImage](#cimage)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CImage：： AlphaBlend](#alphablend)|顯示具有透明或半透明圖元的點陣圖。|
|[CImage：： Attach](#attach)|將 HBITMAP 附加至 `CImage` 物件。 可以與非 DIB 區段點陣圖或 DIB 區段點陣圖一起使用。|
|[CImage：： BitBlt](#bitblt)|從來源裝置內容將點陣圖複製到這個目前的裝置內容。|
|[CImage：： Create](#create)|建立 DIB 區段點陣圖，並將其附加至先前所建立的 `CImage` 物件。|
|[CImage：： CreateEx](#createex)|使用) 的其他參數建立 DIB 區段點陣圖 (，並將其附加至先前所建立的 `CImage` 物件。|
|[CImage：:D estroy](#destroy)|從物件卸離點陣圖 `CImage` ，並終結點陣圖。|
|[CImage：:D etach](#detach)|從物件卸離點陣圖 `CImage` 。|
|[CImage：:D 原始](#draw)|從來源矩形將點陣圖複製到目的地矩形。 `Draw` 視需要伸展或壓縮點陣圖以符合目的矩形的尺寸，並處理 Alpha 混色和透明色彩。|
|[CImage：： GetBits](#getbits)|捕獲點陣圖實際圖元值的指標。|
|[CImage：： GetBPP](#getbpp)|抓取每圖元的位數。|
|[CImage：： GetColorTable](#getcolortable)|從色彩資料表中的專案範圍，抓取紅色、綠色、藍色 (RGB) 色彩值。|
|[CImage：： GetDC](#getdc)|抓取選取目前點陣圖的裝置內容。|
|[CImage：： GetExporterFilterString](#getexporterfilterstring)|尋找可用的影像格式及其描述。|
|[CImage：： GetHeight](#getheight)|抓取目前影像的高度（以圖元為單位）。|
|[CImage：： GetImporterFilterString](#getimporterfilterstring)|尋找可用的影像格式及其描述。|
|[CImage：： GetMaxColorTableEntries](#getmaxcolortableentries)|抓取 color 資料表中專案的最大數目。|
|[CImage：： GetPitch](#getpitch)|抓取目前影像的音調（以位元組為單位）。|
|[CImage：： GetPixel](#getpixel)|抓取 *x* 和 *y*指定的圖元色彩。|
|[CImage：： GetPixelAddress](#getpixeladdress)|抓取指定圖元的位址。|
|[CImage：： GetTransparentColor](#gettransparentcolor)|抓取色彩表中透明色彩的位置。|
|[CImage：： GetWidth](#getwidth)|抓取目前影像的寬度（以圖元為單位）。|
|[CImage：： IsDIBSection](#isdibsection)|判斷附加的點陣圖是否為 DIB 區段。|
|[CImage：： IsIndexed](#isindexed)|指出點陣圖的色彩會對應到索引的調色板。|
|[CImage：： IsNull](#isnull)|指出目前是否已載入來源點陣圖。|
|[CImage：： IsTransparencySupported](#istransparencysupported)|指出應用程式是否支援透明點陣圖。|
|[CImage：： Load](#load)|從指定的檔案載入映射。|
|[CImage：： LoadFromResource](#loadfromresource)|從指定的資源載入映射。|
|[CImage：： MaskBlt](#maskblt)|使用指定的遮罩和點陣運算，結合來源和目的點陣圖的色彩資料。|
|[CImage：:P lgBlt](#plgblt)|執行從來源裝置內容中的矩形到目的地裝置內容中之平行四邊形的位區區塊轉送。|
|[CImage：： ReleaseDC](#releasedc)|釋放使用 [CImage：： GetDC](#getdc)取出的裝置內容。|
|[CImage：： ReleaseGDIPlus](#releasegdiplus)|釋放 GDI + 所使用的資源。 必須呼叫，才能釋放全域物件所建立的資源 `CImage` 。|
|[CImage：： Save](#save)|將影像儲存為指定的類型。 `Save` 無法指定影像選項。|
|[CImage：： SetColorTable](#setcolortable)|在 DIB 區段的色彩資料表中，將紅色、綠色、藍色 RGB) 色彩值。|
|[CImage：： Bitmap.setpixel](#setpixel)|將指定座標的圖元設定為指定的色彩。|
|[CImage：： SetPixelIndexed](#setpixelindexed)|將指定座標的圖元設定為在指定的調色板索引處的色彩。|
|[CImage：： SetPixelRGB](#setpixelrgb)|將指定座標的圖元設定為指定的紅色、綠色、藍色 (RGB) 值。|
|[CImage：： SetTransparentColor](#settransparentcolor)|設定要視為透明的色彩索引。 只有一個調色板中的色彩可以是透明的。|
|[CImage：： StretchBlt](#stretchblt)|如有必要，將點陣圖從來源矩形複製到目的地矩形、延展或壓縮點陣圖，以符合目的地矩形的尺寸。|
|[CImage：： TransparentBlt](#transparentblt)|從來源裝置內容將具有透明色彩的點陣圖複製到這個目前的裝置內容。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CImage：： operator HBITMAP](#operator_hbitmap)|傳回附加至物件的 Windows 控制碼 `CImage` 。|

## <a name="remarks"></a>備註

`CImage` 採用與裝置無關點陣圖 (DIB) 區段的點陣圖;不過，您可以使用 [Create](#create) 或 [CImage：： Load](#load) （僅限 DIB 區段）。 您可以使用 Attach 將非 DIB 區段點陣圖附加至 `CImage` 物件， [Attach](#attach)但是您無法使用下列 `CImage` 僅支援 DIB 區段點陣圖的方法：

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

若要判斷附加的點陣圖是否為 DIB 區段，請呼叫 [IsDibSection](#isdibsection)。

> [!NOTE]
> 在 Visual Studio .NET 2003 中，此類別會保留所建立之物件數目的計數 `CImage` 。 每當計數變成0時， `GdiplusShutdown` 就會自動呼叫函式來釋放 GDI + 所使用的資源。 這樣可確保 `CImage` dll 直接或間接建立的任何物件一律會正確地終結，而 `GdiplusShutdown` 不會從呼叫 `DllMain` 。

> [!NOTE]
> `CImage`不建議在 DLL 中使用全域物件。 如果您需要 `CImage` 在 DLL 中使用全域物件，請呼叫 [CImage：： ReleaseGDIPlus](#releasegdiplus) ，以明確釋放 gdi + 所使用的資源。

`CImage` 無法選取至新的 [CDC](../../mfc/reference/cdc-class.md)。 `CImage` 為影像建立自己的 HDC。 由於 HBITMAP 一次只能選取一個 HDC，因此與相關聯的 HBITMAP `CImage` 無法選取到另一個 hdc 中。 如果您需要 CDC，請從取出的 HDC， `CImage` 然後將它提供給 [cdc：： FromHandle](../../mfc/reference/cdc-class.md#fromhandle)。

## <a name="examples"></a>範例

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

當您 `CImage` 在 MFC 專案中使用時，請注意專案中的哪些成員函式預期 [CBitmap](../../mfc/reference/cbitmap-class.md) 物件的指標。 如果您想要搭配 `CImage` 這類函數使用，例如 [CMenu：： AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)，請使用 [CBitmap：： FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle)，將您的 HBITMAP 傳遞給它， `CImage` 然後使用傳回的 `CBitmap*` 。

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

透過 `CImage` ，您可以存取 DIB 區段的實際位。 您可以使用 `CImage` 任何先前使用 WIN32 HBITMAP 或 DIB 區段的物件。

您可以 `CImage` 從 MFC 或 ATL 使用。

> [!NOTE]
> 當您使用建立專案時 `CImage` ，您必須在 `CString` 包含 *atlimage*之前定義。 如果您的專案使用 ATL 但沒有 MFC，請在包含*atlimage*之前，先包含*和 atlstr.h。* 如果您的專案使用 MFC (或者，如果它是具有 MFC 支援) 的 ATL 專案，請在包含*atlimage*之前，先包含*afxstr。*
>
> 同樣地，您必須先包含 *atlimage* ，然後再包含 *atlimpl .cpp*。 若要輕鬆完成這項工作，請在您的*pch. h* (*stdafx.h*中加入*atlimage* ，Visual Studio 2017 及更早的) 。

## <a name="requirements"></a>需求

**標頭：** atlimage。h

## <a name="cimagealphablend"></a><a name="alphablend"></a> CImage：： AlphaBlend

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
目的地矩形左上角的 x 座標（以邏輯單位表示）。

*yDest*<br/>
目的地矩形左上角的 y 座標（以邏輯單位表示）。

*bSrcAlpha*<br/>
要用於整個來源點陣圖的 Alpha 透明度值。 預設的 0xff (255) 會假設您的映射是不透明的，而且您只想要使用每圖元的 Alpha 值。

*bBlendOp*<br/>
適用于來源和目的地點陣圖的 Alpha 混合函式、要套用至整個來源點陣圖的全域 Alpha 值，以及來源點陣圖的格式資訊。 來源和目的地 blend 函數目前僅限 AC_SRC_OVER。

*pointDest*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構的參考，該結構會識別目的地矩形的左上角（以邏輯單位表示）。

*nDestWidth*<br/>
目的地矩形的寬度（以邏輯單位表示）。

*nDestHeight*<br/>
目的地矩形的高度（以邏輯單位表示）。

*xSrc*<br/>
來源矩形左上角的邏輯 x 座標。

*ySrc*<br/>
來源矩形左上角的邏輯 y 座標。

*nSrcWidth*<br/>
來源矩形的寬度（以邏輯單位表示）。

*nSrcHeight*<br/>
來源矩形的高度（以邏輯單位表示）。

*rectDest*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，識別目的地。

*rectSrc*<br/>
結構的參考 `RECT` ，識別來源。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

Alpha-blend 點陣圖支援以圖元為單位的色彩混合。

當 *bBlendOp* 設定為 AC_SRC_OVER 的預設值時，會根據來源圖元的 Alpha 值，將來源點陣圖放在目的地點陣圖上。

## <a name="cimageattach"></a><a name="attach"></a> CImage：： Attach

將 *hBitmap* 附加至 `CImage` 物件。

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
HBITMAP 的控制碼。

*eOrientation*<br/>
指定點陣圖的方向。 可以是下列其中一項：

- DIBOR_DEFAULT 點陣圖的方向是由作業系統決定。

- DIBOR_BOTTOMUP 點陣圖的這幾行會以相反的順序排列。 這會導致 [CImage：： GetBits](#getbits) 傳回點陣圖緩衝區結尾附近的指標，以及 [CImage：： GetPitch](#getpitch) 傳回負數。

- DIBOR_TOPDOWN 點陣圖的這幾行是由上到下的順序。 這會導致 [CImage：： GetBits](#getbits) 傳回點陣圖緩衝區第一個位元組的指標，以及 [CImage：： GetPitch](#getpitch) 傳回正數。

### <a name="remarks"></a>備註

點陣圖可以是非 DIB 區段點陣圖或 DIB 區段點陣圖。 如需可搭配 DIB 區段點陣圖使用的方法清單，請參閱 [IsDIBSection](#isdibsection) 。

## <a name="cimagebitblt"></a><a name="bitblt"></a> CImage：： BitBlt

從來源裝置內容將點陣圖複製到這個目前的裝置內容。

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
目的地矩形左上角的邏輯 x 座標。

*yDest*<br/>
目的地矩形左上角的邏輯 y 座標。

*dwROP*<br/>
要執行的點陣運算。 點陣作業程式碼會明確定義如何合併來源、目的地和模式 (的位數，如目前選取之筆刷) 所定義，以形成目的地。 請參閱 Windows SDK 中的 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) ，以取得其他點陣操作程式碼的清單及其描述。

*pointDest*<br/>
指出目的地矩形左上角的 [點](/windows/win32/api/windef/ns-windef-point) 結構。

*nDestWidth*<br/>
目的地矩形的寬度（以邏輯單位表示）。

*nDestHeight*<br/>
目的地矩形的高度（以邏輯單位表示）。

*xSrc*<br/>
來源矩形左上角的邏輯 x 座標。

*ySrc*<br/>
來源矩形左上角的邏輯 y 座標。

*rectDest*<br/>
表示目的地矩形的 [RECT](/windows/win32/api/windef/ns-windef-rect) 結構。

*pointSrc*<br/>
`POINT`結構，指出來源矩形的左上角。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 。

## <a name="cimagecimage"></a><a name="cimage"></a> CImage：： CImage

建構 `CImage` 物件。

```
CImage() throw();
```

### <a name="remarks"></a>備註

一旦您已建立物件，請呼叫 [Create](#create)、 [Load](#load)、 [LoadFromResource](#loadfromresource)或 [attach](#attach) ，以將點陣圖附加至物件。

**注意** 在 Visual Studio 中，此類別會保留所建立物件數目的計數 `CImage` 。 每當計數變成0時， `GdiplusShutdown` 就會自動呼叫函式來釋放 GDI + 所使用的資源。 這樣可確保 `CImage` dll 直接或間接建立的任何物件一律會正確地終結，而 `GdiplusShutdown` 不會從 DllMain 呼叫。

`CImage`不建議在 DLL 中使用全域物件。 如果您需要 `CImage` 在 DLL 中使用全域物件，請呼叫 [CImage：： ReleaseGDIPlus](#releasegdiplus) ，以明確釋放 gdi + 所使用的資源。

## <a name="cimagecreate"></a><a name="create"></a> CImage：： Create

建立 `CImage` 點陣圖，並將其附加至先前所建立的 `CImage` 物件。

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*nWidth*<br/>
點陣圖的寬度 `CImage` （以圖元為單位）。

*nHeight*<br/>
點陣圖的高度 `CImage` （以圖元為單位）。 如果 *nHeight* 是正數，則點陣圖是由上而下的 DIB，而其原點是左下角。 如果 *nHeight* 是負數，則點陣圖是由上而下的 DIB，而其原點是左上角。

*nBPP*<br/>
點陣圖中每個圖元的位數。 通常是4、8、16、24或32。 適用于單色點陣圖或遮罩的1可以是1。

*dwFlags*<br/>
指定點陣圖物件是否具有 Alpha 色板。 可以是零或多個下列值的組合：

- *createAlphaChannel* 只有在 *nBPP* 為32，而且 *eCompression* 是 BI_RGB 時，才能使用。 如果指定，則建立的影像會有每個圖元的 Alpha (透明) 值，並儲存在每個圖元的第4個位元組中， (未在非 Alpha 32 位影像) 中使用。 呼叫 [CImage：： AlphaBlend](#alphablend)時，會自動使用此 Alpha 通道。

> [!NOTE]
> 在呼叫 [CImage：:D 原始](#draw)時，具有 Alpha 色板的影像會自動與目的地進行 Alpha 混合。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="cimagecreateex"></a><a name="createex"></a> CImage：： CreateEx

建立 `CImage` 點陣圖，並將其附加至先前所建立的 `CImage` 物件。

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
點陣圖的寬度 `CImage` （以圖元為單位）。

*nHeight*<br/>
點陣圖的高度 `CImage` （以圖元為單位）。 如果 *nHeight* 是正數，則點陣圖是由上而下的 DIB，而其原點是左下角。 如果 *nHeight* 是負數，則點陣圖是由上而下的 DIB，而其原點是左上角。

*nBPP*<br/>
點陣圖中每個圖元的位數。 通常是4、8、16、24或32。 適用于單色點陣圖或遮罩的1可以是1。

*eCompression*<br/>
指定壓縮的下點陣圖壓縮類型 (由上而下的 Dib 無法壓縮) 。 可以是下列值之一：

- BI_RGB 格式未壓縮。 當呼叫時，指定此值 `CImage::CreateEx` 相當於呼叫 `CImage::Create` 。

- BI_BITFIELDS 格式是未壓縮的，且色彩表包含三個 DWORD 色遮罩，分別指定每個圖元的紅色、綠色和藍色元件。 這在搭配使用16和 32-bpp 點陣圖時有效。

*pdwBitfields*<br/>
只有在 *eCompression* 設定為 BI_BITFIELDS 時才使用，否則必須是 Null。 指向三個 DWORD 位元遮罩陣列的指標，指定每個圖元的每個圖元分別用於色彩的紅色、綠色和藍色元件。 如需位欄位限制的詳細資訊，請參閱 Windows SDK 中的 [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) 。

*dwFlags*<br/>
指定點陣圖物件是否具有 Alpha 色板。 可以是零或多個下列值的組合：

- *createAlphaChannel* 只有在 *nBPP* 為32，而且 *eCompression* 是 BI_RGB 時，才能使用。 如果指定，則建立的影像會有每個圖元的 Alpha (透明) 值，並儲存在每個圖元的第4個位元組中， (未在非 Alpha 32 位影像) 中使用。 呼叫 [CImage：： AlphaBlend](#alphablend)時，會自動使用此 Alpha 通道。

   > [!NOTE]
   > 在呼叫 [CImage：:D 原始](#draw)時，具有 Alpha 色板的影像會自動與目的地進行 Alpha 混合。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE。 否則為 FALSE。

### <a name="example"></a>範例

下列範例會建立100x100 圖元點陣圖，並使用16位編碼每個圖元。 在指定的16位圖元中，bits 0-3 會將紅色元件編碼、bits 4-7 編碼為綠色，而 bits 8-11 會將 blue 編碼。 剩餘的4個位未使用。

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a> CImage：:D estroy

從物件卸離點陣圖 `CImage` ，並終結點陣圖。

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a> CImage：:D etach

從物件卸離點陣圖 `CImage` 。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>傳回值

已卸離點陣圖的控制碼，如果未附加點陣圖，則為 Null。

## <a name="cimagedraw"></a><a name="draw"></a> CImage：:D 原始

從來源裝置內容將點陣圖複製到目前的裝置內容。

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
目的地矩形左上角的 x 座標（以邏輯單位表示）。

*yDest*<br/>
目的地矩形左上角的 y 座標（以邏輯單位表示）。

*nDestWidth*<br/>
目的地矩形的寬度（以邏輯單位表示）。

*nDestHeight*<br/>
目的地矩形的高度（以邏輯單位表示）。

*xSrc*<br/>
來源矩形左上角的 x 座標（以邏輯單位表示）。

*ySrc*<br/>
來源矩形左上角的 y 座標（以邏輯單位表示）。

*nSrcWidth*<br/>
來源矩形的寬度（以邏輯單位表示）。

*nSrcHeight*<br/>
來源矩形的高度（以邏輯單位表示）。

*rectDest*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，識別目的地。

*rectSrc*<br/>
結構的參考 `RECT` ，識別來源。

*pointDest*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構的參考，該結構會識別目的地矩形的左上角（以邏輯單位表示）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Draw` 執行與 [StretchBlt](#stretchblt)相同的作業，除非影像包含透明色彩或 Alpha 色板。 在此情況下，會 `Draw` 視需要執行與 [TransparentBlt](#transparentblt) 或 [AlphaBlend](#alphablend) 相同的作業。

如果沒有 `Draw` 指定來源矩形的版本，則會使用整個來源影像作為預設值。 針對 `Draw` 未指定目的地矩形大小的版本，來源影像的大小為預設值，且不會進行延展或壓縮。

## <a name="cimagegetbits"></a><a name="getbits"></a> CImage：： GetBits

抓取點陣圖中特定圖元的實際位值指標。

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>傳回值

點陣圖緩衝區的指標。 如果點陣圖是由上而下的 DIB，指標會指向緩衝區結尾附近的位置。 如果點陣圖是由上而下的 DIB，指標會指向緩衝區的第一個位元組。

### <a name="remarks"></a>備註

使用這個指標以及 [GetPitch](#getpitch)傳回的值，您可以在影像中找出並變更個別的圖元。

> [!NOTE]
> 這個方法僅支援 DIB 區段點陣圖;因此，存取物件的圖元 `CImage` 的方式，與 DIB 區段的圖元相同。 傳回的指標指向位置 (0，0) 的圖元。

## <a name="cimagegetbpp"></a><a name="getbpp"></a> CImage：： GetBPP

抓取每圖元位值。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>傳回值

每圖元的位數。

### <a name="remarks"></a>備註

這個值會決定定義每個圖元的位數，以及點陣圖中的最大色彩數目。

每圖元的位數通常是1、4、8、16、24或32。 如需 `biBitCount` 此值的詳細資訊，請參閱 Windows SDK 中的 [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) 成員。

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a> CImage：： GetColorTable

從 DIB 區段之選擇區中的專案範圍，抓取紅色、綠色、藍色 (RGB) 色彩值。

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>參數

*iFirstColor*<br/>
要取出的第一個專案的色彩表索引。

*nColors*<br/>
要取出的色彩資料表專案數目。

*prgbColors*<br/>
[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)結構陣列的指標，可取得色彩資料表專案。

## <a name="cimagegetdc"></a><a name="getdc"></a> CImage：： GetDC

抓取目前已選取影像的裝置內容。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>傳回值

裝置內容的控制代碼。

### <a name="remarks"></a>備註

對於的每個呼叫 `GetDC` ，您都必須要有後續的 [ReleaseDC](#releasedc)呼叫。

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a> CImage：： GetExporterFilterString

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
`CSimpleString` 物件的參考。 如需詳細資訊，請參閱 **備註** 。

*aguidFileTypes*<br/>
Guid 陣列，其中每個專案都對應至字串中的其中一個檔案類型。 在下面 *pszAllFilesDescription* 的範例中， *aguidFileTypes*[0] 是 GUID_Null，其餘的陣列值是目前作業系統所支援的影像檔案格式。

> [!NOTE]
> 如需常數的完整清單，請參閱 Windows SDK 中的 **圖像檔案格式常數** 。

*pszAllFilesDescription*<br/>
如果這個參數不是 Null，則篩選字串在清單的開頭會有一個額外的篩選。 此篩選準則會有 *pszAllFilesDescription* 的目前值做為描述，並接受清單中任何其他匯出工具所支援之任何副檔名的檔案。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
一組位旗標，指定要從清單中排除的檔案類型。 允許的旗標為：

- `excludeGIF` = 0x01 排除 GIF 檔案。

- `excludeBMP` = 0x02 排除 BMP (Windows 點陣圖) 檔。

- `excludeEMF` = 0x04 會排除 (增強的中繼檔) 檔案的 EMF。

- `excludeWMF` = 0x08 排除 WMF (Windows 中繼檔) 檔。

- `excludeJPEG` = 0x10 排除 JPEG 檔案。

- `excludePNG` = 0x20 排除 PNG 檔案。

- `excludeTIFF` = 0x40 排除 TIFF 檔案。

- `excludeIcon` = 0x80 排除 (Windows 圖示) 檔案的 .ICO。

- `excludeOther` = 0x80000000 排除上面未列出的任何其他檔案類型。

- `excludeDefaultLoad` = 0 代表載入，預設會包含所有檔案類型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 為了節省，預設會排除這些檔案，因為它們通常具有特殊需求。

*chSeparator*<br/>
影像格式之間使用的分隔符號。 如需詳細資訊，請參閱 **備註** 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞至 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) 物件，以在 [檔案另存新檔] 對話方塊中公開可用影像格式的副檔名。

參數 *strExporter* 的格式如下：

file description0&#124;\* . ext0&#124;filedescription1&#124;\* . ext1&#124; .。。檔案描述 *n*&#124;\* 。 ext *n*&#124;&#124;

其中 ' &#124; ' 是所指定的分隔字元 `chSeparator` 。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果您將此字串傳遞至 MFC 物件，請使用預設分隔符號 ' &#124; ' `CFileDialog` 。 如果您將此字串傳遞至一般檔案儲存對話方塊，請使用 null 分隔符號 ' \ 0 '。

## <a name="cimagegetheight"></a><a name="getheight"></a> CImage：： GetHeight

抓取影像的高度（以圖元為單位）。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>傳回值

影像的高度（以圖元為單位）。

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a> CImage：： GetImporterFilterString

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
`CSimpleString` 物件的參考。 如需詳細資訊，請參閱 **備註** 。

*aguidFileTypes*<br/>
Guid 陣列，其中每個專案都對應至字串中的其中一個檔案類型。 在下面 *pszAllFilesDescription* 的範例中， *aguidFileTypes*[0] 是 GUID_Null，其餘的陣列值是目前作業系統所支援的影像檔案格式。

> [!NOTE]
> 如需常數的完整清單，請參閱 Windows SDK 中的 **圖像檔案格式常數** 。

*pszAllFilesDescription*<br/>
如果這個參數不是 Null，則篩選字串在清單的開頭會有一個額外的篩選。 此篩選準則會有 *pszAllFilesDescription* 的目前值做為描述，並接受清單中任何其他匯出工具所支援之任何副檔名的檔案。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
一組位旗標，指定要從清單中排除的檔案類型。 允許的旗標為：

- `excludeGIF` = 0x01 排除 GIF 檔案。

- `excludeBMP` = 0x02 排除 BMP (Windows 點陣圖) 檔。

- `excludeEMF` = 0x04 會排除 (增強的中繼檔) 檔案的 EMF。

- `excludeWMF` = 0x08 排除 WMF (Windows 中繼檔) 檔。

- `excludeJPEG` = 0x10 排除 JPEG 檔案。

- `excludePNG` = 0x20 排除 PNG 檔案。

- `excludeTIFF` = 0x40 排除 TIFF 檔案。

- `excludeIcon` = 0x80 排除 (Windows 圖示) 檔案的 .ICO。

- `excludeOther` = 0x80000000 排除上面未列出的任何其他檔案類型。

- `excludeDefaultLoad` = 0 代表載入，預設會包含所有檔案類型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 為了節省，預設會排除這些檔案，因為它們通常具有特殊需求。

*chSeparator*<br/>
影像格式之間使用的分隔符號。 如需詳細資訊，請參閱 **備註** 。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞至 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) 物件，以在 [ **開啟** 檔案] 對話方塊中公開可用影像格式的副檔名。

參數 *strImporter* 的格式如下：

file description0&#124;\* . ext0&#124;filedescription1&#124;\* . ext1&#124; .。。檔案描述 *n*&#124;\* 。 ext *n*&#124;&#124;

其中 ' &#124; ' 是 *chSeparator*所指定的分隔字元。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果您將此字串傳遞至 MFC 物件，請使用預設分隔符號 ' &#124; ' `CFileDialog` 。 如果您將此字串傳遞給一般的 [ **開啟** 檔案] 對話方塊，請使用 null 分隔符號 ' \ 0 '。

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a> CImage：： GetMaxColorTableEntries

抓取 color 資料表中專案的最大數目。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>傳回值

色彩資料表中的專案數。

### <a name="remarks"></a>備註

這個方法僅支援 DIB 區段點陣圖。

## <a name="cimagegetpitch"></a><a name="getpitch"></a> CImage：： GetPitch

抓取影像的音調。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>傳回值

影像的音調。 如果傳回值為負數，則點陣圖是由上而下的 DIB，而其原點是左下角。 如果傳回值是正數，則點陣圖是由上而下的 DIB，而其原點是左上角。

### <a name="remarks"></a>備註

「音調」是兩個記憶體位址之間的距離（以位元組為單位），代表一個點陣圖線的開頭和下一個點陣圖行的開頭。 由於音調以位元組為單位，因此影像的音調可協助您判斷像素格式。 此音調也可以包含額外的記憶體，以保留給點陣圖。

使用 `GetPitch` With [GetBits](#getbits) 來尋找影像的個別圖元。

> [!NOTE]
> 這個方法僅支援 DIB 區段點陣圖。

## <a name="cimagegetpixel"></a><a name="getpixel"></a> CImage：： GetPixel

抓取 *x* 和 *y*所指定位置的圖元色彩。

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>參數

*x*<br/>
圖元的 x 座標。

*y*<br/>
圖元的 y 座標。

### <a name="return-value"></a>傳回值

圖元的紅色、綠色、藍色 (RGB) 值。 如果圖元超出目前的裁剪區域，則傳回值為 CLR_INVALID。

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a> CImage：： GetPixelAddress

抓取圖元的確切位址。

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
圖元的 x 座標。

*y*<br/>
圖元的 y 座標。

### <a name="remarks"></a>備註

位址是根據圖元的座標、點陣圖的音調，以及每圖元的位數來決定。

對於每圖元少於8個位的格式，這個方法會傳回包含圖元的位元組位址。 例如，如果您的影像格式有每圖元4個位，則 `GetPixelAddress` 會傳回位元組中第一個圖元的位址，且您必須計算每個位元組2個圖元。

> [!NOTE]
> 這個方法僅支援 DIB 區段點陣圖。

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a> CImage：： GetTransparentColor

抓取色調色板中透明色彩的索引位置。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>傳回值

透明色彩的索引。

## <a name="cimagegetwidth"></a><a name="getwidth"></a> CImage：： GetWidth

抓取影像的寬度（以圖元為單位）。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>傳回值

點陣圖的寬度（以圖元為單位）。

## <a name="cimageisdibsection"></a><a name="isdibsection"></a> CImage：： IsDIBSection

判斷附加的點陣圖是否為 DIB 區段。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>傳回值

如果附加的點陣圖為 DIB 區段，則為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

如果點陣圖不是 DIB 區段，您就無法使用下列 `CImage` 僅支援 dib 區段點陣圖的方法：

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a> CImage：： IsIndexed

判斷點陣圖的圖元是否對應到色調色板。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>傳回值

如果已編制索引，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

只有當點陣圖為8位 (256 色彩) 或更少時，此方法才會傳回 TRUE。

> [!NOTE]
> 這個方法僅支援 DIB 區段點陣圖。

## <a name="cimageisnull"></a><a name="isnull"></a> CImage：： IsNull

判斷是否目前已載入點陣圖。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>備註

如果目前未載入點陣圖，這個方法會傳回 TRUE;否則為 FALSE。

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a> CImage：： IsTransparencySupported

指出應用程式是否支援透明點陣圖。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>傳回值

如果目前的平臺支援透明度，則為非零。 否則為 0。

### <a name="remarks"></a>備註

如果傳回值為非零值，而且支援透明度，則呼叫 [AlphaBlend](#alphablend)、 [TransparentBlt](#transparentblt)或 [Draw](#draw) 將會處理透明色彩。

## <a name="cimageload"></a><a name="load"></a> CImage：： Load

載入影像。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pszFileName*<br/>
字串的指標，其中包含要載入之影像檔案的名稱。

*pStream*<br/>
資料流程的指標，其中包含要載入之影像檔案的名稱。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

載入 *>pszfilename* 或 *pStream*所指定的影像。

有效的影像類型為 BMP、GIF、JPEG、PNG 和 TIFF。

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a> CImage：： LoadFromResource

從點陣圖資源載入影像。

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
模組實例的控制碼，其中包含要載入的影像。

*pszResourceName*<br/>
字串的指標，其中包含包含要載入之影像的資源名稱。

*nIDResource*<br/>
要載入的資源 ID。

### <a name="remarks"></a>備註

資源必須是點陣圖類型。

## <a name="cimagemaskblt"></a><a name="maskblt"></a> CImage：： MaskBlt

使用指定的遮罩和點陣運算，結合來源和目的點陣圖的色彩資料。

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
模組的控制碼，其可執行檔包含資源。

*xDest*<br/>
目的地矩形左上角的 x 座標（以邏輯單位表示）。

*yDest*<br/>
目的地矩形左上角的 y 座標（以邏輯單位表示）。

*nDestWidth*<br/>
目的地矩形和來源點陣圖的寬度（以邏輯單位表示）。

*nDestHeight*<br/>
目的地矩形和來源點陣圖的高度（以邏輯單位表示）。

*xSrc*<br/>
來源點陣圖左上角的邏輯 x 座標。

*ySrc*<br/>
來源點陣圖左上角的邏輯 y 座標。

*hbmMask*<br/>
與來源裝置內容中的色彩點陣圖結合的單色遮罩點陣圖控制碼。

*xMask*<br/>
*HbmMask*參數所指定遮罩點陣圖的水準圖元位移。

*yMask*<br/>
*HbmMask*參數所指定的遮罩點陣圖垂直圖元位移。

*dwROP*<br/>
指定方法用來控制來源和目的地資料組合的前景和背景三元點陣作業代碼。 背景點陣操作程式碼會儲存在此值的高序位字組的高序位位元組中;前景點陣操作程式碼會儲存在此值的高序位字組的低序位位元組中;此值的低序位文字會被忽略，且應為零。 如需此方法內容中前景和背景的討論，請參閱 `MaskBlt` Windows SDK 中的。 如需常見的點陣操作程式代碼清單，請參閱 `BitBlt` Windows SDK 中的。

*rectDest*<br/>
結構的參考 `RECT` ，識別目的地。

*pointSrc*<br/>
`POINT`結構，指出來源矩形的左上角。

*pointMask*<br/>
`POINT`結構，表示遮罩點陣圖的左上角。

*pointDest*<br/>
`POINT`結構的參考，此結構會識別目的地矩形的左上角（以邏輯單位表示）。

### <a name="return-value"></a>傳回值

如果成功，則為非零，否則為0。

### <a name="remarks"></a>備註

此方法僅適用于 Windows NT 4.0 版和更新版本。

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a> CImage：： operator HBITMAP

使用這個運算子來取得附加的物件 Windows GDI 控制碼 `CImage` 。 這個運算子是轉換運算子，可支援直接使用 HBITMAP 物件。

## <a name="cimageplgblt"></a><a name="plgblt"></a> CImage：:P lgBlt

執行從來源裝置內容中的矩形到目的地裝置內容中之平行四邊形的位區區塊轉送。

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
邏輯空間中三個點的陣列指標，可識別目的地平行四邊形的三個角落。 來源矩形的左上角會對應到這個陣列中的第一個點、右上角至這個陣列中的第二個點，以及左下角至第三個點。 來源矩形的右下角會對應至平行四邊形中的隱含第四個點。

*hbmMask*<br/>
選用的單色點陣圖的控制碼，可用來遮罩來源矩形的色彩。

*xSrc*<br/>
來源矩形左上角的 x 座標（以邏輯單位表示）。

*ySrc*<br/>
來源矩形左上角的 y 座標（以邏輯單位表示）。

*nSrcWidth*<br/>
來源矩形的寬度（以邏輯單位表示）。

*nSrcHeight*<br/>
來源矩形的高度（以邏輯單位表示）。

*xMask*<br/>
單色點陣圖左上角的 x 座標。

*yMask*<br/>
單色點陣圖左上角的 y 座標。

*rectSrc*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，指定來源矩形的座標。

*pointMask*<br/>
指出遮罩點陣圖左上角的 [點](/windows/win32/api/windef/ns-windef-point) 結構。

### <a name="return-value"></a>傳回值

如果成功，則為非零，否則為0。

### <a name="remarks"></a>備註

如果 *hbmMask* 識別有效的單色點陣圖，則會 `PlgBit` 使用這個點陣圖來遮罩來源矩形的色彩資料位。

此方法僅適用于 Windows NT 4.0 版和更新版本。 如需詳細資訊，請參閱 Windows SDK 中的 [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) 。

## <a name="cimagereleasedc"></a><a name="releasedc"></a> CImage：： ReleaseDC

釋放裝置內容。

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>備註

由於一次只能選取一個點陣圖到裝置內容中，因此您必須呼叫 `ReleaseDC` [GetDC](#getdc)的每個呼叫。

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a> CImage：： ReleaseGDIPlus

釋放 GDI + 所使用的資源。

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>備註

您必須呼叫這個方法，才能釋放全域物件所配置的資源 `CImage` 。 請參閱 [CImage：： CImage](#cimage)。

## <a name="cimagesave"></a><a name="save"></a> CImage：： Save

將影像儲存至磁片上指定的資料流程或檔案。

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
COM IStream 物件的指標，其中包含檔案映射資料。

*pszFileName*<br/>
影像檔案名的指標。

*guidFileType*<br/>
要儲存映射的檔案類型。 可以是下列其中一項：

- `ImageFormatBMP` 未壓縮的點陣圖影像。

- `ImageFormatPNG` 便攜網狀圖形 (PNG) 壓縮的影像。

- `ImageFormatJPEG` JPEG 壓縮的影像。

- `ImageFormatGIF` GIF 壓縮的影像。

> [!NOTE]
> 如需常數的完整清單，請參閱 Windows SDK 中的 **圖像檔案格式常數** 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

呼叫此函式，以使用指定的名稱和類型來儲存影像。 如果未包含 *guidFileType* 參數，則會使用檔案名的副檔名來決定影像格式。 如果未提供任何副檔名，則會以 BMP 格式儲存映射。

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a> CImage：： SetColorTable

在 [DIB] 區段的 [選擇區] 中，為某個專案範圍設定紅色、綠色、藍色 (RGB) 色彩值。

```cpp
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
[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)結構陣列的指標，用來設定色彩資料表專案。

### <a name="remarks"></a>備註

這個方法僅支援 DIB 區段點陣圖。

## <a name="cimagesetpixel"></a><a name="setpixel"></a> CImage：： Bitmap.setpixel

設定點陣圖中指定位置的圖元色彩。

```cpp
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

如果圖元座標落在選取的裁剪區域外，這個方法就會失敗。

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a> CImage：： SetPixelIndexed

將圖元色彩設定為色彩選擇區中位於 *iIndex* 的色彩。

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>參數

*x*<br/>
要設定之圖元的水準位置。

*y*<br/>
要設定之圖元的垂直位置。

*iIndex*<br/>
色彩調色板中色彩的索引。

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a> CImage：： SetPixelRGB

將 *x* 和 *y* 所指定位置上的圖元，設定為紅色、綠色、藍色 (RGB) 影像中 *r*、 *g*和 *b*所表示的色彩。

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
要設定之圖元的水準位置。

*y*<br/>
要設定之圖元的垂直位置。

*r*<br/>
紅色色彩的濃度。

*g*<br/>
綠色色彩的濃度。

*b*<br/>
藍色色彩的濃度。

### <a name="remarks"></a>備註

紅色、綠色和藍色參數都是以0到255之間的數位表示。 如果您將這三個參數設定為零，則合併產生的色彩會是黑色。 如果您將這三個參數都設為255，則合併產生的色彩會是白色。

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a> CImage：： SetTransparentColor

將指定索引位置的色彩設定為透明。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>參數

*iTransparentColor*<br/>
色彩選擇區中要設定為透明的索引。 如果為-1，則不會將色彩設定為透明。

### <a name="return-value"></a>傳回值

先前設定為透明的色彩索引。

## <a name="cimagestretchblt"></a><a name="stretchblt"></a> CImage：： StretchBlt

從來源裝置內容將點陣圖複製到這個目前的裝置內容。

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
目的地矩形左上角的 x 座標（以邏輯單位表示）。

*yDest*<br/>
目的地矩形左上角的 y 座標（以邏輯單位表示）。

*nDestWidth*<br/>
目的地矩形的寬度（以邏輯單位表示）。

*nDestHeight*<br/>
目的地矩形的高度（以邏輯單位表示）。

*dwROP*<br/>
要執行的點陣運算。 點陣作業程式碼會明確定義如何合併來源、目的地和模式 (的位數，如目前選取之筆刷) 所定義，以形成目的地。 請參閱 Windows SDK 中的 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) ，以取得其他點陣操作程式碼的清單及其描述。

*rectDest*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，識別目的地。

*xSrc*<br/>
來源矩形左上角的 x 座標（以邏輯單位表示）。

*ySrc*<br/>
來源矩形左上角的 y 座標（以邏輯單位表示）。

*nSrcWidth*<br/>
來源矩形的寬度（以邏輯單位表示）。

*nSrcHeight*<br/>
來源矩形的高度（以邏輯單位表示）。

*rectSrc*<br/>
結構的參考 `RECT` ，識別來源。

### <a name="return-value"></a>傳回值

如果成功，則為非零，否則為0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的 [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) 。

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a> CImage：： TransparentBlt

從來源裝置內容將點陣圖複製到這個目前的裝置內容。

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
目的地矩形左上角的 x 座標（以邏輯單位表示）。

*yDest*<br/>
目的地矩形左上角的 y 座標（以邏輯單位表示）。

*nDestWidth*<br/>
目的地矩形的寬度（以邏輯單位表示）。

*nDestHeight*<br/>
目的地矩形的高度（以邏輯單位表示）。

*crTransparent*<br/>
來源點陣圖中要視為透明的色彩。 根據預設，CLR_INVALID，表示應該使用目前設定為影像透明色彩的色彩。

*rectDest*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，識別目的地。

*xSrc*<br/>
來源矩形左上角的 x 座標（以邏輯單位表示）。

*ySrc*<br/>
來源矩形左上角的 y 座標（以邏輯單位表示）。

*nSrcWidth*<br/>
來源矩形的寬度（以邏輯單位表示）。

*nSrcHeight*<br/>
來源矩形的高度（以邏輯單位表示）。

*rectSrc*<br/>
結構的參考 `RECT` ，識別來源。

### <a name="return-value"></a>傳回值

如果成功則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

`TransparentBlt` 支援每圖元4位的來源點陣圖和每圖元8位。 使用 [CImage：： AlphaBlend](#alphablend) 指定具有透明度的每圖元32位點陣圖。

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
