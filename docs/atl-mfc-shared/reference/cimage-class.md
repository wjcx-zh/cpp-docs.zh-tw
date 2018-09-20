---
title: CImage 類別 |Microsoft Docs
ms.custom: ''
ms.date: 02/01/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd0858763d31e1f46e1cb366154871f06ae7a910
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400402"
---
# <a name="cimage-class"></a>CImage 類別

`CImage` 提供增強的點陣圖支援，包括載入和儲存 JPEG、 GIF、 BMP、 和可攜式網路圖形 (PNG) 格式的映像的能力。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CImage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CImage::CImage](#cimage)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Cimage:: Alphablend](#alphablend)|顯示具有透明或半透明的像素的點陣圖。|
|[CImage::Attach](#attach)|附加至 HBITMAP`CImage`物件。 可以搭配非 DIB 區段點陣圖或 DIB 區段點陣圖。|
|[CImage::BitBlt](#bitblt)|來源裝置內容的點陣圖複製到這個目前的裝置內容。|
|[CImage::Create](#create)|建立 DIB 區段點陣圖，並將它附加至先前建構`CImage`物件。|
|[CImage::CreateEx](#createex)|建立 DIB 區段點陣圖 （與其他參數），並將它附加至先前建構`CImage`物件。|
|[CImage::Destroy](#destroy)|卸離點陣圖`CImage`物件，並終結點陣圖。|
|[CImage::Detach](#detach)|卸離點陣圖`CImage`物件。|
|[Cimage](#draw)|來源矩形的點陣圖複製到目的地矩形。 `Draw` 會自動縮放或壓縮點陣圖以符合目的地矩形的維度，如有必要，並處理 alpha 透明混色和透明的色彩。|
|[CImage::GetBits](#getbits)|擷取點陣圖的實際像素值的指標。|
|[CImage::GetBPP](#getbpp)|擷取每個像素的位元。|
|[CImage::GetColorTable](#getcolortable)|從範圍的色彩表中的項目擷取紅、 綠、 藍 (RGB) 色彩值。|
|[CImage::GetDC](#getdc)|擷取到其中的目前點陣圖已選取的裝置內容。|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|尋找可用映像格式和其描述。|
|[CImage::GetHeight](#getheight)|擷取目前的映像，單位為像素的高度。|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|尋找可用映像格式和其描述。|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|擷取色彩表中的項目的數目上限。|
|[CImage::GetPitch](#getpitch)|擷取目前的映像，以位元組為單位的字幅。|
|[CImage::GetPixel](#getpixel)|擷取所指定的像素的色彩*x*並*y*。|
|[CImage::GetPixelAddress](#getpixeladdress)|擷取指定的像素的位址。|
|[CImage::GetTransparentColor](#gettransparentcolor)|擷取的透明色彩的色彩表中的位置。|
|[CImage::GetWidth](#getwidth)|擷取目前的影像像素為單位的寬度。|
|[CImage::IsDIBSection](#isdibsection)|判斷附加的點陣圖為之 DIB 區段。|
|[CImage::IsIndexed](#isindexed)|表示點陣圖的色彩會對應到索引的調色盤。|
|[CImage::IsNull](#isnull)|表示是否目前已載入的來源點陣圖。|
|[CImage::IsTransparencySupported](#istransparencysupported)|指出應用程式是否支援透明的點陣圖。|
|[CImage::Load](#load)|從指定的檔案載入影像。|
|[CImage::LoadFromResource](#loadfromresource)|從指定的資源載入映像。|
|[CImage::MaskBlt](#maskblt)|結合使用指定的遮罩和點陣作業的來源和目的地點陣圖的色彩資料。|
|[CImage::PlgBlt](#plgblt)|執行從來源裝置內容中的矩形的位元區塊傳輸到目的地裝置內容中的平行四邊形。|
|[CImage::ReleaseDC](#releasedc)|釋放與已擷取的裝置內容[CImage::GetDC](#getdc)。|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|釋放 GDI + 所使用的資源。 必須由全域可用的資源呼叫`CImage`物件。|
|[CImage::Save](#save)|將影像儲存為指定的類型。 `Save` 無法指定映像的選項。|
|[CImage::SetColorTable](#setcolortable)|將紅色、 綠色、 藍色 RGB） 色彩的色彩表之 DIB 區段中的項目範圍中的值。|
|[CImage::SetPixel](#setpixel)|在指定的座標，以指定的色彩設定像素。|
|[CImage::SetPixelIndexed](#setpixelindexed)|色彩調色盤的指定索引處的指定座標上設定之像素。|
|[CImage::SetPixelRGB](#setpixelrgb)|在指定的座標指定的紅、 綠、 藍 (RGB) 值會設定像素。|
|[CImage::SetTransparentColor](#settransparentcolor)|會設定為透明處理色彩的索引。 只有一種色彩調色盤中的可以是透明的。|
|[CImage::StretchBlt](#stretchblt)|來源矩形的點陣圖複製到目的地矩形，延伸或壓縮點陣圖以符合目的地矩形的維度，如有必要。|
|[CImage::TransparentBlt](#transparentblt)|來源裝置內容以透明色彩的點陣圖複製到這個目前的裝置內容。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|傳回附加至的 Windows 控制代碼`CImage`物件。|

## <a name="remarks"></a>備註

`CImage` 會為其中一個裝置獨立點陣圖 (DIB) 區段，或不; 的點陣圖不過，您可以使用[Create](#create)或是[CImage::Load](#load)只 DIB 區段。 您可以將附加至非 DIB 區段點陣圖`CImage`物件使用[附加](#attach)，但您便無法使用下列`CImage`方法，其支援 DIB 區段點陣圖：

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

若要判斷是否將附加的點陣圖之 DIB 區段，請呼叫[IsDibSection](#isdibsection)。

> [!NOTE]
> **附註**在 Visual Studio.NET 2003 中，這個類別會保留的數目計數`CImage`所建立的物件。 每當計數變成 0，此函式`GdiplusShutdown`釋放 GDI + 所使用的資源時，會自動呼叫。 這可確保任何`CImage`一律會正確地終結物件直接或間接由 Dll 和可`GdiplusShutdown`不會從呼叫`DllMain`。

> [!NOTE]
>  使用全域`CImage`不建議在 DLL 中的物件。 如果您需要使用全域`CImage`物件在 DLL 中，呼叫[CImage::ReleaseGDIPlus](#releasegdiplus)明確釋放 GDI + 所使用的資源。

`CImage` 無法選取至新[CDC](../../mfc/reference/cdc-class.md)。 `CImage` 建立自己的 HDC 映像。 HBITMAP HBITMAP 一次只能選取一個 HDC 到，因為相關聯`CImage`到另一個 HDC 無法選取。 如果您需要在 CDC 時，擷取從 HDC `CImage` ，並提供給 [CDC::FromHandle] (../../mfc/reference/cdc-class.md#cdc__fromhandle。

## <a name="example"></a>範例

```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

當您使用`CImage`在 MFC 專案中，請注意在您的專案中的成員函式預期的指標[CBitmap](../../mfc/reference/cbitmap-class.md)物件。 如果您想要使用`CImage`這類函式，例如[CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)，使用[CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle)，將它傳遞您`CImage`HBITMAP，並使用傳回`CBitmap*`。  


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


透過`CImage`，您可以存取之 DIB 區段的實際位元。 您可以使用`CImage`您先前使用的 Win32 HBITMAP 或 DIB 區段的任何位置物件。

您可以使用`CImage`從 MFC 或 atl。

> [!NOTE]
>  當您建立專案，使用`CImage`，您必須定義`CString`您加入之前`atlimage.h`。 如果您的專案使用 ATL 不以 MFC，包括`atlstr.h`您加入之前`atlimage.h`。 如果您的專案使用 MFC （或如果它是 MFC 支援的 ATL 專案），包括`afxstr.h`您加入之前`atlimage.h`。  
>   
>  同樣地，您必須包含`atlimage.h`您加入之前`atlimpl.cpp`。 若要完成這項作業輕鬆，包括`atlimage.h`在您`stdafx.h`。

## <a name="requirements"></a>需求

**標頭：** atlimage.h

##  <a name="alphablend"></a>  Cimage:: Alphablend

顯示具有透明或半透明的像素的點陣圖。

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

*hDestDC*  
目的地裝置內容的控制代碼。

*xDest*  
X 軸座標，以邏輯單位，目的地矩形左上角。

*yDest*  
Y 軸座標，以邏輯單位，目的地矩形左上角。

*bSrcAlpha*  
用於整個來源點陣圖的 alpha 透明度值。 預設值 0xff (255) 假設您的映像，是不透明，和您想要使用僅限每一像素 alpha 值。

*bBlendOp*  
Alpha 透明混色函式的來源和目的地點陣圖、 全域的 alpha 值，要套用至整個來源點陣圖和來源點陣圖的格式資訊。 來源和目的地 blend 函式是目前僅限於 AC_SRC_OVER。

*pointDest*  
參考[點](https://msdn.microsoft.com/library/windows/desktop/dd162805)識別目的地矩形，以邏輯單位表示的左上的角的結構。

*nDestWidth*  
以邏輯單位，目的地矩形的寬度。

*nDestHeight*  
以邏輯單位，目的地矩形的高度。

*xSrc*  
邏輯 x 座標的來源矩形左上角。

*ySrc*  
邏輯 y 座標的來源矩形左上角。

*nSrcWidth*  
以邏輯單位，來源矩形的寬度。

*nSrcHeight*  
以邏輯單位，來源矩形的高度。

*rectDest*  
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。

*rectSrc*  
參考`RECT`結構，來識別來源。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

Alpha 混色點陣圖支援每一像素為基礎的色彩混合。

當*bBlendOp*設定 AC_SRC_OVER 為預設值，將來源點陣圖會透過根據來源像素的 alpha 值的目的地點陣圖。  

##  <a name="attach"></a>  CImage::Attach

附加*hBitmap*到`CImage`物件。

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*hBitmap*  
HBITMAP 控制代碼。

*eOrientation*  
指定點陣圖的方向。 可以是下列其中一項：

- DIBOR_DEFAULT 點陣圖的方向是由作業系統決定。 不過，這可能永遠沒有預期的結果在所有作業系統上。 如需詳細資訊，請參閱下列知識庫文件 (**Q186586**): PRB: getobject （） 一律會傳回正數高度的 DIB 區段。

- DIBOR_BOTTOMUP 點陣圖的線是以反向順序。 這會導致[CImage::GetBits](#getbits)附近點陣圖緩衝區結尾的指標傳回並[CImage::GetPitch](#getpitch)傳回負數。

- DIBOR_TOPDOWN 點陣圖的幾行位於由上而下的順序。 這會導致[CImage::GetBits](#getbits)指標傳回第一個位元組的點陣圖緩衝區並[CImage::GetPitch](#getpitch)来傳回的正數值。

### <a name="remarks"></a>備註

非 DIB 區段點陣圖或 DIB 區段點陣圖，可以是點陣圖。 請參閱[IsDIBSection](#isdibsection)取得一份方法，您可以只使用 DIB 區段點陣圖。

##  <a name="bitblt"></a>  CImage::BitBlt

來源裝置內容的點陣圖複製到這個目前的裝置內容。

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

*hDestDC*  
目的地 HDC。

*xDest*  
邏輯 x 座標的目的矩形左上角。

*yDest*  
邏輯 y 座標的目的矩形左上角。

*dwROP*  
要執行的點陣作業。 點陣作業程式碼會定義如何結合以形成目的地的來源、 目的地和模式的位元 （如目前選取的筆刷所定義）。 請參閱[BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) Windows SDK 中針對其他的點陣作業程式碼及其描述的清單。

*pointDest*  
A[點](https://msdn.microsoft.com/library/windows/desktop/dd162805)指出目的地矩形左上的角的結構。

*nDestWidth*  
以邏輯單位，目的地矩形的寬度。

*nDestHeight*  
以邏輯單位，目的地矩形的高度。

*xSrc*  
邏輯 x 座標的來源矩形左上角。

*ySrc*  
邏輯 y 座標的來源矩形左上角。

*rectDest*  
A [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)指出目的地矩形的結構。

*pointSrc*  
A`POINT`指出來源矩形左上的角的結構。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) Windows SDK 中。

##  <a name="cimage"></a>  CImage::CImage

建構 `CImage` 物件。

```
CImage() throw();
```

### <a name="remarks"></a>備註

一旦您建構了該物件，呼叫[Create](#create)，[負載](#load)， [LoadFromResource](#loadfromresource)，或[附加](#attach)來附加至物件的點陣圖。

**附註**在 Visual Studio 中，這個類別會保留的數目計數`CImage`所建立的物件。 每當計數變成 0，此函式`GdiplusShutdown`釋放 GDI + 所使用的資源時，會自動呼叫。 這可確保任何`CImage`一律會正確地終結物件直接或間接由 Dll，`GdiplusShutdown`不會從 DllMain 呼叫。

使用全域`CImage`不建議在 DLL 中的物件。 如果您需要使用全域`CImage`物件在 DLL 中，呼叫[CImage::ReleaseGDIPlus](#releasegdiplus)明確釋放 GDI + 所使用的資源。

##  <a name="create"></a>  CImage::Create

會建立`CImage`點陣圖，並將它附加至先前建構`CImage`物件。

```
BOOL Create(
int nWidth,
int nHeight,
int nBPP,
DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>參數

*nWidth*  
寬度`CImage`點陣圖、 像素為單位。

*nHeight*  
高度`CImage`點陣圖、 像素為單位。 如果*nHeight*是正數，點陣圖是由下往上 DIB 和其來源是左下的角。 如果*nHeight*是負數，點陣圖是由上而下 DIB 和其來源是左上的角。

*nBPP*  
每個點陣圖中像素的位元數字。 通常是 4、 8、 16、 24、 或 32。 可以是 1，單色點陣圖或遮罩。

*dwFlags*  
指定點陣圖物件是否具有 alpha 色頻。 可以是零或多個下列值的組合：

- *createAlphaChannel*僅適用於如果*nBPP*為 32，和*eCompression*是 BI_RGB。 如果指定，建立的映像會有每個像素，儲存在每個像素 （未使用非英數 32 位元映像中） 的第 4 個位元組的 alpha （投影片） 值。 呼叫時，會自動使用此 alpha 色板[cimage:: Alphablend](#alphablend)。

> [!NOTE]
>  在呼叫[Cimage](#draw)，含 alpha 色板的映像會自動 alpha 混合到目的地。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="createex"></a>  CImage::CreateEx

會建立`CImage`點陣圖，並將它附加至先前建構`CImage`物件。

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

*nWidth*  
寬度`CImage`點陣圖、 像素為單位。

*nHeight*  
高度`CImage`點陣圖、 像素為單位。 如果*nHeight*是正數，點陣圖是由下往上 DIB 和其來源是左下的角。 如果*nHeight*是負數，點陣圖是由上而下 DIB 和其來源是左上的角。

*nBPP*  
每個點陣圖中像素的位元數字。 通常是 4、 8、 16、 24、 或 32。 可以是 1，單色點陣圖或遮罩。

*eCompression*  
指定壓縮由下往上點陣圖 （Dib 由上而下不能壓縮） 的壓縮的類型。 可為下列其中一個值：

- BI_RGB 格式未壓縮。 指定這個值時呼叫`CImage::CreateEx`相當於呼叫`CImage::Create`。

- BI_BITFIELDS 格式未壓縮和 color 資料表包含三個的 DWORD 色彩遮罩，分別指定每個像素的紅色、 綠色和藍色元件。 這是在 16 及 32 bpp 點陣圖搭配使用時才有效。

*pdwBitfields*  
只有在使用*eCompression*設定至 BI_BITFIELDS，否則它必須是 NULL。 三個 DWORD 位元遮罩，指定每個像素的位元會分別使用紅色、 綠色和藍色色彩元件的陣列指標。 如需位元欄位的限制資訊，請參閱[BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) Windows SDK 中。

*dwFlags*  
指定點陣圖物件是否具有 alpha 色頻。 可以是零或多個下列值的組合：

- *createAlphaChannel*僅適用於如果*nBPP*為 32，和*eCompression*是 BI_RGB。 如果指定，建立的映像會有每個像素，儲存在每個像素 （未使用非英數 32 位元映像中） 的第 4 個位元組的 alpha （投影片） 值。 呼叫時，會自動使用此 alpha 色板[cimage:: Alphablend](#alphablend)。

   > [!NOTE]
   > 在呼叫[Cimage](#draw)，含 alpha 色板的映像會自動 alpha 混合到目的地。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE。 否則為 FALSE。

### <a name="example"></a>範例

下列範例會建立 100 x 100 像素點陣圖，使用 16 位元編碼每個像素。 中指定的 16 位元像素位元 0-3 編碼紅色元件、 位元 4-7 編碼綠色及藍色的編碼位元 8-11。 剩餘的 4 個位元皆未使用。  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>  CImage::Destroy

卸離點陣圖`CImage`物件，並終結點陣圖。

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

卸離的點陣圖從`CImage`物件。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>傳回值

卸離後，點陣圖的控制代碼或如果沒有點陣圖會附加 NULL。

##  <a name="draw"></a>  Cimage

來源裝置內容的點陣圖複製到目前的裝置內容。

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

*hDestDC*  
目的地裝置內容控制代碼。

*xDest*  
X 軸座標，以邏輯單位，目的地矩形左上角。

*yDest*  
Y 軸座標，以邏輯單位，目的地矩形左上角。

*nDestWidth*  
以邏輯單位，目的地矩形的寬度。

*nDestHeight*  
以邏輯單位，目的地矩形的高度。

*xSrc*  
X 軸座標，以邏輯單位，來源矩形左上角。

*ySrc*  
Y 軸座標，以邏輯單位，來源矩形左上角。

*nSrcWidth*  
以邏輯單位，來源矩形的寬度。

*nSrcHeight*  
以邏輯單位，來源矩形的高度。

*rectDest*  
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。

*rectSrc*  
參考`RECT`結構，來識別來源。

*pointDest*  
參考[點](https://msdn.microsoft.com/library/windows/desktop/dd162805)識別目的地矩形，以邏輯單位表示的左上的角的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`Draw` 執行相同的作業[StretchBlt](#stretchblt)，除非您的映像包含透明的色彩或 alpha 色頻。 在此情況下，`Draw`執行相同作業，可能是[TransparentBlt](#transparentblt)或是[alphablend，還有旁邊](#alphablend)視需要而定。

版本`Draw`，未指定來源矩形，整個來源影像是預設值。 新版`Draw`不指定目的地矩形的大小、 來源映像的大小是預設值，而且沒有自動縮放或壓縮，就會發生。

##  <a name="getbits"></a>  CImage::GetBits

擷取指定的像素點陣圖中的實際位元值的指標。

```
void* GetBits() throw();
```

### <a name="return-value"></a>傳回值

點陣圖緩衝區的指標。 如果點陣圖是由下往上 DIB，緩衝區的結尾附近，指標指向。 如果點陣圖是由上而下 DIB，指標會指向第一個位元組的緩衝區。

### <a name="remarks"></a>備註

使用這個指標，以及所傳回的值[GetPitch](#getpitch)，您可以找出並變更影像中的個別像素。

> [!NOTE]
>  這個方法支援只有 DIB 區段的點陣圖;因此，您可以存取的像素`CImage`物件相同的方式，就像素 DIB 區段。 傳回的指標會指向的位置 （0，0） 像素。

##  <a name="getbpp"></a>  CImage::GetBPP

擷取每個像素的位元值。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>傳回值

每個像素的位元數。

### <a name="remarks"></a>備註

這個值會決定定義每個像素的位元的數目和最大的點陣圖中的色彩數目。

每個像素的位元通常是 1、 4、 8、 16、 24、 或 32。 請參閱`biBitCount`隸屬[BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) Windows SDK 中針對此值的詳細資訊。

##  <a name="getcolortable"></a>  CImage::GetColorTable

擷取 DIB 區段的調色盤中的項目範圍中的紅、 綠、 藍 (RGB) 色彩值。

```
void GetColorTable(UINT iFirstColor,
UINT nColors,
RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>參數

*iFirstColor*  
要擷取之第一個項目的色彩表索引。

*nColors*  
若要擷取的色彩表項目數目。

*prgbColors*  
陣列的指標[RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)結構，以擷取色彩表項目。

##  <a name="getdc"></a>  CImage::GetDC

擷取目前已選取成它的映像的裝置內容。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>傳回值

裝置內容的控制代碼。

### <a name="remarks"></a>備註

每次呼叫`GetDC`，您必須擁有的後續呼叫[ReleaseDC](#releasedc)。

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

尋找可用的映像格式來儲存映像。

```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
CSimpleArray<GUID>& aguidFileTypes,
LPCTSTR pszAllFilesDescription = NULL,
DWORD dwExclude = excludeDefaultSave,
TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>參數

*strExporters*  
對 `CSimpleString` 物件的參考。 請參閱**備註**如需詳細資訊。

*aguidFileTypes*  
每個項目對應到其中一個字串中的檔案類型的 Guid，陣列。 在範例中，在*pszAllFilesDescription*下方， *aguidFileTypes*[0] 是 GUID_NULL 而其餘的陣列值是目前的作業系統所支援的影像檔案格式。

> [!NOTE]
>  常數的完整清單，請參閱 <<c0>  **映像檔案格式常數**Windows SDK 中。

*pszAllFilesDescription*  
如果這個參數不是 NULL，篩選條件字串就會有一個額外的篩選器清單的開頭。 此篩選器的目前值*pszAllFilesDescription*針對其描述，並接受檔案清單中的任何其他匯出工具所支援的任何延伸模組。

例如:   

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
_T("All Image Files"));
```


*dwExclude*  
指定要從清單中排除哪些檔案類型的位元旗標集。 允許的旗標如下：

- `excludeGIF` = 0x01 排除 GIF 檔案。

- `excludeBMP` = 0x02 排除 BMP （Windows 點陣圖） 檔案。

- `excludeEMF` = 0x04 排除 EMF （增強型中繼檔） 檔案。

- `excludeWMF` = 0x08 排除的 WMF （Windows 中繼檔） 檔案。

- `excludeJPEG` = 0x10 排除 JPEG 檔案。

- `excludePNG` = 0x20 排除 PNG 檔案。

- `excludeTIFF` = 0x40 排除 TIFF 檔案。

- `excludeIcon` = 0x80 排除 ICO （Windows 圖示） 檔案。

- `excludeOther` = 0x80000000 排除以上未列出的任何其他檔案類型。

- `excludeDefaultLoad` = 0 的負載，預設會包含類型的所有檔案

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 儲存，這些檔案會排除預設情況下，因為它們通常會有特殊需求。

*chSeparator*  
使用映像格式之間的分隔符號。 請參閱**備註**如需詳細資訊。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞至您的 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)格式在 [另存新檔] 對話方塊中的物件公開可用的映像的檔案副檔名。

參數*strExporter*格式：

檔案 description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;....file 描述*n*&#124;\*.ext *n*&#124;&#124;

位置 '&#124;' 分隔符號字元由`chSeparator`。 例如: 

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

使用預設的分隔符號 '&#124;' 如果您將此字串傳遞至 MFC`CFileDialog`物件。 如果您將此字串傳遞給通用的儲存檔案對話方塊中，請使用 null 分隔符號 '\0'。

##  <a name="getheight"></a>  CImage::GetHeight

擷取高度，單位為像素的影像。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>傳回值

高度，單位為像素的影像。

##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString

尋找可用的映像格式載入影像。

```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
CSimpleArray<GUID>& aguidFileTypes,
LPCTSTR pszAllFilesDescription = NULL,
DWORD dwExclude = excludeDefaultLoad,
TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>參數

*strImporters*  
對 `CSimpleString` 物件的參考。 請參閱**備註**如需詳細資訊。

*aguidFileTypes*  
每個項目對應到其中一個字串中的檔案類型的 Guid，陣列。 在範例中，在*pszAllFilesDescription*下方， *aguidFileTypes*[0] GUID_NULL 剩餘的陣列值為目前的作業系統所支援的影像檔案格式。

> [!NOTE]
>  常數的完整清單，請參閱 <<c0>  **映像檔案格式常數**Windows SDK 中。

*pszAllFilesDescription*  
如果這個參數不是 NULL，篩選條件字串就會有一個額外的篩選器清單的開頭。 此篩選器的目前值*pszAllFilesDescription*針對其描述，並接受檔案清單中的任何其他匯出工具所支援的任何延伸模組。

例如:   

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
_T("All Image Files"));
```


*dwExclude*  
指定要從清單中排除哪些檔案類型的位元旗標集。 允許的旗標如下：

- `excludeGIF` = 0x01 排除 GIF 檔案。

- `excludeBMP` = 0x02 排除 BMP （Windows 點陣圖） 檔案。

- `excludeEMF` = 0x04 排除 EMF （增強型中繼檔） 檔案。

- `excludeWMF` = 0x08 排除的 WMF （Windows 中繼檔） 檔案。

- `excludeJPEG` = 0x10 排除 JPEG 檔案。

- `excludePNG` = 0x20 排除 PNG 檔案。

- `excludeTIFF` = 0x40 排除 TIFF 檔案。

- `excludeIcon` = 0x80 排除 ICO （Windows 圖示） 檔案。

- `excludeOther` = 0x80000000 排除以上未列出的任何其他檔案類型。

- `excludeDefaultLoad` = 0 的負載，預設會包含類型的所有檔案

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 儲存，這些檔案會排除預設情況下，因為它們通常會有特殊需求。

*chSeparator*  
使用映像格式之間的分隔符號。 請參閱**備註**如需詳細資訊。

### <a name="remarks"></a>備註

您可以將產生的格式字串傳遞至您的 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)格式中的物件公開可用的映像的檔案副檔名**檔案開啟** 對話方塊。

參數*strImporter*格式：

檔案 description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;....file 描述*n*&#124;\*.ext *n*&#124;&#124;

位置 '&#124;' 所指定的分隔符號字元*chSeparator*。 例如: 

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

使用預設的分隔符號 '&#124;' 如果您將此字串傳遞至 MFC`CFileDialog`物件。 使用 null 分隔符號 '\0'，如果您將此字串傳遞給通用**開啟舊檔** 對話方塊。

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

擷取色彩表中的項目的數目上限。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>傳回值

色彩表中的項目數目。

### <a name="remarks"></a>備註

這個方法支援 DIB 區段點陣圖。

##  <a name="getpitch"></a>  CImage::GetPitch

擷取映像的字幅。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>傳回值

映像的字幅。 如果傳回的值為負數，點陣圖是由下往上 DIB 和其來源是左下的角。 如果傳回的值是正數，點陣圖是由上而下 DIB 和其來源是左上的角。

### <a name="remarks"></a>備註

推銷是以位元組為單位，表示點陣圖中的一行開頭的兩個記憶體位址和下一步 的點陣圖一行的開頭之間的距離。 行距以位元組為單位，因為映像的字幅可協助您判斷的像素格式。 越大，音調也可以包含更多的記憶體，保留的點陣圖。

使用`GetPitch`具有[GetBits](#getbits)若要尋找的映像的個別像素。

> [!NOTE]
>  這個方法支援 DIB 區段點陣圖。

##  <a name="getpixel"></a>  CImage::GetPixel

擷取所指定位置的像素的色彩*x*並*y*。

```
COLORREF GetPixel(int x,int y) const throw();
```

### <a name="parameters"></a>參數

*x*  
像素的 x 座標。

*y*  
像素的 y 座標。

### <a name="return-value"></a>傳回值

像素的紅色、 綠色、 藍色 (RGB) 值。 如果像素超出目前裁剪區域，則傳回的值會是 CLR_INVALID。

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

擷取實際的地址，像素。

```
void* GetPixelAddress(int x,int y) throw();
```

### <a name="parameters"></a>參數

*x*  
像素的 x 座標。

*y*  
像素的 y 座標。

### <a name="remarks"></a>備註

位址取決於像素座標、 點陣圖和每個像素的位元的點數。

對於具有少於每個像素 8 位元的格式，這個方法會傳回包含像素的位元組的位址。 例如，如果您的映像格式有每像素 4 個位元`GetPixelAddress`傳回位元組，和您的第一個像素的位址必須計算每個位元組的 2 個像素。

> [!NOTE]
>  這個方法支援 DIB 區段點陣圖。

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

擷取的透明色彩調色盤中的索引的位置。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>傳回值

透明的色彩索引。

##  <a name="getwidth"></a>  CImage::GetWidth

擷取寬度，單位為像素的影像。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>傳回值

點陣圖，單位為像素的寬度。

##  <a name="isdibsection"></a>  CImage::IsDIBSection

判斷附加的點陣圖為之 DIB 區段。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>傳回值

如果附加的點陣圖為 DIB 區段，則為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

如果點陣圖不是之 DIB 區段，您無法使用下列`CImage`方法，其支援 DIB 區段點陣圖：

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>  CImage::IsIndexed

決定是否將點陣圖的像素會對應到調色盤。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>傳回值

如果編製索引，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳回 TRUE，只有當點陣圖是 8 位元 （256 色） 或更少。

> [!NOTE]
>  這個方法支援 DIB 區段點陣圖。

##  <a name="isnull"></a>  CImage::IsNull

決定是否目前已載入點陣圖。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>備註

如果目前未載入點陣圖，這個方法傳回 TRUE否則為 FALSE。

##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported

指出應用程式是否支援透明的點陣圖。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>傳回值

如果目前的平台支援透明度，非零值。 否則為 0。

### <a name="remarks"></a>備註

如果傳回的值為非零值，並支援透明度，則呼叫[alphablend，還有旁邊](#alphablend)， [TransparentBlt](#transparentblt)，或[繪製](#draw)處理透明的色彩。

##  <a name="load"></a>  CImage::Load

載入影像。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pszFileName*  
包含要載入的映像檔案名稱的字串指標。

*pStream*  
包含要載入的映像檔案名稱的資料流指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

載入所指定的影像*pszFileName*或是*pStream*。

有效的映像類型為 BMP、 GIF、 JPEG、 PNG 和 TIFF。

##  <a name="loadfromresource"></a>  CImage::LoadFromResource

從載入映像的點陣圖資源。

```
void LoadFromResource(
HINSTANCE hInstance,
LPCTSTR pszResourceName) throw();

void LoadFromResource(
HINSTANCE hInstance,
UINT nIDResource) throw();
```

### <a name="parameters"></a>參數

*hInstance*  
包含要載入的映像的模組的執行個體的控制代碼。

*pszResourceName*  
包含的資源，包含要載入的影像名稱的字串指標。

*nIDResource*  
若要載入之資源識別碼。

### <a name="remarks"></a>備註

資源必須是類型的點陣圖。

##  <a name="maskblt"></a>  Maskblt

結合使用指定的遮罩和點陣作業的來源和目的地點陣圖的色彩資料。

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

*hDestDC*  
其可執行檔包含資源的模組控制代碼。

*xDest*  
X 軸座標，以邏輯單位，目的地矩形左上角。

*yDest*  
Y 軸座標，以邏輯單位，目的地矩形左上角。

*nDestWidth*  
以邏輯單位，目的地的 rectangle 和來源點陣圖的寬度。

*nDestHeight*  
以邏輯單位，目的地的 rectangle 和來源點陣圖的高度。

*xSrc*  
邏輯 x 座標的來源點陣圖左上角。

*ySrc*  
邏輯 y 座標的來源點陣圖左上角。

*hbmMask*  
結合色彩的點陣圖來源裝置內容中的單色遮罩點陣圖的控制代碼。

*xMask*  
所指定的遮罩點陣圖的像素水平位移*hbmMask*參數。

*yMask*  
所指定的遮罩點陣圖的像素垂直位移*hbmMask*參數。

*dwROP*  
指定前景和背景三元點陣作業程式碼，此方法會使用來控制來源和目的地資料的組合。 背景的點陣作業程式碼會儲存在這個值; 高序位字組的高序位位元組前景點陣作業程式碼會儲存在這個值; 高序位字組的低序位位元組低序位字組，這個值會被忽略，而且必須為零。 如需前景和背景，這個方法的內容中的討論，請參閱`MaskBlt`Windows SDK 中。 如需常見的點陣作業程式碼的清單，請參閱`BitBlt`Windows SDK 中。

*rectDest*  
參考`RECT`結構，用來識別目的地。

*pointSrc*  
A`POINT`指出來源矩形左上的角的結構。

*pointMask*  
A`POINT`表示遮罩點陣圖左上的角的結構。

*pointDest*  
參考`POINT`識別目的地矩形，以邏輯單位表示的左上的角的結構。

### <a name="return-value"></a>傳回值

非零值，如果成功，否則為 0。

### <a name="remarks"></a>備註

這個方法適用於 Windows NT 4.0 和更新版本的版本。

##  <a name="operator_hbitmap"></a>  CImage::operator HBITMAP

使用這個運算子來取得附加的 Windows GDI 控制代碼的`CImage`物件。 這位操作員便轉型運算子，可支援直接使用 HBITMAP 物件。

##  <a name="plgblt"></a>  CImage::PlgBlt

執行從來源裝置內容中的矩形的位元區塊傳輸到目的地裝置內容中的平行四邊形。

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

*hDestDC*  
目的地裝置內容控制代碼。

*pPoints*  
在邏輯空間中識別目的地平行四邊形的三個角落的三個點的陣列指標。 來源矩形左上的角會對應至這個陣列、 在此陣列中，第二個點的右上角和左下的角的第三個點的第一個點。 來源矩形的右下角會對應至隱含的平行四邊形中第四個點。

*hbmMask*  
用來遮罩來源矩形的色彩選擇性單色點陣圖控制代碼。

*xSrc*  
X 軸座標，以邏輯單位，來源矩形左上角。

*ySrc*  
Y 軸座標，以邏輯單位，來源矩形左上角。

*nSrcWidth*  
以邏輯單位，來源矩形的寬度。

*nSrcHeight*  
以邏輯單位，來源矩形的高度。

*xMask*  
單色點陣圖左上角的 x 座標。

*yMask*  
單色點陣圖左上角的 y 座標。

*rectSrc*  
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定來源矩形的座標。

*pointMask*  
A[點](https://msdn.microsoft.com/library/windows/desktop/dd162805)表示遮罩點陣圖左上的角的結構。

### <a name="return-value"></a>傳回值

非零值，如果成功，否則為 0。

### <a name="remarks"></a>備註

如果*hbmMask*識別有效的單色點陣圖，`PlgBit`遮罩從來源矩形的色彩資料位元會使用此點陣圖。

這個方法適用於 Windows NT 4.0 和更新版本的版本。 請參閱[PlgBlt](/windows/desktop/api/wingdi/nf-wingdi-plgblt)在 Windows SDK 中，如需詳細資訊。

##  <a name="releasedc"></a>  CImage::ReleaseDC

釋放裝置內容。

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>備註

因為只有一個點陣圖可以放入裝置內容中選取一次，您必須呼叫`ReleaseDC`每次呼叫[GetDC](#getdc)。

##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus

釋放 GDI + 所使用的資源。

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>備註

必須呼叫這個方法，以便釋出資源配置的全域`CImage`物件。 請參閱[CImage::CImage](#cimage)。

##  <a name="save"></a>  CImage::Save

將影像儲存至指定的資料流或檔案在磁碟上。

```
HRESULT Save(IStream* pStream,
REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
REFGUID guidFileType= GUID_NULL) const throw();
```

### <a name="parameters"></a>參數

*pStream*  
COM IStream 物件，包含檔案的影像資料指標。

*pszFileName*  
映像的檔案名稱指標。

*guidFileType*  
要儲存映像的檔案類型。 可以是下列其中一項：

- `ImageFormatBMP` 未壓縮的點陣圖影像。

- `ImageFormatPNG` 可攜式網路圖形 (PNG) 的壓縮映像。

- `ImageFormatJPEG` JPEG 壓縮映像。

- `ImageFormatGIF` GIF 的壓縮映像。

> [!NOTE]
>  常數的完整清單，請參閱 <<c0>  **映像檔案格式常數**Windows SDK 中。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

呼叫此函式來儲存映像，使用指定的名稱和型別。 如果*guidFileType*未包含參數、 檔名的副檔名將用來判斷映像格式。 如果提供不含副檔名，則將 BMP 格式儲存影像。

##  <a name="setcolortable"></a>  CImage::SetColorTable

設定 DIB 區段的調色盤中的紅、 綠、 藍 (RGB) 色彩值範圍的項目。

```
void SetColorTable(
    UINT iFirstColor, 
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>參數

*iFirstColor*  
若要設定的第一個項目色彩表索引。

*nColors*  
若要設定的色彩表項目數目。

*prgbColors*  
陣列的指標[RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)結構，以設定色彩表項目。

### <a name="remarks"></a>備註

這個方法支援 DIB 區段點陣圖。

##  <a name="setpixel"></a>  CImage::SetPixel

設定在點陣圖中的指定位置的像素的色彩。

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>參數

*x*  
要設定之像素水平位置。

*y*  
要設定之像素垂直位置。

*色彩*  
要設定像素的色彩。

### <a name="remarks"></a>備註

如果像素座標圓周在選取的裁剪區域之外，這個方法將會失敗。

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

將像素色彩設定為位於色彩*iIndex*調色盤的色彩。

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>參數

*x*  
要設定之像素水平位置。

*y*  
要設定之像素垂直位置。

*iIndex*  
色彩調色盤中的索引。

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

設定所指定位置的像素*x*並*y*所指定的色彩*r*， *g*，和*b*、 以紅色、 綠色、 藍色 (RGB) 映像。

```
void SetPixelRGB(  
int x,
int y,
BYTE r,
BYTE g,
BYTE b) throw();
```

### <a name="parameters"></a>參數

*x*  
要設定之像素水平位置。

*y*  
要設定之像素垂直位置。

*r*  
紅色的色彩的濃度。

*g*  
綠色的色彩的濃度。

*b*  
藍色的色彩的濃度。

### <a name="remarks"></a>備註

紅色、 綠色和藍色參數會分別表示 0 和 255 之間的數字。 如果您將所有的三個參數設定為零，則合併的結果色彩為黑色。 如果您將所有的三個參數為 255 時，合併的結果色彩為白色。

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

設定的色彩為透明的指定索引位置。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>參數

*iTransparentColor*  
若要設定為透明色彩的調色盤中的索引。 -1，如果沒有色彩設為透明。

### <a name="return-value"></a>傳回值

先前的色彩索引設定為透明。

##  <a name="stretchblt"></a>  CImage::StretchBlt

來源裝置內容的點陣圖複製到這個目前的裝置內容。

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

*hDestDC*  
目的地裝置內容控制代碼。

*xDest*  
X 軸座標，以邏輯單位，目的地矩形左上角。

*yDest*  
Y 軸座標，以邏輯單位，目的地矩形左上角。

*nDestWidth*  
以邏輯單位，目的地矩形的寬度。

*nDestHeight*  
以邏輯單位，目的地矩形的高度。

*dwROP*  
要執行的點陣作業。 點陣作業程式碼會定義如何結合以形成目的地的來源、 目的地和模式的位元 （如目前選取的筆刷所定義）。 請參閱[BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) Windows SDK 中針對其他的點陣作業程式碼及其描述的清單。

*rectDest*  
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。

*xSrc*  
X 軸座標，以邏輯單位，來源矩形左上角。

*ySrc*  
Y 軸座標，以邏輯單位，來源矩形左上角。

*nSrcWidth*  
以邏輯單位，來源矩形的寬度。

*nSrcHeight*  
以邏輯單位，來源矩形的高度。

*rectSrc*  
參考`RECT`結構，來識別來源。

### <a name="return-value"></a>傳回值

非零值，如果成功，否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [StretchBlt](/windows/desktop/api/wingdi/nf-wingdi-stretchblt) Windows SDK 中。

##  <a name="transparentblt"></a>  Transparentblt

來源裝置內容的點陣圖複製到這個目前的裝置內容。

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

*hDestDC*  
目的地裝置內容控制代碼。

*xDest*  
X 軸座標，以邏輯單位，目的地矩形左上角。

*yDest*  
Y 軸座標，以邏輯單位，目的地矩形左上角。

*nDestWidth*  
以邏輯單位，目的地矩形的寬度。

*nDestHeight*  
以邏輯單位，目的地矩形的高度。

*crTransparent*  
中要視為透明的來源點陣圖的色彩。 依預設，CLR_INVALID，表示應該使用目前設定為影像的透明色彩的色彩。

*rectDest*  
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。

*xSrc*  
X 軸座標，以邏輯單位，來源矩形左上角。

*ySrc*  
Y 軸座標，以邏輯單位，來源矩形左上角。

*nSrcWidth*  
以邏輯單位，來源矩形的寬度。

*nSrcHeight*  
以邏輯單位，來源矩形的高度。

*rectSrc*  
參考`RECT`結構，來識別來源。

### <a name="return-value"></a>傳回值

如果成功，否則為 FALSE，則為 TRUE。

### <a name="remarks"></a>備註

`TransparentBlt` 支援的 4 個位元，每像素，每像素 8 位元的來源點陣圖。 使用[cimage:: Alphablend](#alphablend)透明度指定 32 位元每一像素的點陣圖。


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

[MMXSwarm 範例](../../visual-cpp-samples.md)<br/>
[SimpleImage 範例](../../visual-cpp-samples.md)<br/>
[裝置獨立點陣圖](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)<br/>
[裝置獨立點陣圖](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)   

